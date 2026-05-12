---
title: "Day-by-Day Flow"
layout: default
nav_order: 5
---

> Detailed schedule for all four days of the event, including coach checklists, participant outputs, decision branches, and risks.

---

## How to Use This Document

Review the relevant day's section **before** the day starts. Use the coach checklist to confirm readiness, follow the if/else branches during the session, and verify the definition of done at the end of each day.

**For an interactive, checkbox-driven version of this schedule, use the [Coach Runbook](14-coach-runbook.md).** The runbook links to tool guides for step-by-step Copilot, Azure, CLI, MCP, and Skills instructions.

---

## Day 1: Orientation, Setup, and Diagnosis

### Purpose
Ensure every participant has working access to all tools, establish the coaching relationship, and diagnose skill levels to select the right path for the rest of the event.

### Schedule Overview

| Block | Activity | Duration |
|---|---|---|
| Opening | Event welcome, introduction to coaches, agenda overview | 15 min |
| Setup validation | Verify Azure, GitHub, Copilot access for all participants | 30 min |
| Diagnosis | Run quick diagnosis questions + diagnostic task | 20 min |
| Path assignment | Classify participants, communicate paths | 10 min |
| Baseline alignment | Walkthrough of a sample repository for baseline participants | 30 min |
| Wrap-up | Confirm readiness for Day 2, capture blockers | 15 min |

### Coach Checklist

- [ ] Event Azure tenant is accessible and participants can log in
- [ ] GitHub organization is accessible and participants can see assigned repositories
- [ ] Copilot is active for all participants (check license and extension)
- [ ] Diagnostic questions are ready (see [Participant Diagnosis](03-participant-diagnosis.md))
- [ ] Participant Diagnosis Sheets are available (see [template](../templates/participant-diagnosis-sheet.md))
- [ ] Fallback activities are prepared for blocked participants
- [ ] Both coaches have agreed on how to split the room (by table, by skill level, or rotating)

### Participant Output

| Output | Description |
|---|---|
| Completed diagnosis | Each participant has been classified (beginner / intermediate / advanced / blocked) |
| Working environment | Azure, GitHub, and Copilot access confirmed — or fallback path assigned |
| Path assignment | Each participant knows whether they are on baseline or advanced path |

### If/Else Branches

```
IF participant's access works on first try
  → Proceed to diagnosis
ELSE IF access partially works (e.g., Azure but not Copilot)
  → Troubleshoot the failing component (5-minute rule)
  → If unresolved, escalate and assign fallback
ELSE IF access completely fails
  → Escalate immediately
  → Assign to pairing or demo mode
  → Do not wait — begin diagnosis verbally
```

### Common Risks

| Risk | Mitigation |
|---|---|
| Azure tenant not provisioned for some participants | Have event tech team on standby. Use fallback paths. |
| Copilot license not active | Check org licensing. Escalate to admin. Switch to manual coding in the meantime. |
| Participants arrive late and miss setup | Assign a catch-up buddy. Run compressed setup + diagnosis. |
| Network/firewall blocks access | Identify alternative networks. Have mobile hotspot as backup. |

### Definition of Done

Day 1 is complete when:
- Every participant has been diagnosed and classified
- Every participant has confirmed access to tools or has been placed on a fallback path
- Coaches have a clear picture of the room's skill distribution
- All blockers are logged and escalated if necessary

---

## Day 2: Living Documentation

### Purpose
Participants learn to build and structure documentation that serves both humans and AI. Baseline participants create foundational documentation. Advanced participants evaluate and enhance existing documentation and may begin code/infrastructure auditing.

### Schedule Overview

| Block | Activity | Duration |
|---|---|---|
| Quick check | Verify Day 1 issues are resolved; re-diagnose if needed | 10 min |
| Introduction | Living documentation concepts; why it matters for AI | 15 min |
| Baseline activity | Repository understanding → documentation creation | 60 min |
| Advanced activity | Documentation evaluation → ADRs, Copilot context, audit prep | 60 min |
| Output capture | Participants finalize and submit their documentation outputs | 20 min |
| Wrap-up | Review outputs, preview Day 3 | 15 min |

