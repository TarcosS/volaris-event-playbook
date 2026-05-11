# Participant Diagnosis

> How to assess participant skill level and select the right coaching path.

---

## Purpose

Participant diagnosis is the first step of every coaching interaction. Before guiding any activity, determine where the participant stands so you can select the baseline or advanced path. This document provides the questions, classification criteria, and diagnostic tasks to make that decision quickly and confidently.

## Quick Diagnosis Questions

Ask these questions at the start of each session. Listen for specifics — not just "yes" or "no," but the depth and confidence of the answer.

| # | Question | What You're Looking For |
|---|---|---|
| 1 | Have you deployed resources to Azure before? | Hands-on experience vs. theoretical knowledge. Listen for specifics: portal, CLI, Bicep, Terraform, or ARM. |
| 2 | Have you used GitHub Actions? | Familiarity with CI/CD concepts and GitHub-specific workflows. |
| 3 | Do you actively use GitHub Copilot? | Regular usage vs. tried-it-once. Ask what they use it for. |
| 4 | Have you used AI-assisted coding for a real feature, refactor, or audit? | Practical application vs. experimentation. Real projects signal advanced readiness. |
| 5 | Do you have Infrastructure as Code experience with Bicep, Terraform, or ARM? | IaC experience indicates infrastructure reasoning ability. |
| 6 | What do you want to leave with today? | Signals motivation and helps you set expectations. Vague answers may indicate unclear goals. |

### How to Ask

Keep it conversational. Do not read the questions like a checklist.

**Example opening:**

> "Before we decide how deep to go, I want to quickly understand your current experience. Have you worked with Azure, GitHub Copilot, or infrastructure/code auditing in a real project before?"

Follow up based on their answer. If they mention specific tools or projects, probe deeper. If they give general answers, move on — you will learn more from the diagnostic task.

---

## Classification Table

Based on the answers and the diagnostic task, classify each participant into one of five levels:

| Level | Signals | Coach Action | Recommended Path | Output Target |
|---|---|---|---|---|
| **Beginner** | Has not deployed to Azure. Limited GitHub experience. Has not used Copilot meaningfully. Struggles with basic codebase navigation. | Provide step-by-step guidance. Use baseline path. Pair with an intermediate participant if possible. | Baseline | One documented understanding + one identified risk + one GitHub issue |
| **Intermediate** | Has Azure/GitHub experience but limited audit or documentation skills. Uses Copilot but does not verify output. Can navigate code but struggles to identify risks. | Guide with structured prompts. Use baseline path with faster pacing. Challenge them to find evidence. | Baseline (accelerated) | Baseline outputs + attempt one advanced output |
| **Advanced** | Explains systems confidently with specifics. Uses Copilot as a reasoning tool and verifies output. Identifies risks from code/config evidence. Has IaC experience. | Move to advanced path quickly. Provide audit categories and let them self-direct. Check in periodically. | Advanced | Full audit report + risk register + prioritized backlog |
| **Blocked** | Cannot access Azure, GitHub, or Copilot. Environment or tooling issues prevent any hands-on work. | Resolve the blocker (5-minute rule). If unresolved, switch to fallback mode: pairing, demo, documentation, or architecture review. | Fallback | Whatever is achievable in the fallback mode |
| **Unclear** | Gives vague or inconsistent answers. Difficult to classify from questions alone. | Run the diagnostic task. Observe their approach and classify based on behavior, not self-reporting. | Start with baseline, upgrade if warranted | Baseline initially, adjust based on performance |

---

## Diagnostic Task

When the quick questions are not enough to classify a participant (or to confirm your classification), use this hands-on diagnostic task.

### The Task

Ask the participant to use GitHub Copilot to inspect a repository and answer four questions:

1. **What does this application do?** (System understanding)
2. **Where is the main entry point?** (Code navigation)
3. **What risks or missing documentation exist?** (Critical thinking)
4. **Write one improvement ticket.** (Output creation)

### How to Run It

1. Point the participant at the event's assigned repository
2. Ask them to use Copilot to explore and answer the four questions
3. Set a time limit: **10 minutes**
4. Observe their process — how they use Copilot, whether they verify answers, and how specific their responses are

### Interpretation Guide

| Observation | Classification | Next Step |
|---|---|---|
| **Struggles to start** — cannot navigate the repo, does not know how to prompt Copilot, or gets stuck on basic setup | Beginner | Move to baseline path. Provide guided walkthrough. |
| **Gives generic answers** — "the app does stuff with data," "it could use better docs" — without pointing to specific files, functions, or configurations | Intermediate (needs coaching) | Stay on baseline path. Use prompt coaching: "Can you point to a specific file or config that shows this?" |
| **Reasons from evidence** — identifies the entry point by file/function name, finds specific risks with code references, writes a ticket with a clear problem statement and evidence | Advanced | Move to advanced path. Provide audit categories and let them run. |
| **Cannot access tools** — Copilot is not working, GitHub access is denied, or Azure is not configured | Blocked | Trigger the [Troubleshooting Guide](09-troubleshooting-guide.md). Apply the 5-minute rule. Switch to fallback if unresolved. |
| **Finishes too quickly with surface-level answers** — completes in 2 minutes but answers lack depth | Unclear (possibly overconfident) | Challenge: "You mentioned a risk — can you show me the code that creates this risk?" Reclassify based on response. |

---

## Decision Flowchart

```
START: Ask diagnostic questions
  │
  ├─ Participant cannot access tools?
  │   └─ YES → Blocked → Troubleshooting Guide → Fallback path
  │
  ├─ Answers are clear and specific?
  │   ├─ YES → Run diagnostic task
  │   │   ├─ Reasons from evidence → Advanced path
  │   │   ├─ Gives generic answers → Baseline path (with prompt coaching)
  │   │   └─ Struggles to start → Baseline path (guided)
  │   │
  │   └─ NO → Run diagnostic task
  │       ├─ Performs well → Intermediate/Advanced (reclassify)
  │       └─ Struggles → Beginner (baseline, guided)
  │
  └─ Participant is unclear or inconsistent?
      └─ Run diagnostic task → Classify based on behavior
```

---

## Diagnosis Timing

| Session | When to Diagnose | Time Budget |
|---|---|---|
| Day 1 — Orientation | Full diagnosis: questions + task | 15–20 minutes |
| Day 2 — Living Documentation | Quick check: has anything changed since Day 1? | 2–3 minutes |
| Day 3 — Code/Infrastructure Audit | Quick check: did they advance on Day 2? | 2–3 minutes |
| Day 4 — Ticket Triage | Quick check: are they ready for independent work? | 2–3 minutes |

After the initial Day 1 diagnosis, subsequent checks are fast. Look for signals that a participant has grown (upgrade to advanced) or is struggling (downgrade to baseline or fallback).

---

## Recording Diagnosis

Use the [Participant Diagnosis Sheet](../templates/participant-diagnosis-sheet.md) to record each participant's or group's classification. Keep brief notes so you can reference them across days.

---

## Common Diagnosis Mistakes

| Mistake | Why It Happens | How to Avoid |
|---|---|---|
| Trusting self-reported skill level | Participants may overestimate or underestimate | Always run the diagnostic task for unclear cases |
| Classifying based on job title | "Senior developer" does not mean "advanced in this context" | Focus on demonstrated ability with the specific tools |
| Skipping diagnosis for returning participants | Assumes Day 1 classification is still valid | Do a quick check each day — people learn fast |
| Not recognizing blocked participants | Access issues can look like low skill | Check tools and access before judging ability |
