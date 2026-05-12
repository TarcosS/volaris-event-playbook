# SDK Guide

> How to read, understand, and audit Azure SDK code during the event.

---

## Purpose

During the code audit (Day 3), participants will encounter Azure SDK usage in the codebases they inspect. This guide helps coaches understand the common SDKs, recognize patterns, and identify risks in how they are used.

This is **not** a development tutorial. It is an **audit reference** — how to spot problems in existing SDK usage.

---

## Common Azure SDKs by Language

### .NET (`Azure.*` packages)

| Package | Purpose |
|---|---|
| `Azure.Identity` | Authentication (DefaultAzureCredential, ManagedIdentity) |
| `Azure.Storage.Blobs` | Blob storage operations |
| `Azure.Security.KeyVault.Secrets` | Key Vault secret management |
| `Azure.Messaging.ServiceBus` | Service Bus messaging |
| `Azure.ResourceManager.*` | ARM resource management |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | Key Vault as config source |

**Where to check:** `.csproj` files, `Directory.Build.props`, or `Directory.Packages.props`

```bash
# List Azure SDK packages in a .NET project
grep -r "Azure\." --include="*.csproj" .
dotnet list package | grep -i azure
```

### JavaScript/TypeScript (`@azure/*` packages)

| Package | Purpose |
|---|---|
| `@azure/identity` | Authentication |
| `@azure/storage-blob` | Blob storage |
| `@azure/keyvault-secrets` | Key Vault |
| `@azure/service-bus` | Service Bus |
| `@azure/arm-*` | Resource management |

**Where to check:** `package.json`

```bash
# List Azure packages
cat package.json | grep "@azure"
npm list | grep azure
```

### Python (`azure-*` packages)

| Package | Purpose |
|---|---|
| `azure-identity` | Authentication |
| `azure-storage-blob` | Blob storage |
| `azure-keyvault-secrets` | Key Vault |
| `azure-servicebus` | Service Bus |
| `azure-mgmt-*` | Resource management |

**Where to check:** `requirements.txt`, `pyproject.toml`, `setup.py`

```bash
# List Azure packages
grep azure requirements.txt
pip list | grep azure
```

---

## Authentication Patterns to Audit

### Good Patterns ✅

```csharp
// .NET — DefaultAzureCredential (recommended)
var credential = new DefaultAzureCredential();
var client = new BlobServiceClient(new Uri(endpoint), credential);
```

```typescript
// TypeScript — DefaultAzureCredential
const credential = new DefaultAzureCredential();
const client = new BlobServiceClient(url, credential);
```

### Bad Patterns ❌ (Audit Findings)

```csharp
// RISK: Hardcoded connection string with embedded credentials
var client = new BlobServiceClient("DefaultEndpointsProtocol=https;AccountName=...;AccountKey=...");
```

```python
# RISK: Hardcoded credentials
client = BlobServiceClient(
    account_url="https://myaccount.blob.core.windows.net",
    credential="hardcoded-key-here"
)
```

```typescript
// RISK: Credentials in environment variable without Key Vault
const key = process.env.STORAGE_KEY;  // Better than hardcoded, but Key Vault is preferred
```

### What to Look For

| Pattern | Risk Level | Finding |
|---|---|---|
| `new DefaultAzureCredential()` | ✅ Good | Recommended authentication pattern |
| `ManagedIdentityCredential()` | ✅ Good | Production-appropriate for Azure-hosted apps |
| Connection string with `AccountKey=` | ❌ High | Credential embedded in connection string |
| Hardcoded key/password in code | ❌ Critical | Direct credential exposure |
| `process.env.SECRET` without Key Vault | ⚠️ Medium | Acceptable for dev, should use Key Vault in prod |
| No credential rotation mechanism | ⚠️ Medium | Long-lived credentials increase blast radius |

---

## Error Handling Patterns to Audit

### Good Patterns ✅

```csharp
try
{
    var response = await client.GetBlobClient(name).DownloadAsync();
}
catch (RequestFailedException ex) when (ex.Status == 404)
{
    _logger.LogWarning("Blob {Name} not found", name);
    return NotFound();
}
catch (RequestFailedException ex)
{
    _logger.LogError(ex, "Azure Storage error for blob {Name}", name);
    throw;
}
```

