---
title: "Azure"
layout: default
parent: "Tool Guides"
nav_order: 3
---

> Step-by-step Azure commands and procedures coaches will use and teach during the event.

---

## Logging In

### Azure Portal

1. Go to `https://portal.azure.com`
2. Sign in with the event-provided Microsoft account
3. **Check tenant:** top-right corner shows the tenant name
4. If wrong tenant: click user icon → "Switch directory" → select event tenant

### Azure CLI

```bash
# Basic login (opens browser)
az login

# Login with device code (useful when browser redirect fails)
az login --use-device-code

# Login to a specific tenant
az login --tenant <tenant-id>

# Verify current account
az account show --output table

# List all available subscriptions
az account list --output table

# Set the correct subscription
az account set --subscription "<subscription-name-or-id>"
```

### Coach Checklist

- [ ] Participant can log in to Azure portal
- [ ] Correct tenant is selected
- [ ] Event subscription is visible
- [ ] Azure CLI authenticated (`az account show` returns correct tenant)

---

## Troubleshooting

### Cannot Log In

| Issue | Fix |
|---|---|
| Login page loops | Try incognito/private window |
| Wrong account cached | Clear browser cookies for `*.microsoft.com` |
| Corporate SSO interferes | Use `az login --use-device-code` instead |
| MFA not set up | Follow the MFA registration flow when prompted |
| Account not provisioned | Escalate to event tech team |

### Wrong Tenant

```bash
# List available tenants
az account list --output table --all

# Switch to event tenant
az login --tenant <event-tenant-id>
```

In the portal: click user icon → "Switch directory" → select the event directory.

### No Subscription Visible

```bash
# Check subscription filter (portal may be filtering)
# In portal: top filter bar → ensure "All subscriptions" is selected

# CLI: list all subscriptions (including disabled)
az account list --all --output table
```

If no subscription appears, the participant needs a role assignment. Escalate to event tech team.

---

## Resource Inspection

### Useful Commands for Auditing

```bash
# List all resource groups in the subscription
az group list --output table

# List all resources in a specific resource group
az resource list --resource-group <rg-name> --output table

# Get details of a specific resource
az resource show --ids <resource-id>

# List role assignments for the current user
az role assignment list --assignee <user-email> --output table

# List role assignments for a resource group
az role assignment list --resource-group <rg-name> --output table
```

### Security-Relevant Commands

```bash
# Check network security groups
az network nsg list --resource-group <rg-name> --output table
az network nsg rule list --nsg-name <nsg-name> --resource-group <rg-name> --output table

# Check Key Vault access policies
az keyvault list --resource-group <rg-name> --output table
az keyvault show --name <vault-name> --query "properties.accessPolicies"

# Check storage account access
az storage account list --resource-group <rg-name> --output table
az storage account show --name <account-name> --query "allowBlobPublicAccess"

# Check App Service configuration
az webapp config show --name <app-name> --resource-group <rg-name>
az webapp config appsettings list --name <app-name> --resource-group <rg-name>
```

### Infrastructure as Code Review

```bash
# If using Bicep — list Bicep files in the repo
find . -name "*.bicep" -type f

# If using Terraform
find . -name "*.tf" -type f

# If using ARM templates
find . -name "*.json" -path "*/templates/*" -type f
```

Participants can audit these files directly without Azure access — they are code.

---

## Common Tasks During the Event

### Day 1: Verify Access

```bash
# Full verification sequence
az login
az account show --output table          # Confirm tenant
az account list --output table          # Confirm subscription
az group list --output table            # Confirm resource group access
```

### Day 3: Infrastructure Audit

```bash
# Quick security scan of a resource group
az resource list --resource-group <rg-name> --output table
az role assignment list --resource-group <rg-name> --output table
az network nsg list --resource-group <rg-name> --output table

# Check for publicly accessible resources
az storage account list --query "[?allowBlobPublicAccess==true]" --output table
az webapp list --query "[?httpsOnly==false]" --output table
```

### Fallback: No Azure Access

If a participant cannot access Azure:
1. They can still audit IaC files (Bicep/Terraform/ARM) as code
2. They can review Azure configuration referenced in app settings
3. They can review CI/CD pipeline Azure deployment steps
4. Coach can demonstrate Azure portal inspection while participant observes

---

## Azure for Coaches: Quick Reference

| Task | Command |
|---|---|
| Who am I? | `az account show --output table` |
| List subscriptions | `az account list --output table` |
| Switch subscription | `az account set --subscription "name"` |
| List resources | `az resource list -g <rg> --output table` |
| Check RBAC | `az role assignment list -g <rg> --output table` |
| Check NSGs | `az network nsg list -g <rg> --output table` |
| Check Key Vault | `az keyvault list -g <rg> --output table` |
| Check app config | `az webapp config appsettings list -n <app> -g <rg>` |
