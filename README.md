# Volaris Event Playbook

> A field-ready coaching playbook for a 4-day developer coaching event under Volaris Group.  
> Built for two developer coaches guiding ~200 participants through Azure, GitHub, and GitHub Copilot.

---

## What This Playbook Is

This repository is an operational guide for developer coaches attending a 4-day hands-on coaching event. It provides decision trees, diagnostic flows, session guides, troubleshooting paths, and ready-to-use scripts so coaches can make fast, evidence-based decisions during live sessions.

This is **not** a training curriculum. It is a coaching playbook — designed to help coaches assess participants, select the right guidance path, and ensure every participant leaves with concrete, evidence-backed outputs.

## Who It Is For

- **Primary audience:** The two developer coaches attending the event
- **Secondary audience:** Event organizers and technical leads who want visibility into the coaching approach

## Event Context

| Detail | Value |
|---|---|
| **Organization** | Volaris Group |
| **Format** | 4-day hands-on developer coaching event |
| **Participants** | ~200 developers (mixed skill levels) |
| **Technologies** | Azure, GitHub, GitHub Copilot |
| **Coach count** | 2 |
| **Session themes** | Living documentation, code/infrastructure audit, ticket triage |

Participants will work with real or representative codebases and infrastructure. Coaches are responsible for diagnosing skill levels, unblocking environment issues, guiding hands-on activities, and ensuring participants produce meaningful outputs.

## How to Use This Playbook

1. **Before the event:** Read the [Event Overview](docs/01-event-overview.md), [Coaching Principles](docs/02-coaching-principles.md), and [Day-by-Day Flow](docs/04-day-by-day-flow.md).
2. **At the start of each day:** Review the day's section in [Day-by-Day Flow](docs/04-day-by-day-flow.md) and the relevant session guide.
3. **During sessions:** Use the [If/Else Playbook](docs/08-if-else-playbook.md) for real-time decisions and the [Coach Scripts](docs/10-coach-scripts.md) for ready-made phrases.
4. **When problems arise:** Use the [Troubleshooting Guide](docs/09-troubleshooting-guide.md) and [Escalation Matrix](docs/12-escalation-matrix.md).
5. **For quick lookups:** Keep the [Quick Reference](docs/13-quick-reference.md) open at all times.

## Recommended Workflow for Coaches

```
┌─────────────────────────────────────────────────────┐
│              COACHING LOOP (per participant)         │
│                                                     │
│   1. Diagnose the participant                       │
│   2. Select the right path (baseline / advanced)    │
│   3. Guide the activity                             │
│   4. Validate with evidence                         │
│   5. Capture a concrete output                      │
│                                                     │
│   Repeat for each session. Escalate if blocked.     │
└─────────────────────────────────────────────────────┘
```

### Core Decision Rule

This rule applies throughout the entire event:

> **IF** the participant can explain the system, use Copilot with evidence, and reason about code/infrastructure risks,  
> **THEN** move them to the **advanced path**.
>
> **ELSE** keep them in the **guided baseline path**.

## Repository Structure

```
volaris-event-playbook/
├── README.md                          ← You are here
├── docs/
│   ├── 01-event-overview.md           ← Event purpose, audience, technologies
│   ├── 02-coaching-principles.md      ← Core coaching principles
│   ├── 03-participant-diagnosis.md    ← Diagnostic flow and classification
│   ├── 04-day-by-day-flow.md          ← 4-day schedule with checklists
│   ├── 05-living-documentation-session.md   ← Session guide: living docs
│   ├── 06-code-infrastructure-audit-session.md  ← Session guide: audit
│   ├── 07-ticket-triage-session.md    ← Session guide: ticket triage
│   ├── 08-if-else-playbook.md         ← Core operational decision playbook
│   ├── 09-troubleshooting-guide.md    ← Common blockers and fixes
│   ├── 10-coach-scripts.md            ← Ready-to-use coaching phrases
│   ├── 11-output-templates.md         ← Collected output templates
│   ├── 12-escalation-matrix.md        ← When and how to escalate
│   └── 13-quick-reference.md          ← One-page live reference card
└── templates/
    ├── audit-finding-template.md      ← Template for audit findings
    ├── github-issue-template.md       ← Template for GitHub issues
    ├── session-output-template.md     ← Template for session outputs
    ├── participant-diagnosis-sheet.md ← Template for participant diagnosis
    └── risk-register-template.md      ← Template for risk registers
```

