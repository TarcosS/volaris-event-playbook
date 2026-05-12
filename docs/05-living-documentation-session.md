---
title: "Living Documentation"
layout: default
parent: "Sessions"
nav_order: 1
---

> Session guide for Day 2 — building and structuring knowledge for human and AI success.

---

## Session Purpose

Participants learn to create documentation that serves three audiences: human developers, onboarding processes, and AI tools like GitHub Copilot. The goal is to produce documentation that makes the codebase understandable, navigable, and auditable.

## Prerequisites

- Participant has been diagnosed (see [Participant Diagnosis](03-participant-diagnosis.md))
- Participant has access to assigned repository, GitHub, and Copilot
- If access is blocked, participant is on a fallback path (see [Troubleshooting Guide](09-troubleshooting-guide.md))

---

## Baseline Path

**For:** Beginner and intermediate participants  
**Goal:** Understand the repository and create or improve foundational documentation  
**Time:** ~60 minutes of guided work

### Steps

#### Step 1: Understand the Repository (20 min)

Guide the participant through a structured exploration of the codebase:

1. **Read the existing README** (if one exists) — is it accurate? Is it complete?
2. **Identify the project structure** — what are the main directories and their purpose?
3. **Find the main entry point** — where does the application start?
4. **Identify key dependencies** — what frameworks, libraries, and services does it use?
5. **Check for configuration** — environment variables, config files, secrets references

**Coach check:** Ask the participant to explain the project in 2–3 sentences. If they cannot, they need more guided exploration before moving to documentation.

#### Step 2: Identify Documentation Gaps (10 min)

Ask the participant to list what is missing from the documentation:

- [ ] How to set up and run the project locally
- [ ] Architecture overview
- [ ] Key dependencies and their purpose
- [ ] Environment variables and configuration
- [ ] Deployment process
- [ ] Known limitations or technical debt
- [ ] Next steps or roadmap

#### Step 3: Create or Improve Documentation (30 min)

Based on the gaps identified, the participant writes documentation. Focus on one or two sections — depth over breadth.

**Priority order for documentation creation:**
1. Setup and run instructions (highest value for onboarding)
2. Architecture overview (highest value for understanding)
3. Environment variables and configuration
4. Deployment notes
5. Known limitations and next steps

**Output:** A Markdown document or updated README committed to the repository (or saved as a draft).

---

## Advanced Path

**For:** Advanced participants  
**Goal:** Evaluate documentation quality for humans and AI, create advanced artifacts, and prepare for code/infrastructure auditing  
**Time:** ~60 minutes of self-directed work with periodic check-ins

### Steps

#### Step 1: Evaluate Existing Documentation (15 min)

Assess the documentation against these criteria:

| Criterion | Question |
|---|---|
| **Accuracy** | Does the documentation match the current code? |
| **Completeness** | Are all critical areas covered (setup, architecture, deployment, config)? |
| **Currency** | When was it last updated? Are there stale references? |
| **AI-usability** | Could an AI tool like Copilot use this documentation to answer questions about the project accurately? |
| **Onboarding value** | Could a new developer set up and understand the project using only this documentation? |

#### Step 2: Create Advanced Artifacts (30 min)

Choose one or more based on what the repository needs most:

**Architecture Decision Records (ADRs)**
- Document key architectural decisions with context, decision, and consequences
- Format: `ADR-001: [Decision Title]` with Status, Context, Decision, Consequences sections

**Copilot Context / Instructions**
- Create `.github/copilot-instructions.md` or equivalent
- Document project conventions, naming patterns, architecture rules, and domain-specific terminology
- Goal: make Copilot's suggestions more accurate for this specific project

**Architecture Overview**
- Create a high-level system diagram (text-based: Mermaid, ASCII, or structured Markdown)
- Document service boundaries, data flows, and integration points

#### Step 3: Transition to Audit Preparation (15 min)

If documentation work is complete, begin preliminary code/infrastructure audit:

