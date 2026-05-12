---
title: "Code & Infrastructure Audit"
layout: default
parent: "Sessions"
nav_order: 2
---

> Session guide for Day 3 — finding vulnerabilities, risks, and improvement areas in a brownfield context.

---

## Session Purpose

Participants inspect real codebases and infrastructure configurations to identify risks across multiple categories. The goal is to produce evidence-backed findings that can be converted into actionable tickets on Day 4.

## Prerequisites

- Participant has completed the Living Documentation session (Day 2)
- Participant has a basic understanding of the assigned codebase
- Participant has access to repository, GitHub, and Copilot
- Audit Finding Template is available (see [template](../templates/audit-finding-template.md))
- Risk Register Template is available for advanced participants (see [template](../templates/risk-register-template.md))

---

## Audit Categories

Use these categories to guide the audit. Baseline participants focus on 1–2 categories. Advanced participants cover as many as time allows.

| Category | What to Look For |
|---|---|
| **Security** | Hardcoded secrets, weak authentication, missing input validation, overly permissive permissions, exposed endpoints, insecure dependencies |
| **Reliability** | Missing error handling, no retry logic, single points of failure, missing health checks, no graceful degradation |
| **Maintainability** | Large/complex functions, no separation of concerns, missing abstractions, tight coupling, poor naming, dead code |
| **Cloud Readiness** | Hardcoded configuration, missing environment variable support, no containerization, stateful design assumptions, missing infrastructure as code |
| **Observability** | No logging, no metrics, no tracing, no alerting, insufficient log levels, missing correlation IDs |
| **Cost** | Over-provisioned resources, no autoscaling, no resource cleanup, expensive service tiers for non-production, missing budget alerts |
| **Developer Experience** | Missing README, no setup automation, unclear contribution guidelines, no local development setup, missing IDE configuration |
| **Testing** | No unit tests, no integration tests, low coverage on critical paths, no test automation, brittle tests |
| **CI/CD** | No pipeline, manual deployments, no quality gates, missing security scanning, no environment promotion strategy |
| **Dependency Risk** | Outdated dependencies, known vulnerabilities, unmaintained libraries, license issues, excessive dependency count |

---

## Baseline Path

**For:** Beginner and intermediate participants  
**Goal:** Find one real risk with evidence and document it as a finding  
**Time:** ~60 minutes of guided work

### Steps

#### Step 1: Confirm Repository Understanding (10 min)

Before auditing, verify the participant can explain:
- What the application does
- Where the main entry point is
- What the key dependencies are

**If they cannot:** Go back to repository understanding. Use 10 minutes from the Living Documentation session approach. Do not proceed to auditing without understanding.

#### Step 2: Select Audit Categories (5 min)

For baseline participants, start with the most accessible categories:

1. **Security** — look for hardcoded secrets, missing validation
2. **Testing** — check for test coverage on critical paths
3. **Developer Experience** — evaluate README, setup process, contribution docs

Ask the participant to pick one category that they feel most confident about.

#### Step 3: Guided Audit (30 min)

Walk the participant through a structured inspection:

1. **Use Copilot to scan** — ask Copilot to review the selected area
2. **Verify Copilot's output** — check the actual code for each finding Copilot suggests
3. **Evaluate severity** — is this a real risk or a minor improvement?
4. **Gather evidence** — note the file, line, and what the code does (or fails to do)
5. **Document the finding** — use the [Audit Finding Template](../templates/audit-finding-template.md)

**Coach check at 15 min:** Has the participant found anything? If not, suggest a specific file or area to inspect.

#### Step 4: Document the Finding (15 min)

Using the [Audit Finding Template](../templates/audit-finding-template.md), the participant documents:

- What the risk is
- Where the evidence is (file path, line number, or configuration key)
- Why it matters (impact)
- What should be done about it (recommended fix)

---

## Advanced Path

**For:** Advanced participants  
**Goal:** Conduct a structured audit across multiple categories and produce an audit report with risk register  
**Time:** ~60 minutes of self-directed work with check-ins

### Steps

#### Step 1: Multi-Category Audit (40 min)

Advanced participants audit the codebase across multiple categories. Suggest they allocate time per category:

| Category | Focus Area | Time |
|---|---|---|
| **Security** | Secrets, authentication, authorization, input validation, dependency vulnerabilities | 10 min |
| **Infrastructure** | CI/CD pipeline, deployment configuration, IaC review, environment management | 10 min |
| **Reliability** | Error handling, retry logic, health checks, failure modes | 10 min |
| **Observability** | Logging, metrics, tracing, alerting | 5 min |
| **Cost/Scalability** | Resource sizing, autoscaling, cleanup, optimization opportunities | 5 min |

#### Step 2: Security and Infrastructure Deep Dive

For participants with infrastructure experience, guide them through:

