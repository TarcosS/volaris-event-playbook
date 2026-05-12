---
title: "Troubleshooting"
layout: default
nav_order: 11
---

> Quick-reference guide for resolving common event blockers. Follow the resolution path, apply the 5-minute rule, and switch to fallback if unresolved.

---

## How to Use This Guide

1. Identify the symptom
2. Run the quick checks
3. Follow the resolution path
4. If not resolved within 5 minutes, use the fallback path
5. If the fallback path is insufficient, escalate using the [Escalation Matrix](12-escalation-matrix.md)

**Golden rule:** No participant should sit idle for more than 5 minutes due to a technical issue. If you cannot fix it, switch them to an alternative activity immediately.

---

## Azure Issues

### Azure Login Failure

**Symptom:** Participant cannot log in to the Azure portal or CLI. Login page throws an error or redirects endlessly.

**Quick Checks:**
- [ ] Correct Microsoft account being used (work/school vs. personal)?
- [ ] Browser cache / incognito mode — try a private window
- [ ] Correct Azure portal URL: `portal.azure.com`
- [ ] VPN or corporate proxy interfering?

**Resolution Path:**
1. Try a different browser or incognito window
2. Clear browser cookies for `microsoft.com` and `azure.com`
3. Try Azure CLI login: `az login --use-device-code`
4. Check with event tech team if the account has been provisioned

**Fallback:** Switch to read/analyze mode — participant reviews code and infrastructure configs without logging in to Azure.

**When to Escalate:** If login fails across all methods and the account appears unprovisioned. → Event technical team.

---

### Wrong Tenant

**Symptom:** Participant logs in successfully but sees no subscriptions or resources. They may be in their company's tenant instead of the event tenant.

**Quick Checks:**
- [ ] Check tenant name in the top-right corner of Azure portal
- [ ] Click "Switch directory" and look for the event tenant
- [ ] Run `az account list` and check the tenant ID

**Resolution Path:**
1. Click "Switch directory" in Azure portal and select the event tenant
2. CLI: `az login --tenant <event-tenant-id>`
3. If the event tenant does not appear, the account may not have been added as a guest

**Fallback:** Pair with someone who has correct access. Switch to documentation or code review mode.

**When to Escalate:** If the participant's account is not in the event tenant. → Event technical team or org admin.

---

### Missing Subscription or Resource Group Access

**Symptom:** Participant is in the correct tenant but cannot see the subscription or resource group for the event.

**Quick Checks:**
- [ ] Check subscription filter in Azure portal (top filter bar)
- [ ] Run `az account list --output table` to see available subscriptions
- [ ] Check IAM (Access Control) for the resource group

**Resolution Path:**
1. Ensure the correct subscription is selected in the portal filter
2. If subscription is visible but resource group is not, check resource group permissions
3. If neither is visible, the participant needs a role assignment

**Fallback:** Audit infrastructure configuration files (Bicep, Terraform, ARM templates) in the repository without live Azure access.

**When to Escalate:** If role assignment is needed. → Event technical team or subscription admin.

---

### Read-Only Permissions

**Symptom:** Participant can view Azure resources but cannot create, modify, or deploy.

**Quick Checks:**
- [ ] Check role assignment: Reader vs. Contributor vs. Owner
- [ ] Run `az role assignment list --assignee <user-email>`

**Resolution Path:**
1. Request Contributor role for the event resource group
2. If role change is not possible, focus on read-only activities

**Fallback:** All audit and documentation activities work with read-only access. Deployment activities can be demonstrated by the coach.

**When to Escalate:** If Contributor access is needed and cannot be assigned. → Subscription admin.

---

### Cannot Deploy Resources

**Symptom:** Participant has write access but deployment fails. Errors about quotas, policies, or region restrictions.

**Quick Checks:**
- [ ] Check error message for quota limits
- [ ] Check Azure Policy assignments that may block resource types
- [ ] Verify the target region supports the resource type

**Resolution Path:**
1. Try a different region or smaller SKU
2. Check if Azure Policy is blocking the deployment and request an exception
3. If quota is exceeded, request a quota increase (event tech team)

**Fallback:** Review the deployment configuration and document what should be deployed without actually deploying. Create a deployment plan as the output.

**When to Escalate:** Quota increases or policy exceptions. → Event technical team or subscription admin.

---

### MFA Issues

**Symptom:** Multi-factor authentication is required but the participant's MFA is not set up, their phone is not available, or the MFA prompt is not arriving.