## Quick Start for Coaches

**5 minutes before the event starts:**

1. Open this repo on your laptop or tablet
2. Open the [Quick Reference](docs/13-quick-reference.md) in a pinned tab
3. Have the [If/Else Playbook](docs/08-if-else-playbook.md) ready for fast lookups
4. Print or bookmark the [Participant Diagnosis](docs/03-participant-diagnosis.md) sheet
5. Confirm you have access to the event's Azure tenant, GitHub organization, and Copilot licenses

**First 15 minutes of each session:**

1. Run the diagnosis flow from [Participant Diagnosis](docs/03-participant-diagnosis.md)
2. Classify participants as beginner / intermediate / advanced / blocked
3. Assign paths and begin guided activities

## Core Coaching Model

The playbook is built on five pillars:

| Pillar | Description |
|---|---|
| **Diagnose first** | Never assume participant level. Always ask, observe, and classify. |
| **Evidence over opinion** | Every finding, ticket, and recommendation must be backed by evidence from the code, configuration, or infrastructure. |
| **Concrete outputs** | Every session must produce something tangible: a document, a finding, a ticket, or a recommendation. |
| **Adaptive paths** | Baseline and advanced paths exist for every session. Coaches select the path based on diagnosis. |
| **Escalate early** | Environment and access issues must be escalated immediately. Do not let blockers consume session time. |

## Final Expected Outputs

By the end of the 4-day event, each participant (or group) should have produced:

### Baseline Outputs
- One documented understanding of a system (README, architecture notes, or setup guide)
- One identified risk or improvement area with evidence
- One actionable GitHub issue with acceptance criteria
- One recommended next step

### Advanced Outputs
- Audit report covering multiple risk categories
- Risk register with severity, likelihood, and recommended actions
- Prioritized issue backlog
- PR implementation plan or infrastructure hardening recommendations

---

## Quick Links

| Document | Purpose |
|---|---|
| [Event Overview](docs/01-event-overview.md) | What this event is about |
| [Coaching Principles](docs/02-coaching-principles.md) | How we coach |
| [Participant Diagnosis](docs/03-participant-diagnosis.md) | How to assess participants |
| [Day-by-Day Flow](docs/04-day-by-day-flow.md) | What happens each day |
| [Living Documentation Session](docs/05-living-documentation-session.md) | Session guide: documentation |
| [Code/Infrastructure Audit](docs/06-code-infrastructure-audit-session.md) | Session guide: audit |
| [Ticket Triage Session](docs/07-ticket-triage-session.md) | Session guide: triage |
| [If/Else Playbook](docs/08-if-else-playbook.md) | Real-time decision guide |
| [Troubleshooting Guide](docs/09-troubleshooting-guide.md) | Fix common blockers |
| [Coach Scripts](docs/10-coach-scripts.md) | What to say |
| [Output Templates](docs/11-output-templates.md) | Templates for outputs |
| [Escalation Matrix](docs/12-escalation-matrix.md) | When to escalate |
| [Quick Reference](docs/13-quick-reference.md) | One-page cheat sheet |
| [Audit Finding Template](templates/audit-finding-template.md) | Template for documenting findings |
| [GitHub Issue Template](templates/github-issue-template.md) | Template for creating issues |
| [Session Output Template](templates/session-output-template.md) | Template for session records |
| [Participant Diagnosis Sheet](templates/participant-diagnosis-sheet.md) | Template for participant assessment |
| [Risk Register Template](templates/risk-register-template.md) | Template for risk tracking |
