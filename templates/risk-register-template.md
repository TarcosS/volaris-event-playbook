# Risk Register Template

> Use this template to track multiple risks in a consolidated register. Primarily for advanced participants during the Code/Infrastructure Audit session.

---

## Risk Register: [Repository or System Name]

**Auditor:** [Name or group]  
**Date:** [Date]  
**Scope:** [What was audited — e.g., "Full repository", "Backend services only", "Infrastructure configuration"]

---

### Register

| Risk ID | Description | Category | Evidence | Severity | Likelihood | Impact | Owner | Recommended Action | Status |
|---|---|---|---|---|---|---|---|---|---|
| R-001 | [Short description] | [Category] | [File/line/config reference] | [Critical/High/Medium/Low] | [High/Medium/Low] | [What happens if it occurs] | [Team/role] | [What to do] | [Open/In Progress/Mitigated/Accepted] |
| R-002 | | | | | | | | | |
| R-003 | | | | | | | | | |
| R-004 | | | | | | | | | |
| R-005 | | | | | | | | | |

---

### Field Definitions

| Field | Description |
|---|---|
| **Risk ID** | Unique identifier (e.g., R-001, R-002) |
| **Description** | Short, clear description of the risk |
| **Category** | Security / Reliability / Maintainability / Cloud Readiness / Observability / Cost / Developer Experience / Testing / CI/CD / Dependency Risk |
| **Evidence** | Specific reference to the file, line, configuration, or behavior |
| **Severity** | How bad is it if it happens? Critical / High / Medium / Low |
| **Likelihood** | How likely is it to happen? High / Medium / Low |
| **Impact** | What is the blast radius? What breaks, leaks, or degrades? |
| **Owner** | Who is responsible for addressing this risk? |
| **Recommended Action** | What should be done? Be specific. |
| **Status** | Open (unaddressed), In Progress (being fixed), Mitigated (fixed), Accepted (acknowledged, no action planned) |

### Severity × Likelihood Matrix

| | **High Likelihood** | **Medium Likelihood** | **Low Likelihood** |
|---|---|---|---|
| **Critical Severity** | 🔴 Immediate action | 🔴 Immediate action | 🟠 Plan urgently |
| **High Severity** | 🔴 Immediate action | 🟠 Plan urgently | 🟡 Plan soon |
| **Medium Severity** | 🟠 Plan urgently | 🟡 Plan soon | 🔵 Address when convenient |
| **Low Severity** | 🟡 Plan soon | 🔵 Address when convenient | ⚪ Accept or defer |

---

## Example

### Risk Register: Contoso Retail API

**Auditor:** Group A — Table 2  
**Date:** Day 3  
**Scope:** Full repository — backend API and infrastructure configuration

| Risk ID | Description | Category | Evidence | Severity | Likelihood | Impact | Owner | Recommended Action | Status |
|---|---|---|---|---|---|---|---|---|---|
| R-001 | Production database password hardcoded in config | Security | `src/appsettings.json:12` | Critical | High | Credential exposure to all repo readers | Platform team | Move to Key Vault; rotate password; add secret scanning | Open |
| R-002 | No rate limiting on authentication endpoints | Security | `src/routes/auth.js:15-40` — no middleware | High | High | Brute-force attacks on login | Backend team | Add rate-limiting middleware; log violations | Open |
| R-003 | Error in payment processing silently swallowed | Reliability | `src/services/payment.js:67` — empty catch block | High | Medium | Failed payments not detected; revenue loss | Backend team | Log error, notify ops, return appropriate error to caller | Open |
| R-004 | No health check endpoint | Reliability | No `/health` route in `src/routes/` | Medium | Medium | Load balancer cannot detect unhealthy instances | Backend team | Add `/health` endpoint returning service and dependency status | Open |
| R-005 | 47 npm packages with known vulnerabilities | Dependency Risk | `npm audit` output — 12 high, 35 moderate | Medium | High | Exploitable vulnerabilities in production dependencies | Backend team | Run `npm audit fix`; manually update breaking changes; add audit to CI | Open |
| R-006 | No structured logging | Observability | All logging uses `console.log` — `src/` (multiple files) | Medium | Low | Cannot search, filter, or alert on log data in production | Backend team | Replace console.log with structured logging library (e.g., pino, winston) | Open |
| R-007 | CI pipeline has no security scanning step | CI/CD | `.github/workflows/ci.yml` — build and test only | Medium | Medium | Vulnerabilities and secrets may be deployed without detection | DevOps team | Add dependency scanning, secret scanning, and SAST to CI pipeline | Open |

### Summary

| Severity | Count |
|---|---|
| Critical | 1 |
| High | 2 |
| Medium | 4 |
| Low | 0 |
| **Total** | **7** |

### Top 3 Priority Actions

1. **R-001 (Critical):** Remove hardcoded database password and move to Key Vault immediately
2. **R-002 (High):** Add rate limiting to authentication endpoints before next deployment
3. **R-003 (High):** Fix silent error swallowing in payment processing