**Quick Checks:**
- [ ] Is MFA registered for this account?
- [ ] Is the phone available and has signal?
- [ ] Can they use the Microsoft Authenticator app instead of SMS?

**Resolution Path:**
1. Try a different MFA method (app, SMS, phone call)
2. If MFA is not registered, follow the registration flow
3. If the participant's personal phone is not available, check if temporary access passes are available

**Fallback:** Pair with someone who has authenticated access.

**When to Escalate:** If MFA cannot be completed and no temporary access pass is available. → Event technical team.

---

## GitHub Issues

### GitHub Login Failure

**Symptom:** Participant cannot log in to GitHub or is logged in to the wrong account.

**Quick Checks:**
- [ ] Correct GitHub account (personal vs. work)?
- [ ] Password/2FA issues?
- [ ] Browser cache / incognito mode

**Resolution Path:**
1. Try logging in from a private browser window
2. If 2FA is the issue, check for backup codes
3. If the wrong account, log out and use the correct account

**Fallback:** Pair with someone who has access. The blocked participant can drive documentation or review work.

**When to Escalate:** Account lockout or lost 2FA. → GitHub admin or event tech team.

---

### Copilot License Not Active

**Symptom:** Copilot suggestions do not appear. The Copilot icon is grayed out or shows "not available."

**Quick Checks:**
- [ ] Is the Copilot extension installed and enabled?
- [ ] Check VS Code / IDE bottom bar — does it show "Copilot" active?
- [ ] Is the user's GitHub account assigned a Copilot license?
- [ ] Check: `https://github.com/settings/copilot`

**Resolution Path:**
1. Verify Copilot is enabled at `github.com/settings/copilot`
2. If not enabled, check organization seat assignment
3. Reload the IDE / restart the extension
4. Check if the organization has Copilot Business/Enterprise enabled

**Fallback:** Participant works without Copilot — manual code review, documentation, and ticket writing. All activities are achievable without Copilot; it just takes longer.

**When to Escalate:** If Copilot license is not assigned and cannot be assigned. → GitHub org admin.

---

### Copilot Extension Not Working

**Symptom:** Copilot is licensed but the extension does not provide suggestions, or it throws errors.

**Quick Checks:**
- [ ] Extension installed and up to date?
- [ ] IDE restarted after installation?
- [ ] Check extension output logs for errors
- [ ] Network connectivity — can the IDE reach GitHub's API?

**Resolution Path:**
1. Uninstall and reinstall the Copilot extension
2. Restart the IDE
3. Check for proxy or firewall blocking Copilot's endpoints
4. Try a different file type (some extensions activate only for certain languages)

**Fallback:** Manual coding and review. All activities work without Copilot.

**When to Escalate:** If the extension consistently fails and network issues are ruled out. → Event tech team.

---

### Organization Policy Blocking Copilot

**Symptom:** Copilot is installed and licensed but the organization has a policy that blocks it for certain repositories or contexts.

**Quick Checks:**
- [ ] Check organization Copilot settings
- [ ] Check repository-level Copilot settings
- [ ] Is there a content exclusion policy?

**Resolution Path:**
1. Check with org admin if Copilot is enabled for the event repositories
2. If policy-blocked, request a temporary exception for the event

**Fallback:** Work without Copilot. All activities are designed to be completable without AI assistance.

**When to Escalate:** If org policy cannot be changed. → Organization admin.

---

### Repository Access Denied

**Symptom:** Participant gets 404 or 403 when trying to access the assigned repository.

**Quick Checks:**
- [ ] Correct URL?
- [ ] Correct GitHub account?
- [ ] Is the participant a member of the organization?
- [ ] Is the repository private?

**Resolution Path:**
1. Verify the repository URL
2. Check that the participant is logged in to the correct GitHub account
3. Verify organization membership
4. If not a member, invite them to the organization or the specific repository

**Fallback:** Work on a public fork or a different accessible repository. Pair with someone who has access.

**When to Escalate:** If organization membership cannot be granted. → GitHub org admin.

---

## Network and Local Environment Issues

### Network or Firewall Issues

**Symptom:** Participant's network blocks access to Azure, GitHub, or Copilot endpoints. Corporate VPN or firewall restrictions.

**Quick Checks:**
- [ ] Can they reach `github.com` in a browser?
- [ ] Can they reach `portal.azure.com`?
- [ ] Are they on a corporate VPN?
- [ ] Can they use a mobile hotspot as a temporary alternative?