- Scan the codebase for obvious risks (hardcoded secrets, missing error handling, no tests)
- Note areas that need deeper investigation on Day 3
- Document initial observations in the [Audit Finding Template](../templates/audit-finding-template.md)

---

## Decision Tree

```
START: Participant begins living documentation session
  │
  ├─ Does the participant understand the codebase?
  │   ├─ NO → Step 1: Repository mapping (guided exploration)
  │   │         └─ After mapping → Step 2: Identify documentation gaps
  │   │
  │   └─ YES → Is existing documentation weak or missing?
  │       ├─ YES → Step 3: Create living documentation
  │       │
  │       └─ NO → Is documentation accurate, current, and AI-usable?
  │           ├─ NO → Advanced: Evaluate and enhance documentation
  │           │
  │           └─ YES → Is the participant advanced?
  │               ├─ YES → Advanced: Create ADRs, Copilot context,
  │               │         or begin audit preparation
  │               │
  │               └─ NO → Deepen existing documentation
  │                        (add deployment notes, known limitations, etc.)
```

---

## Copilot Prompts for This Session

Participants can use these prompts with GitHub Copilot to accelerate their work. Coaches should model how to use these and emphasize verification of results.

### Repository Understanding

```
Explain this repository structure in simple terms. What is the purpose of each top-level directory?
```

```
Identify the main entry point of this application and summarize what it does.
```

```
List the key dependencies in this project and explain what each one is used for.
```

### Documentation Creation

```
Create a README section explaining how to set up and run this project locally,
including prerequisites, environment variables, and step-by-step instructions.
```

```
Identify missing documentation that would help a new developer onboard to this project.
Prioritize by importance.
```

```
Create an architecture overview from the repository structure. Include the main components,
how they interact, and what technologies they use.
```

### Advanced Documentation

```
Review the existing README for accuracy. Identify any statements that do not match the
current code and suggest corrections.
```

```
Create a Copilot instructions file (.github/copilot-instructions.md) for this project.
Include coding conventions, architectural patterns, and domain-specific terminology.
```

```
Draft an Architecture Decision Record (ADR) for [specific decision observed in the code].
Include context, decision, and consequences.
```

> **Reminder:** All Copilot output must be verified against the actual code. See [Coaching Principle 4](02-coaching-principles.md#principle-4-use-copilot-as-a-reasoning-assistant-not-an-authority).

---

## Output Template

Use the [Session Output Template](../templates/session-output-template.md) to capture session results.

### Example Baseline Output

| Field | Value |
|---|---|
| **Session** | Living Documentation |
| **Starting level** | Beginner |
| **Path** | Baseline |
| **Activities completed** | Repository exploration, README creation |
| **Output created** | Updated README with setup instructions, architecture overview, and environment variables |
| **Blockers** | None |
| **Follow-up needed** | Deployment section still incomplete — continue on Day 3 if time allows |

### Example Advanced Output

| Field | Value |
|---|---|
| **Session** | Living Documentation |
| **Starting level** | Advanced |
| **Path** | Advanced |
| **Activities completed** | Documentation evaluation, ADR creation, Copilot instructions, preliminary audit |
| **Output created** | ADR-001 (database choice), .github/copilot-instructions.md, 3 preliminary audit notes |
| **Blockers** | None |
| **Follow-up needed** | Audit notes to be expanded on Day 3 |

---

## Common Pitfalls

| Pitfall | How to Address |
|---|---|
| Participant copies Copilot output verbatim without checking | "Let's verify this against the actual code. Does the setup process really work this way?" |
| Documentation is too generic ("this is a web app") | "What specifically does it do? What framework? What data does it handle?" |
| Participant focuses on formatting over content | "Content first, formatting later. What would a new developer need to know?" |
| Advanced participant finds documentation "good enough" | Challenge: "Could an AI assistant give accurate answers about this project using only this documentation?" |
