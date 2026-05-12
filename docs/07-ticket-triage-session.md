---
title: "Ticket Triage"
layout: default
parent: "Sessions"
nav_order: 3
---

> Session guide for Day 4 — converting audit findings into actionable, prioritized GitHub issues.

---

## Session Purpose

Participants learn to transform raw findings into well-structured engineering tickets. The goal is to produce GitHub issues that another engineer could pick up and act on without needing additional context from the author.

## Prerequisites

- Participant has completed the Code/Infrastructure Audit session (Day 3)
- Participant has at least one evidence-backed finding
- GitHub Issue Template is available (see [template](../templates/github-issue-template.md))
- If participant has no findings from Day 3, use this session to find one and convert it directly

---

## Ticket Structure

Every ticket created during this session must include these fields:

| Field | Description | Required |
|---|---|---|
| **Problem** | Clear statement of what is wrong or missing | Yes |
| **Evidence** | Specific file, line, config, or behavior that demonstrates the problem | Yes |
| **Impact** | What happens if this is not addressed? Who or what is affected? | Yes |
| **Suggested Fix** | Recommended approach to resolve the issue | Yes |
| **Acceptance Criteria** | How do we know the fix is complete and correct? | Yes |
| **Priority** | Critical / High / Medium / Low | Yes |
| **Estimated Effort** | Small (hours) / Medium (days) / Large (weeks) | Yes |
| **Owner or Recommended Owner** | Who should work on this? (team or role, not necessarily a name) | Recommended |
| **Dependencies** | What must be done before this can be started? | If applicable |

### What Makes a Good Ticket

| Good Ticket | Bad Ticket |
|---|---|
| "Database connection string is hardcoded in `appsettings.json` (line 12). Move to Key Vault." | "Security could be better." |
| "No health check endpoint exists. Add `/health` returning service status." | "Add monitoring." |
| "Error in `PaymentService.Process()` (line 45) is caught and silently swallowed." | "Improve error handling." |

---

## Baseline Path

**For:** Beginner and intermediate participants  
**Goal:** Convert one finding into a complete, actionable GitHub issue  
**Time:** ~45 minutes of guided work

### Steps

#### Step 1: Review and Refine Findings (10 min)

Before creating tickets, review the participant's Day 3 findings:

1. **Is the finding specific?** Does it reference a file, line, or configuration?
2. **Is the evidence solid?** Can you verify it in the code?
3. **Is the impact clear?** What happens if this is not fixed?

**If findings are vague:** Spend 10 minutes refining. Use the audit approach from Day 3 to add evidence. Do not create tickets from vague findings.

#### Step 2: Create the GitHub Issue (25 min)

Using the [GitHub Issue Template](../templates/github-issue-template.md):

1. Write the problem statement — one or two sentences
2. Add the evidence — file path, line number, or screenshot
3. Describe the impact — what could go wrong
4. Suggest a fix — what should be done
5. Write acceptance criteria — how do we know it is done
6. Set priority and effort

**Coach check at 15 min:** Is the ticket taking shape? If the participant is stuck on wording, help them focus on clarity over polish.

#### Step 3: Review and Submit (10 min)

Review the ticket together:
- Would an engineer who has not seen this code understand the problem?
- Is the evidence specific enough to locate the issue?
- Are the acceptance criteria testable?

If the ticket passes review, the participant submits it as a GitHub issue (or saves it as a draft).

---

## Advanced Path

**For:** Advanced participants  
**Goal:** Create a prioritized backlog with multiple issues, severity assignments, and implementation recommendations  
**Time:** ~45 minutes of self-directed work with check-ins

### Steps

#### Step 1: Convert All Findings to Tickets (20 min)

Convert each finding from the audit report or risk register into a GitHub issue using the template. Focus on quality — each ticket should stand on its own.

#### Step 2: Prioritize Using the Matrix (15 min)

Apply the prioritization matrix to organize the backlog:

| | **Low Effort** | **High Effort** |
|---|---|---|
| **High Impact** | 🟢 **Do First** — Quick wins with significant impact | 🟡 **Plan** — Important but requires investment |
| **Low Impact** | 🔵 **Quick Win** — Easy improvements, do when convenient | ⚪ **Defer** — Not worth the effort right now |

For each ticket, assign:
- **Severity:** Critical / High / Medium / Low
- **Effort:** Small / Medium / Large
- **Confidence:** How certain are we that this is a real issue? (High / Medium / Low)
- **Recommended Owner:** Which team or role should handle this?

