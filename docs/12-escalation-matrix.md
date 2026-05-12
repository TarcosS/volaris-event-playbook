---
title: "Escalation Matrix"
layout: default
nav_order: 14
---

> When to handle an issue yourself and when to escalate. Use this during the event to make fast decisions about who should resolve what.

---

## How to Use This Document

1. Identify the issue category
2. Check if it is something you (the coach) can resolve
3. If not, escalate to the appropriate team
4. Apply the fallback path immediately — do not wait for escalation to resolve

**Rule:** Escalate in parallel with applying the fallback. The participant should never wait idle for an escalation to resolve.

---

## Escalation Levels

| Level | Who | Response Time | Examples |
|---|---|---|---|
| **Coach** | You (the developer coach) | Immediate | Copilot prompts, code navigation, methodology questions, scope reduction |
| **Event Technical Team** | On-site technical support | Minutes | Azure provisioning, network issues, machine configuration |
| **Organization Admin** | GitHub/Azure org administrator | Minutes to hours | Org membership, license assignment, policy changes |
| **Out of Scope** | Beyond the event's ability to resolve | N/A | Hardware failures, personal account issues, third-party service outages |

---

## Escalation Table

| Issue Category | Examples | Coach Handles? | Escalate to Event Tech Team? | Escalate to Org Admin? | Fallback Path |
|---|---|---|---|---|---|
| **Azure tenant/access** | Wrong tenant, no guest access, account not provisioned | Try switch directory | Yes — if account needs provisioning | Yes — if tenant config needs changes | Pair mode, code review without Azure |
| **Azure subscription permissions** | No subscription visible, Reader instead of Contributor, quota exceeded | Check filters and role | Yes — for role assignments and quotas | Yes — if subscription-level changes needed | Read-only audit, IaC review from files |
| **Azure deployment failures** | Policy blocks, region restrictions, SKU unavailable | Try alternative region/SKU | Yes — for policy exceptions | Rarely | Document deployment plan as output |
| **GitHub organization policy** | Copilot blocked by policy, SAML required, IP restrictions | Check org settings | No | Yes — policy changes need admin | Work without Copilot, use web UI |
| **GitHub repository access** | 404/403 on repo, not an org member, wrong account | Verify URL and account | Yes — for org invitations | Yes — if membership needs admin approval | Pair mode, work on public repos |
| **Copilot licensing** | No Copilot seat, license expired, wrong plan | Check settings page | No | Yes — seat assignment needs admin | All activities work without Copilot |
| **Copilot extension** | Extension not working, no suggestions, errors | Reinstall, restart IDE | Yes — if network/proxy issue | No | Manual code review |
| **Network/firewall** | Cannot reach github.com, azure.com, or package registries | Try VPN disconnect, hotspot | Yes — for network configuration | No | Offline work, local file review |
| **Local machine restrictions** | Cannot install software, admin rights required | Use web alternatives | Yes — for temporary admin or alternatives | No | GitHub web editor, Codespaces |
| **Security-sensitive findings** | Exposed credentials, active vulnerabilities in production | Document and escalate | Yes — security findings need immediate attention | Yes — if production-impacting | Do not publish publicly; report privately |
| **Production-impacting findings** | Active bugs in production, data integrity issues | Document and escalate | Yes — for awareness | Yes — for action | Document finding; do not attempt to fix in production |

---

## Escalation Decision Flow

```
Issue identified
  │
  ├─ Can the coach resolve it in < 5 minutes?
  │   ├─ YES → Resolve it. Continue the session.
  │   └─ NO ↓
  │
  ├─ Is it a technical/infrastructure issue?
  │   ├─ YES → Escalate to Event Technical Team
  │   │         Apply fallback path immediately
  │   └─ NO ↓
  │
  ├─ Is it an organization/admin issue?
  │   ├─ YES → Escalate to Organization Admin
  │   │         Apply fallback path immediately
  │   └─ NO ↓
  │
  ├─ Is it a security or production concern?
  │   ├─ YES → Escalate to BOTH tech team AND org admin
  │   │         Document privately. Do not publish.
  │   └─ NO ↓
  │
  └─ Out of scope → Document the issue, apply fallback,
                      and move on. Do not spend more time.
```

---

## How to Escalate

When you need to escalate:

1. **Identify the issue** clearly — what is happening and what has been tried
2. **Contact the right person/team** — use the event's communication channel (Slack, Teams, in-person)
3. **Provide details:**
   - Participant name or identifier
   - Issue description
   - What you have already tried
   - What access or change is needed
4. **Apply the fallback path immediately** — do not wait for resolution
5. **Follow up** during the next break to check status

### Escalation Message Template

> **Issue:** [Brief description]  
> **Participant:** [Name or identifier]  
> **Tried:** [What you already attempted]  
> **Need:** [Specific action needed — e.g., "Add user X to the event tenant as Guest"]  
> **Urgency:** [Blocking all work / Blocking specific activity / Can work around]

---

## Security and Production Findings

Special handling is required when participants find security vulnerabilities or production-impacting issues:

| Finding Type | Action |
|---|---|
| **Exposed credentials in repository** | Do NOT create a public issue. Report privately to org admin. Document in the risk register with restricted access. |
| **Active security vulnerability** | Report to event tech team and org admin. Recommend immediate remediation. Document privately. |
| **Production data exposure** | Escalate immediately to org admin. Do not access or copy the data. Document the finding and evidence path only. |
| **Infrastructure misconfiguration with active risk** | Report to tech team. Document the finding and recommended fix. Let the responsible team decide on remediation timing. |

### Script for Security Findings

> "This is a real finding, and it's important. Because it's security-sensitive, we are going to document it privately and report it to the right team instead of creating a public issue. This is the professional way to handle security findings."