### Coach Checklist

- [ ] Day 1 blockers resolved or fallbacks confirmed
- [ ] Assigned repositories are accessible
- [ ] Living documentation session guide reviewed (see [Living Documentation Session](05-living-documentation-session.md))
- [ ] Output templates available (see [Output Templates](11-output-templates.md))
- [ ] Quick check: has any participant's classification changed since Day 1?

### Participant Output

| Level | Output |
|---|---|
| Baseline | Improved or created README, setup guide, or architecture overview |
| Advanced | Architecture notes, ADRs, Copilot instructions, and/or early audit findings |

### If/Else Branches

```
IF participant does not understand the codebase
  → Start with repository mapping (guided exploration)

ELSE IF participant understands the codebase but documentation is weak
  → Create living documentation (README, setup, architecture)

ELSE IF documentation already exists
  → Evaluate accuracy, currency, and AI-usability

ELSE IF participant is advanced and documentation is solid
  → Move into code/infrastructure audit preparation
```

### Common Risks

| Risk | Mitigation |
|---|---|
| Participant writes surface-level docs | Ask: "Would a new developer be able to set up and run this project using only your documentation?" |
| Participant skips evidence and writes opinion | Ask: "Can you point to the code that supports this statement?" |
| Advanced participant is bored | Move them to audit prep. Let them create Copilot instructions or ADRs. |
| Repository is too complex for beginners | Narrow scope to one module or one service. |

### Definition of Done

Day 2 is complete when:
- Every participant has produced at least one documentation artifact
- Documentation artifacts are specific and evidence-based (not generic)
- Advanced participants have begun audit preparation or created enhanced documentation
- Outputs are captured using the [Session Output Template](../templates/session-output-template.md)

---

## Day 3: Code and Infrastructure Audit

### Purpose
Participants inspect codebases and infrastructure configurations to identify real risks. Baseline participants focus on finding one risk with evidence. Advanced participants conduct structured audits across multiple categories.

### Schedule Overview

| Block | Activity | Duration |
|---|---|---|
| Quick check | Re-diagnose if needed; review Day 2 outputs | 10 min |
| Introduction | Audit categories; what makes a finding valid | 15 min |
| Baseline activity | Guided codebase inspection → one audit finding | 60 min |
| Advanced activity | Multi-category audit → structured audit report | 60 min |
| Output capture | Finalize findings using audit templates | 20 min |
| Wrap-up | Review findings, preview Day 4 ticket triage | 15 min |

### Coach Checklist

- [ ] Day 2 documentation outputs reviewed (quick scan)
- [ ] Audit categories reference ready (see [Code/Infrastructure Audit Session](06-code-infrastructure-audit-session.md))
- [ ] Audit Finding Template available (see [template](../templates/audit-finding-template.md))
- [ ] Risk Register Template available (see [template](../templates/risk-register-template.md))
- [ ] Re-check: should any baseline participants be upgraded to advanced?

### Participant Output

| Level | Output |
|---|---|
| Baseline | One audit finding with evidence, documented using the [Audit Finding Template](../templates/audit-finding-template.md) |
| Advanced | Audit report with multiple findings + [Risk Register](../templates/risk-register-template.md) |

### If/Else Branches

```
IF participant cannot explain the application
  → Go back to repository understanding (borrow from Day 2)

ELSE IF participant can explain the app but cannot find risks
  → Use guided risk categories (security, reliability, etc.)

ELSE IF participant finds generic issues without evidence
  → Ask for specific code or configuration evidence

ELSE IF participant finds real, evidence-backed risks
  → Move to ticket creation (preview Day 4)
```

### Common Risks