#### Step 3: Create Implementation Plan (10 min)

For the top-priority items, create a brief implementation plan:
- What order should they be addressed?
- Are there dependencies between tickets?
- Can any tickets be combined into a single PR?
- Are there infrastructure changes that must happen before code changes?

---

## Decision Tree

```
START: Participant begins ticket triage session
  │
  ├─ Are Day 3 findings available?
  │   ├─ NO → Find one risk now (compressed audit, 10 min)
  │   │         └─ Then proceed to ticket creation
  │   │
  │   └─ YES → Are findings specific and evidence-backed?
  │       ├─ NO (vague findings)
  │       │   → Refine before creating tickets
  │       │   → Add evidence, clarify impact
  │       │   → Do not create vague tickets
  │       │
  │       └─ YES → Create GitHub issues
  │           ├─ One finding → Baseline: one detailed ticket
  │           │
  │           └─ Multiple findings → Prioritize
  │               ├─ Baseline: pick top finding, create one ticket
  │               │
  │               └─ Advanced: create all tickets,
  │                   apply priority matrix,
  │                   build implementation plan
```

---

## Copilot Prompts for This Session

### Converting Findings to Tickets

```
Convert these audit findings into GitHub issues with clear problem statements,
evidence references, impact descriptions, and acceptance criteria. Use a
structured format for each issue.
```

```
Rewrite this vague finding into an actionable engineering ticket:
[paste vague finding here]
Include: problem, evidence, impact, suggested fix, and acceptance criteria.
```

### Prioritization

```
Create a triage table for these findings with columns: severity, confidence,
effort, recommended owner, and next action. Sort by priority (high impact +
low effort first).
```

```
Evaluate these findings and identify which ones should be addressed before
the next production deployment. Explain your reasoning.
```

### Acceptance Criteria

```
Generate acceptance criteria for this infrastructure hardening task:
[paste task description here]
Include functional criteria, security criteria, and validation steps.
```

```
Write testable acceptance criteria for this bug fix:
[paste bug description here]
Include what "fixed" looks like and how to verify it.
```

> **Reminder:** All Copilot output must be verified against the actual code and findings. See [Coaching Principle 4](02-coaching-principles.md#principle-4-use-copilot-as-a-reasoning-assistant-not-an-authority).

---

## Output Templates

- [GitHub Issue Template](../templates/github-issue-template.md) — for individual tickets
- [Risk Register Template](../templates/risk-register-template.md) — for consolidated risk tracking
- [Session Output Template](../templates/session-output-template.md) — for session-level documentation

### Example GitHub Issue

**Title:** Move database connection string to Azure Key Vault

**Problem:**  
The production database connection string is stored in plaintext in `src/appsettings.json` (line 12) and committed to the repository.

**Evidence:**  
File: `src/appsettings.json`, line 12  
Content: `"ConnectionString": "Server=prod-db.example.com;User=admin;Password=..."`  
The file is tracked in git and the credential is visible in the commit history.

**Impact:**  
Anyone with repository read access can see production database credentials. Credential rotation requires code changes and redeployment. This is a high-severity security risk.

**Suggested Fix:**  
1. Move connection string to Azure Key Vault
2. Update application to read from Key Vault at runtime using managed identity
3. Remove credential from repository history using BFG Repo-Cleaner
4. Add secret scanning to the CI pipeline to prevent future occurrences

**Acceptance Criteria:**  
- [ ] Connection string is not present in any file in the repository
- [ ] Application successfully connects to the database using Key Vault reference
- [ ] Secret scanning is enabled and blocks commits containing credential patterns
- [ ] Git history has been cleaned of the exposed credential

**Priority:** Critical  
**Effort:** Medium (1–2 days)  
**Labels:** `security`, `infrastructure`, `credentials`  
**Owner:** Platform/Infrastructure team  
**Dependencies:** Azure Key Vault must be provisioned; managed identity must be configured

---

## Common Pitfalls

| Pitfall | How to Address |
|---|---|
| Participant creates vague tickets | "Would an engineer who has never seen this code know what to do from this ticket alone?" |
| Participant creates too many low-quality tickets | "Let's focus on your top 3 findings. Make each ticket excellent." |
| Participant struggles with acceptance criteria | "How would you test that this is fixed? What would you check?" |
| Participant copies Copilot's ticket verbatim | "This is a good start. Now customize it — does it match the actual evidence you found?" |
| Priority is assigned without reasoning | "Why is this critical? What is the blast radius if it is not fixed?" |
