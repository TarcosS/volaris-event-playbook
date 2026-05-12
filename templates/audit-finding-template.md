---
title: "Audit Finding"
layout: default
parent: "Templates"
nav_order: 1
---

> Use this template to document each audit finding. Copy and fill in the fields below.

---

## Finding: [Title]

| Field | Value |
|---|---|
| **Title** | [Short, descriptive title of the finding] |
| **Summary** | [One or two sentences describing the finding] |
| **Evidence** | [File path, line number, configuration key, or observable behavior that demonstrates the finding] |
| **Category** | [Security / Reliability / Maintainability / Cloud Readiness / Observability / Cost / Developer Experience / Testing / CI/CD / Dependency Risk] |
| **Severity** | [Critical / High / Medium / Low] |
| **Confidence** | [High — directly observed / Medium — inferred from evidence / Low — suspected but unconfirmed] |
| **Impact** | [What happens if this is not addressed? Who or what is affected?] |
| **Recommended Fix** | [What should be done to resolve this finding?] |
| **Acceptance Criteria** | [How do we know the fix is complete and correct?] |
| **Dependencies** | [What must be in place before this can be fixed?] |
| **Notes** | [Any additional context, related findings, or observations] |

---

## Severity Guide

| Severity | Description |
|---|---|
| **Critical** | Active security vulnerability, data exposure, or production-impacting issue. Requires immediate attention. |
| **High** | Significant risk that could lead to incidents, data loss, or security compromise if not addressed soon. |
| **Medium** | Notable risk or quality issue that should be addressed in the near term but is not immediately dangerous. |
| **Low** | Minor improvement or best practice recommendation. Address when convenient. |

## Confidence Guide

| Confidence | Description |
|---|---|
| **High** | Directly observed in the code, configuration, or infrastructure. Evidence is clear and verifiable. |
| **Medium** | Inferred from evidence (e.g., patterns suggest a risk, but not directly confirmed). Needs verification. |
| **Low** | Suspected based on general knowledge or Copilot suggestion, but not confirmed with evidence. Requires investigation. |

---

## Example

| Field | Value |
|---|---|
| **Title** | API keys hardcoded in frontend configuration |
| **Summary** | Third-party API keys are stored as plaintext strings in the frontend JavaScript configuration file, visible to any user via browser developer tools. |
| **Evidence** | `src/config/api.js`, line 8: `const MAPS_API_KEY = "AIzaSyB..."` and line 9: `const PAYMENT_KEY = "sk_live_..."` |
| **Category** | Security |
| **Severity** | Critical |
| **Confidence** | High — directly observed in committed source code |
| **Impact** | API keys are exposed to all users. The payment key (`sk_live_`) is a production secret that could allow unauthorized transactions. The maps key could be abused for quota exhaustion. |
| **Recommended Fix** | Move API keys to server-side environment variables. For the frontend, use a backend proxy or token-based authentication. Rotate all exposed keys immediately. |
| **Acceptance Criteria** | No API keys are present in frontend source code. Backend proxy handles API calls. Exposed keys have been rotated. Secret scanning prevents future commits of key patterns. |
| **Dependencies** | Backend proxy endpoint must be created before frontend keys can be removed. |
| **Notes** | The payment key prefix `sk_live_` indicates this is a production key, not a test key. This finding should be reported privately — see [Escalation Matrix](../docs/12-escalation-matrix.md). |