| Risk | Mitigation |
|---|---|
| Participant only finds "add more tests" | Push for specifics: "Which function lacks test coverage and why does that matter?" |
| Participant trusts Copilot's audit without verification | Apply Principle 4: "Copilot gave us a hypothesis. Where is the evidence in the code?" |
| Participant overwhelmed by the codebase | Narrow scope: pick one service, one module, or one configuration file. |
| Findings are too many and shallow | Prioritize: "Pick your top 3 by severity. Why are these the most important?" |

### Definition of Done

Day 3 is complete when:
- Every baseline participant has at least one evidence-backed finding
- Advanced participants have a structured audit report or risk register
- Findings reference specific code, configuration, or infrastructure
- Outputs are captured using templates

---

## Day 4: Ticket Triage, Backlog Creation, and Wrap-Up

### Purpose
Convert findings into actionable GitHub issues. Prioritize the backlog. Finalize all outputs. Wrap up the event with clear next steps.

### Schedule Overview

| Block | Activity | Duration |
|---|---|---|
| Quick check | Review Day 3 findings; confirm readiness for ticket creation | 10 min |
| Introduction | What makes a good ticket; prioritization frameworks | 15 min |
| Baseline activity | Convert one finding into a GitHub issue | 45 min |
| Advanced activity | Create prioritized backlog; assign severity, effort, confidence | 45 min |
| Final output capture | Finalize all outputs; ensure templates are complete | 20 min |
| Wrap-up | Event summary; next steps; feedback | 25 min |

### Coach Checklist

- [ ] Day 3 findings are ready to be converted into tickets
- [ ] GitHub Issue Template available (see [template](../templates/github-issue-template.md))
- [ ] Ticket Triage session guide reviewed (see [Ticket Triage Session](07-ticket-triage-session.md))
- [ ] Prioritization matrix ready (see session guide)
- [ ] Plan for final output capture and wrap-up

### Participant Output

| Level | Output |
|---|---|
| Baseline | One GitHub issue with problem, evidence, impact, and acceptance criteria |
| Advanced | Prioritized issue backlog + PR implementation plan or hardening recommendations |

### If/Else Branches

```
IF findings from Day 3 are vague
  → Refine the findings first (do not create vague tickets)

ELSE IF findings are actionable
  → Create GitHub issues using the template

ELSE IF there are too many findings
  → Prioritize using severity/effort matrix

ELSE IF the participant is advanced and has a clean backlog
  → Create a PR implementation plan or hardening recommendations document
```

### Common Risks

| Risk | Mitigation |
|---|---|
| Participant creates vague tickets | Review together: "Would an engineer who hasn't seen this code know what to do?" |
| Participant creates too many low-quality tickets | Focus on top 3. Quality over quantity. |
| Time runs short before outputs are captured | Start output capture early. Use the last 30 minutes for finalization only. |
| Participant did not produce findings on Day 3 | Use the ticket writing session as a chance to find one risk and convert it directly. |

### Definition of Done

Day 4 — and the event — is complete when:
- Every participant has produced at least the baseline outputs (documented understanding, one risk, one issue, one next step)
- Advanced participants have produced structured audit reports, risk registers, and/or prioritized backlogs
- All outputs are evidence-based and use the provided templates
- Participants have a clear understanding of recommended next steps
- Coaches have captured session outputs using the [Session Output Template](../templates/session-output-template.md)

---

## Cross-Day Reference

| Day | Theme | Key Document | Primary Output |
|---|---|---|---|
| 1 | Orientation & Diagnosis | [Participant Diagnosis](03-participant-diagnosis.md) | Participant classification |
| 2 | Living Documentation | [Living Docs Session](05-living-documentation-session.md) | Documentation artifact |
| 3 | Code/Infrastructure Audit | [Audit Session](06-code-infrastructure-audit-session.md) | Audit finding(s) |
| 4 | Ticket Triage & Wrap-Up | [Triage Session](07-ticket-triage-session.md) | GitHub issue(s) |