- **CI/CD review:** Are there quality gates? Security scanning? Is the pipeline secure?
- **Secrets/config review:** Are secrets in environment variables? Are they rotated? Is there a secrets manager?
- **Permissions and identity review:** Principle of least privilege? Service accounts? Role assignments?
- **Observability review:** Are there actionable alerts? Is logging structured? Can you trace a request?
- **Cost/scalability review:** Right-sized resources? Autoscaling configured? Dev/test parity?
- **Deployment hardening:** Blue/green or canary? Rollback strategy? Health checks in deployment?

#### Step 3: Create Audit Report and Risk Register (20 min)

Using the templates:
- Document all findings in [Audit Finding Template](../templates/audit-finding-template.md) format
- Compile into a [Risk Register](../templates/risk-register-template.md) with severity, likelihood, and recommended actions
- Prioritize findings for Day 4 ticket triage

---

## Decision Tree

```
START: Participant begins audit session
  │
  ├─ Can the participant explain the application?
  │   ├─ NO → Go back to repository understanding
  │   │         (use Living Documentation approach for 10 min)
  │   │         └─ Then return to audit
  │   │
  │   └─ YES → Can they find risks?
  │       ├─ NO → Use guided risk categories
  │       │       → Pick one category (security, testing, or dev experience)
  │       │       → Walk through specific files and configurations
  │       │       → Help them see what a risk looks like
  │       │
  │       └─ YES → Are findings specific and evidence-backed?
  │           ├─ NO (generic issues only)
  │           │   → Ask for code or configuration evidence
  │           │   → "Can you point to the specific line or config?"
  │           │   → Help them refine from generic → specific
  │           │
  │           └─ YES (real, evidence-backed risks)
  │               → Document using Audit Finding Template
  │               → If multiple findings: create Risk Register
  │               → If time allows: begin ticket creation (preview Day 4)
```

---

## Copilot Prompts for This Session

### General Audit

```
Audit this repository for security, maintainability, and deployment risks.
Prioritize findings by severity and confidence. For each finding, reference
the specific file and explain why it is a risk.
```

```
Review this codebase and identify the top 5 risks a new team should address
before deploying to production. Include evidence for each.
```

### Security

```
Scan this repository for security risks: hardcoded secrets, missing input
validation, insecure dependencies, overly permissive configurations, and
exposed endpoints. Reference specific files and lines.
```

```
Review the authentication and authorization implementation. Identify any
weaknesses or missing security controls.
```

### Infrastructure

```
Review this infrastructure configuration and identify risks related to
permissions, networking, secrets management, and scalability.
```

```
Analyze the CI/CD pipeline for security and reliability risks. Are there
quality gates? Is the pipeline vulnerable to supply chain attacks?
```

### Observability

```
Identify missing observability signals in this application. Where should
logging, metrics, tracing, or alerting be added? What events are not
currently captured?
```

### Error Handling

```
Find areas where error handling or retry behavior may be weak. Identify
functions that could fail silently or propagate errors incorrectly.
```

> **Reminder:** All Copilot output must be verified against the actual code. See [Coaching Principle 4](02-coaching-principles.md#principle-4-use-copilot-as-a-reasoning-assistant-not-an-authority).

---

## Output Template

Use the [Audit Finding Template](../templates/audit-finding-template.md) for individual findings and the [Risk Register Template](../templates/risk-register-template.md) for a consolidated view. Use the [Session Output Template](../templates/session-output-template.md) to capture session-level results.

### Example Audit Finding

| Field | Value |
|---|---|
| **Title** | Database connection string hardcoded in application config |
| **Summary** | The production database connection string is stored in plaintext in `appsettings.json` and committed to the repository. |
| **Evidence** | `src/appsettings.json`, line 12: `"ConnectionString": "Server=prod-db.example.com;Password=..."` |
| **Category** | Security |
| **Severity** | High |
| **Confidence** | High — directly observed in committed code |
| **Impact** | Credential exposure. Anyone with repository access can see production database credentials. Credential rotation requires code changes and redeployment. |
| **Recommended Fix** | Move connection string to Azure Key Vault or environment variables. Remove from repository history using `git filter-branch` or BFG Repo-Cleaner. Add secret scanning to CI pipeline. |
| **Acceptance Criteria** | Connection string is not present in any committed file. Application reads credentials from Key Vault or environment variables at runtime. Secret scanning blocks commits containing credential patterns. |

---

## Common Pitfalls

| Pitfall | How to Address |
|---|---|
| Participant only finds "add more tests" | "Which specific function lacks coverage? What could go wrong if it fails?" |
| Participant trusts Copilot's audit without checking | "Copilot identified a risk — let's verify it exists in the code." |
| Participant is overwhelmed by the size of the codebase | "Pick one service or one module. We're looking for depth, not breadth." |
| Findings are too many and too shallow | "Pick your top 3 by severity. Let's make those excellent rather than documenting everything." |
| Participant conflates "improvement" with "risk" | "An improvement is nice to have. A risk could cause an incident. Which is this?" |
