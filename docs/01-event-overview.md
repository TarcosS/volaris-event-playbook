# Event Overview

> Context and scope for the 4-day Volaris Group developer coaching event.

---

## Event Purpose

This is a 4-day hands-on developer coaching event organized under Volaris Group. The event brings together approximately 200 developers from across the organization to build practical skills in modern development practices using Azure, GitHub, and GitHub Copilot.

The event is **not** a lecture series. It is a coached, hands-on experience where participants work with real or representative codebases and infrastructure. Coaches guide participants through structured activities, help them diagnose problems, and ensure they produce concrete outputs.

## Audience

| Attribute | Detail |
|---|---|
| **Size** | ~200 participants |
| **Skill distribution** | Unknown in advance — expected mix of beginner, intermediate, and advanced |
| **Background** | Developers, DevOps engineers, team leads, and technical staff from Volaris Group business units |
| **Common ground** | All participants have some development experience, but depth varies significantly |

### Key Assumption

**We do not know in advance how skilled the participants are.** The playbook is designed around this uncertainty. Every session begins with a diagnostic step, and every activity has baseline and advanced paths.

## Coach Responsibilities

Two coaches are responsible for the entire event. Their duties include:

1. **Diagnose participant skill levels** at the start of each session using structured questions and diagnostic tasks
2. **Select the right coaching path** (baseline or advanced) for each participant or group
3. **Guide hands-on activities** during each session — living documentation, code/infrastructure audit, and ticket triage
4. **Unblock environment and tooling issues** — Azure access, GitHub configuration, Copilot licensing, local setup
5. **Ensure evidence-based reasoning** — participants must support findings with code, configuration, or infrastructure evidence
6. **Capture concrete outputs** — every session ends with a tangible artifact (document, finding, ticket, recommendation)
7. **Escalate issues** that cannot be resolved at the coach level to the event technical team or organization admins

## Primary Technologies

| Technology | Role in the Event |
|---|---|
| **Azure** | Cloud platform for infrastructure and deployment. Participants inspect, audit, and reason about Azure resources and configurations. |
| **GitHub** | Source control, collaboration, and issue tracking. Participants work within GitHub repositories, create issues, and use GitHub features. |
| **GitHub Copilot** | AI-assisted coding and reasoning. Participants use Copilot to explore codebases, generate documentation, identify risks, and draft tickets. Coaches guide participants to treat Copilot as a reasoning assistant, not an authority. |

## Main Session Themes

The event is organized around three core session themes, delivered across four days:

### 1. Living Documentation (Day 2)
Building and structuring knowledge for both human and AI success. Participants learn to create documentation that serves developers, onboarding processes, and AI tools like Copilot.

### 2. Code and Infrastructure Audit (Day 3)
Finding vulnerabilities, risks, and improvement areas in a brownfield context. Participants inspect real codebases and infrastructure configurations to identify security, reliability, maintainability, and deployment risks.

### 3. Ticket Triage (Day 4)
Turning findings into actionable work. Participants learn to convert audit findings into well-structured GitHub issues with evidence, acceptance criteria, and prioritization.

## Expected Outputs

By the end of the 4-day event, each participant or group should produce tangible artifacts that demonstrate learning and provide real value.

### Baseline Outputs (All Participants)

Every participant, regardless of skill level, should leave with at least:

| Output | Description |
|---|---|
| **Documented system understanding** | A README, architecture overview, or setup guide for their assigned codebase |
| **One identified risk or improvement** | A specific risk or improvement area backed by evidence from the code or infrastructure |
| **One actionable GitHub issue** | A well-structured issue with problem statement, evidence, impact, and acceptance criteria |
| **One recommended next step** | A clear recommendation for what should happen next with the finding |

### Advanced Outputs (Advanced Participants)

Participants on the advanced path should additionally produce:

| Output | Description |
|---|---|
| **Audit report** | A structured report covering multiple risk categories (security, reliability, maintainability, etc.) |
| **Risk register** | A register with risk descriptions, severity, likelihood, impact, and recommended actions |
| **Prioritized issue backlog** | Multiple GitHub issues organized by priority using a severity/effort matrix |
| **PR implementation plan** | A plan for addressing findings through pull requests, including scope and sequencing |
| **Hardening recommendations** | Infrastructure or security hardening recommendations with evidence and implementation guidance |

## Event Success Criteria

The event is successful when:

- [ ] Every participant has been diagnosed and placed on an appropriate path
- [ ] Every participant has produced at least the baseline outputs
- [ ] Advanced participants have produced additional structured artifacts
- [ ] All outputs are evidence-backed (no vague or unsupported findings)
- [ ] Environment and access blockers were resolved or worked around without losing participant engagement
- [ ] Coaches used the playbook to make consistent, fast decisions across all sessions
