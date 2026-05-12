---
title: "Participant Diagnosis Sheet"
layout: default
parent: "Templates"
nav_order: 4
---

> Use this template to record the diagnosis of each participant or group. Fill in during Day 1 and update on subsequent days.

---

## Participant / Group: [Name or Identifier]

### Quick Diagnosis Responses

| # | Question | Response | Notes |
|---|---|---|---|
| 1 | Have you deployed resources to Azure before? | [Yes — details / No] | |
| 2 | Have you used GitHub Actions? | [Yes — details / No] | |
| 3 | Do you actively use GitHub Copilot? | [Yes — how / No / Tried once] | |
| 4 | Have you used AI-assisted coding for a real task? | [Yes — describe / No] | |
| 5 | Do you have IaC experience (Bicep/Terraform/ARM)? | [Yes — which / No] | |
| 6 | What do you want to leave with today? | [Their answer] | |

### Diagnostic Task Result

| Criterion | Observation |
|---|---|
| **What the app does** | [Did they explain it? How specific?] |
| **Main entry point** | [Did they find it? By file/function name?] |
| **Risks or missing docs** | [Did they identify real issues with evidence?] |
| **Improvement ticket** | [Did they write one? Was it specific and actionable?] |

### Overall Assessment

| Field | Value |
|---|---|
| **Assigned Level** | [Beginner / Intermediate / Advanced / Blocked / Unclear] |
| **Recommended Path** | [Baseline / Baseline (accelerated) / Advanced / Fallback] |
| **Confidence in Assessment** | [High / Medium / Low] |
| **Notes** | [Any relevant context — e.g., "Strong backend skills but no cloud experience"] |

### Day-Over-Day Tracking

| Day | Level | Path | Key Observation |
|---|---|---|---|
| Day 1 | [Level] | [Path] | [Initial assessment notes] |
| Day 2 | [Level — updated?] | [Path — changed?] | [Progress or change noted] |
| Day 3 | [Level — updated?] | [Path — changed?] | [Progress or change noted] |
| Day 4 | [Level — updated?] | [Path — changed?] | [Final assessment] |

---

## Example

### Participant / Group: Group C — Table 7

### Quick Diagnosis Responses

| # | Question | Response | Notes |
|---|---|---|---|
| 1 | Have you deployed resources to Azure before? | Yes — used ARM templates to deploy VMs | Has Azure experience but with older tooling |
| 2 | Have you used GitHub Actions? | No — uses Jenkins | CI/CD experience exists, just different platform |
| 3 | Do you actively use GitHub Copilot? | Tried it once | Low practical experience |
| 4 | Have you used AI-assisted coding for a real task? | No | |
| 5 | Do you have IaC experience (Bicep/Terraform/ARM)? | Yes — ARM templates | Familiar with IaC concepts |
| 6 | What do you want to leave with today? | "Learn how to use AI for code review" | Clear goal, well-scoped |

### Diagnostic Task Result

| Criterion | Observation |
|---|---|
| **What the app does** | Identified it as a REST API but missed the background worker service |
| **Main entry point** | Found `Program.cs` but did not trace the startup configuration |
| **Risks or missing docs** | Said "docs are incomplete" but did not specify what was missing |
| **Improvement ticket** | Wrote "add better documentation" — too vague |

### Overall Assessment

| Field | Value |
|---|---|
| **Assigned Level** | Intermediate |
| **Recommended Path** | Baseline (accelerated) |
| **Confidence in Assessment** | Medium — has infrastructure background but Copilot/GitHub skills are new |
| **Notes** | Strong on infrastructure concepts, needs coaching on evidence-based auditing and Copilot usage. Should improve quickly. |

### Day-Over-Day Tracking

| Day | Level | Path | Key Observation |
|---|---|---|---|
| Day 1 | Intermediate | Baseline (accelerated) | Good infra background, new to Copilot |
| Day 2 | Intermediate | Baseline (accelerated) | Produced solid README; started using Copilot more effectively |
| Day 3 | Intermediate → Advanced | Advanced | Found real security finding with evidence; upgraded to advanced path |
| Day 4 | Advanced | Advanced | Created 4 GitHub issues with full evidence and acceptance criteria |