**Resolution Path:**
1. Disconnect from corporate VPN and use event Wi-Fi
2. If event Wi-Fi also blocks endpoints, try a mobile hotspot
3. Check with event tech team for allowed network configurations

**Fallback:** If no network access can be established, the participant works offline: reviewing local files, writing documentation, creating ticket drafts.

**When to Escalate:** If the event network itself blocks required endpoints. → Event tech team (network admin).

---

### Local Environment Setup Problems

**Symptom:** Participant's local machine is not set up for development — missing IDE, missing runtimes, missing CLI tools.

**Quick Checks:**
- [ ] Is VS Code (or required IDE) installed?
- [ ] Is Git installed and configured?
- [ ] Are required runtimes installed (Node.js, .NET, Python, etc.)?
- [ ] Is Azure CLI installed?
- [ ] Is GitHub CLI installed?

**Resolution Path:**
1. Install missing tools (provide URLs and quick install commands)
2. For VS Code: `code.visualstudio.com`
3. For Azure CLI: `aka.ms/installazurecli`
4. For Git: `git-scm.com`

**Fallback:** Use GitHub's web-based editor (press `.` in any repository) or GitHub Codespaces if available. Web-based tools avoid all local setup issues.

**When to Escalate:** If the participant's machine has IT restrictions that prevent software installation. → Event tech team.

---

### IDE Problems

**Symptom:** IDE crashes, freezes, or behaves unexpectedly.

**Quick Checks:**
- [ ] IDE updated to latest version?
- [ ] Extensions conflicting?
- [ ] Sufficient disk space and memory?

**Resolution Path:**
1. Restart the IDE
2. Disable non-essential extensions
3. Try a clean launch: `code --disable-extensions`
4. If persistent, use the GitHub web editor as a fallback

**Fallback:** GitHub web editor (`.` key in repository) or a terminal-based editor.

**When to Escalate:** Only if the IDE issue cannot be resolved and web alternatives are also blocked.

---

### CLI Not Installed

**Symptom:** Participant needs to use Azure CLI, GitHub CLI, or other command-line tools but they are not installed.

**Quick Checks:**
- [ ] `az --version` — Azure CLI
- [ ] `gh --version` — GitHub CLI
- [ ] `git --version` — Git
- [ ] `node --version` / `dotnet --version` — runtimes

**Resolution Path:**
1. Install via package manager (brew, winget, apt, etc.)
2. Provide direct download URLs
3. For Azure CLI on macOS: `brew install azure-cli`
4. For GitHub CLI: `brew install gh` or `winget install gh`

**Fallback:** Use web-based alternatives (Azure Portal, GitHub web UI) instead of CLI.

**When to Escalate:** If installation is blocked by IT policy. → Event tech team.

---

### Dependency Install Failures

**Symptom:** `npm install`, `dotnet restore`, `pip install`, or equivalent fails. Missing packages, version conflicts, or network errors.

**Quick Checks:**
- [ ] Correct package manager version?
- [ ] Network access to package registries (npmjs.org, nuget.org, pypi.org)?
- [ ] Corporate proxy blocking package downloads?
- [ ] Lock file present and consistent?

**Resolution Path:**
1. Try installing with verbose logging to identify the specific failure
2. If a proxy is the issue, configure the package manager's proxy settings
3. If a specific package fails, try installing it individually
4. Clear the package cache and retry

**Fallback:** If dependencies cannot be installed, switch to code review mode — the participant reads and audits the code without running it.

**When to Escalate:** If the package registry is blocked by network policy. → Event tech team.

---

## Fallback Activity Quick Reference

When access cannot be fixed, switch the participant to one of these activities immediately:

| Fallback Mode | What They Do | What They Produce |
|---|---|---|
| **Read/Analyze** | Review code and configs without write access | Audit findings, documented observations |
| **Pairing** | Work alongside a participant with full access | Shared outputs, collaborative findings |
| **Coach Demo** | Watch the coach demonstrate; take notes | Documented observations, questions, ticket drafts |
| **Documentation** | Write documentation, templates, or guides | README, setup guide, architecture notes |
| **Ticket Writing** | Create issue drafts based on observed findings | GitHub issue drafts (submit when access is restored) |
| **Architecture Review** | Diagram and document system architecture | Architecture overview, component diagrams |
