# Output Templates

> All output templates collected in one place with descriptions and links.

---

## Purpose

This document provides an overview of every output template used during the event. Each template is a standalone Markdown file in the `/templates/` directory. Use the links below to navigate directly to the template you need.

---

## Template Index

| Template | Purpose | Used In |
|---|---|---|
| [Audit Finding Template](../templates/audit-finding-template.md) | Document a single audit finding with evidence, severity, and recommended fix | [Code/Infrastructure Audit Session](06-code-infrastructure-audit-session.md) |
| [GitHub Issue Template](../templates/github-issue-template.md) | Create a well-structured GitHub issue from an audit finding | [Ticket Triage Session](07-ticket-triage-session.md) |
| [Session Output Template](../templates/session-output-template.md) | Record what happened during a session — activities, outputs, blockers | All sessions, [Day-by-Day Flow](04-day-by-day-flow.md) |
| [Participant Diagnosis Sheet](../templates/participant-diagnosis-sheet.md) | Record participant skill assessment and path assignment | [Participant Diagnosis](03-participant-diagnosis.md), Day 1 |
| [Risk Register Template](../templates/risk-register-template.md) | Track multiple risks with severity, likelihood, impact, and actions | [Code/Infrastructure Audit Session](06-code-infrastructure-audit-session.md), advanced path |

---

## When to Use Each Template

### During Diagnosis (Day 1)

Use the **Participant Diagnosis Sheet** for each participant or group you assess. Record their responses, diagnostic task results, and assigned path. Refer to it on subsequent days to track progression.

### During Living Documentation (Day 2)

Use the **Session Output Template** to capture what each participant produced. This is especially important for tracking who completed which documentation artifacts and what follow-up is needed.

### During Code/Infrastructure Audit (Day 3)

Use the **Audit Finding Template** for each risk or issue identified. Advanced participants should also use the **Risk Register Template** to consolidate multiple findings into a structured register.

### During Ticket Triage (Day 4)

Use the **GitHub Issue Template** to convert audit findings into actionable tickets. The template ensures every issue has the fields needed for an engineer to act on it.

### At the End of Every Session

Use the **Session Output Template** to record the session summary. This is the coach's record of what happened and what needs follow-up.

---

## Living Documentation Output Format

When participants produce documentation (Day 2), their output should follow this general structure:

### README or Setup Guide

```markdown
# [Project Name]

## Overview
[What the application does — 2-3 sentences]

## Prerequisites
- [Runtime/SDK version]
- [Required tools]
- [Required accounts/access]

## Setup
1. Clone the repository
2. Install dependencies: `[command]`
3. Configure environment variables (see below)
4. Run the application: `[command]`

## Environment Variables
| Variable | Description | Required | Default |
|---|---|---|---|
| `DATABASE_URL` | Connection string for the database | Yes | None |
| `LOG_LEVEL` | Logging verbosity | No | `info` |

## Architecture
[High-level description of components and how they interact]

## Deployment
[How to deploy the application]

## Known Limitations
- [Limitation 1]
- [Limitation 2]

## Next Steps
- [Improvement 1]
- [Improvement 2]
```

---

## Audit Finding Output Format

See the full template: [Audit Finding Template](../templates/audit-finding-template.md)

**Quick example:**

| Field | Value |
|---|---|
| **Title** | Missing input validation on user registration endpoint |
| **Summary** | The `/api/register` endpoint accepts arbitrary input without validation |
| **Evidence** | `src/controllers/auth.js`, line 42 — request body is passed directly to the database query |
| **Category** | Security |
| **Severity** | High |
| **Confidence** | High |
| **Impact** | SQL injection or data integrity issues |
| **Recommended Fix** | Add input validation using a schema library (e.g., Joi, Zod) |

---

## GitHub Issue Output Format

See the full template: [GitHub Issue Template](../templates/github-issue-template.md)

**Quick example:**

> **Title:** Add input validation to user registration endpoint
>
> **Problem:** The `/api/register` endpoint accepts and processes user input without validation.
>
> **Evidence:** `src/controllers/auth.js`, line 42 — `db.query(req.body)` with no sanitization.
>
> **Impact:** Potential SQL injection. User data integrity cannot be guaranteed.
>
> **Proposed Solution:** Add Zod schema validation to all API endpoints, starting with registration.
>
> **Acceptance Criteria:**
> - [ ] All input fields are validated against a schema
> - [ ] Invalid input returns 400 with descriptive error message
> - [ ] SQL injection test cases pass
>
> **Priority:** High  
> **Effort:** Small (2-4 hours)

---

## Final Wrap-Up Summary Format

At the end of the event (Day 4), coaches should produce a brief summary:

```markdown
# Event Wrap-Up Summary

## Participants
- Total assessed: [number]
- Baseline path: [number]
- Advanced path: [number]
- Blocked / fallback: [number]

## Outputs Produced
- Documentation artifacts: [number]
- Audit findings: [number]
- GitHub issues created: [number]
- Risk registers completed: [number]
- Implementation plans: [number]

## Blockers Encountered
- [Blocker 1 — resolution]
- [Blocker 2 — resolution]

## Key Observations
- [Observation about skill distribution]
- [Observation about most common issues found]
- [Observation about coaching approach effectiveness]

## Recommendations for Next Event
- [Recommendation 1]
- [Recommendation 2]
```