### Bad Patterns ❌ (Audit Findings)

```csharp
// RISK: Silent error swallowing
try { await client.DownloadAsync(); }
catch { }  // Empty catch — errors are silently ignored
```

```python
# RISK: Generic exception handling
try:
    client.download_blob(name)
except Exception:
    pass  # Silently fails — no logging, no retry, no alert
```

```typescript
// RISK: Logging but not handling
try {
    await client.downloadBlob(name);
} catch (e) {
    console.log(e);  // console.log is not structured logging; error is lost
}
```

### What to Look For

| Pattern | Risk Level | Finding |
|---|---|---|
| Specific exception types caught | ✅ Good | Targeted error handling |
| Structured logging on errors | ✅ Good | Errors are observable |
| Empty catch blocks | ❌ High | Silent failures |
| Generic `catch (Exception)` | ⚠️ Medium | May mask specific errors |
| `console.log` for errors | ⚠️ Medium | Not structured, not searchable |
| No retry logic on transient errors | ⚠️ Medium | Azure services can have transient failures |

---

## Retry and Resilience Patterns

### Azure SDK Built-in Retry

Most Azure SDKs have built-in retry policies. Check if they are configured:

```csharp
// .NET — Custom retry policy
var options = new BlobClientOptions();
options.Retry.MaxRetries = 3;
options.Retry.Delay = TimeSpan.FromSeconds(1);
options.Retry.Mode = RetryMode.Exponential;
```

```python
# Python — Custom retry policy
from azure.storage.blob import BlobServiceClient
from azure.core.pipeline.policies import RetryPolicy

client = BlobServiceClient(url, credential=cred, retry_policy=RetryPolicy(retry_total=3))
```

### What to Look For

| Pattern | Risk Level | Finding |
|---|---|---|
| Default retry policy (SDK default) | ✅ Acceptable | SDK defaults are reasonable |
| Custom retry with exponential backoff | ✅ Good | Intentional resilience design |
| Retry disabled (`MaxRetries = 0`) | ⚠️ Medium | Transient failures will propagate |
| No timeout configuration | ⚠️ Medium | Calls may hang indefinitely |
| Infinite retry without circuit breaker | ❌ High | Can cause cascading failures |

---

## Quick Audit Checklist for SDK Code

When a participant encounters Azure SDK usage during Day 3:

- [ ] **Authentication:** How are credentials provided? (DefaultAzureCredential = good, hardcoded = critical finding)
- [ ] **Error handling:** Are errors caught, logged, and handled appropriately? (empty catch = finding)
- [ ] **Retry policy:** Is there retry logic for transient failures? (none = medium finding)
- [ ] **Secrets management:** Are connection strings/keys in code, env vars, or Key Vault?
- [ ] **SDK version:** Is the SDK up to date? Are there known vulnerabilities?
- [ ] **Logging:** Are Azure operations logged with structured logging?
- [ ] **Timeouts:** Are timeouts configured to prevent hanging calls?
- [ ] **Disposal:** Are SDK clients properly disposed/closed? (memory leaks)

---

## Copilot Prompts for SDK Auditing

```
Review how Azure SDKs are used in this project. Check for:
1. Hardcoded credentials or connection strings
2. Empty or generic catch blocks around Azure calls
3. Missing retry logic for transient failures
4. Outdated SDK versions
Reference specific files and lines.
```

```
Find all Azure SDK authentication patterns in this codebase.
Are they using DefaultAzureCredential or hardcoded keys?
List each instance with file path and line number.
```

---

## Coach Quick Reference

| I see this in the code... | It means... | Severity |
|---|---|---|
| `DefaultAzureCredential` | Best practice auth | ✅ Good |
| `AccountKey=...` in a string | Embedded credential | ❌ Critical |
| `catch { }` (empty) | Silent failure | ❌ High |
| `console.log(error)` | Non-structured logging | ⚠️ Medium |
| No retry configuration | Default SDK retry applies | ℹ️ Note |
| `RetryMode.Exponential` | Intentional resilience | ✅ Good |
| Old SDK version | Potential vulnerabilities | ⚠️ Check |
