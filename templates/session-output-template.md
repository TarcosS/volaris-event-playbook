---
title: "Session Output"
layout: default
parent: "Templates"
nav_order: 3
---

> Use this template to record what happened during a session. One per session per participant or group.

---

## Session Output

| Field | Value |
|---|---|
| **Session Name** | [Living Documentation / Code & Infrastructure Audit / Ticket Triage] |
| **Date** | [Day and date] |
| **Participant / Group** | [Name or group identifier] |
| **Starting Level** | [Beginner / Intermediate / Advanced / Blocked] |
| **Path Selected** | [Baseline / Baseline (accelerated) / Advanced / Fallback] |

### Activities Completed

- [ ] [Activity 1 — e.g., "Repository exploration and mapping"]
- [ ] [Activity 2 — e.g., "Created README with setup instructions"]
- [ ] [Activity 3 — e.g., "Identified one security risk with evidence"]

### Output Created

[Describe the tangible output produced during the session. Reference specific files, templates, or issues.]

| Output Type | Description | Location |
|---|---|---|
| [Document / Finding / Issue / Risk Register] | [Brief description] | [File path, issue URL, or template reference] |

### Blockers Encountered

| Blocker | Resolution | Time Lost |
|---|---|---|
| [e.g., "Copilot extension not loading"] | [e.g., "Reinstalled extension, resolved in 3 min"] | [e.g., "5 min"] |
| [None] | — | — |

### Follow-Up Needed

- [ ] [e.g., "Deployment section of README still incomplete"]
- [ ] [e.g., "Access to Azure resolved — can do hands-on audit tomorrow"]
- [ ] [None — all outputs complete]

### Coach Notes

[Any observations about the participant's progress, engagement, or areas for attention in the next session. Brief and factual.]

---

## Example

| Field | Value |
|---|---|
| **Session Name** | Code & Infrastructure Audit |
| **Date** | Day 3 |
| **Participant / Group** | Group B — Table 4 |
| **Starting Level** | Intermediate |
| **Path Selected** | Baseline (accelerated) |

### Activities Completed

- [x] Reviewed codebase structure and identified main components
- [x] Used Copilot to scan for security risks
- [x] Verified one finding against actual code
- [x] Documented finding using Audit Finding Template

### Output Created

| Output Type | Description | Location |
|---|---|---|
| Audit Finding | Hardcoded database credentials in config file | `templates/audit-finding-template.md` (filled) |

### Blockers Encountered

| Blocker | Resolution | Time Lost |
|---|---|---|
| Initial Copilot suggestions were generic | Refined prompts with specific file references | 8 min |

### Follow-Up Needed

- [ ] Participant wants to find a second risk in the CI/CD pipeline on Day 4 if time allows
- [ ] Consider upgrading to advanced path for Day 4

### Coach Notes

Participant showed strong improvement from Day 2. Moved faster than expected on audit. Initially relied too heavily on Copilot but responded well to evidence coaching. Good candidate for advanced path upgrade on Day 4.
