# Copilot Chat Guide

> Step-by-step guide for coaches: how to use and teach GitHub Copilot Chat during the event.

---

## Quick Setup Verification

Before coaching participants on Copilot, verify it works:

```bash
# Check Copilot status
# In VS Code: look at bottom status bar for Copilot icon (should be active, not grayed)
# Or check online:
# https://github.com/settings/copilot
```

### Checklist

- [ ] Copilot extension installed in VS Code
- [ ] Copilot Chat extension installed (separate from inline Copilot)
- [ ] Icon in status bar is active (not grayed out or showing error)
- [ ] Test: open any file, start typing — suggestions should appear
- [ ] Test: open Chat panel (Ctrl+Shift+I / Cmd+Shift+I) — should respond

---

## Copilot Chat Panel Basics

### Opening Chat

| Action | Shortcut |
|---|---|
| Open Chat panel | `Ctrl+Shift+I` (Windows/Linux) / `Cmd+Shift+I` (Mac) |
| Inline Chat (in editor) | `Ctrl+I` / `Cmd+I` |
| Quick Chat (floating) | `Ctrl+Shift+Alt+I` / `Cmd+Shift+Alt+I` |

### Chat Modes

| Mode | When to Use | How |
|---|---|---|
| **Chat panel** | Long conversations, exploration, multi-step tasks | Side panel |
| **Inline Chat** | Quick edits, explanations of selected code | `Cmd+I` on selection |
| **Quick Chat** | Fast one-off questions | Command palette |
| **Edits mode** | Multi-file changes with Copilot applying them | Chat panel → Edits |

**Coach tip:** For the event, the **Chat panel** is the primary tool. Inline Chat is useful for quick code explanations.

---

## Key Chat Participants (@-mentions)

Teach participants these for targeted queries:

| Participant | What It Does | Example |
|---|---|---|
| `@workspace` | Searches across the entire workspace/repo | `@workspace What does this application do?` |
| `@vscode` | VS Code settings, extensions, features | `@vscode How do I change the theme?` |
| `@terminal` | Terminal commands and output | `@terminal What was the last error?` |

### Most Useful for the Event

**`@workspace` is the most important.** Participants should use it for:
- Repository exploration
- Finding entry points
- Understanding architecture
- Cross-file analysis

**Example coaching flow:**

> Coach: "Start by asking Copilot about the whole project. Type `@workspace` and then your question."

---

## Slash Commands

| Command | Purpose | Example |
|---|---|---|
| `/explain` | Explain selected code | Select function → `/explain` |
| `/fix` | Suggest a fix for selected code | Select buggy code → `/fix` |
| `/tests` | Generate tests for selected code | Select function → `/tests` |
| `/doc` | Generate documentation for selected code | Select function → `/doc` |
| `/new` | Scaffold a new file or project | `/new Express API with health check` |

---

## Exploring a Repository

### Step-by-step coaching flow for Day 1 and Day 2

**Step 1: What is this project?**

```
@workspace Explain this repository structure in simple terms. What is the purpose of each top-level directory?
```

**Coach check:** Does the answer match reality? Ask the participant to verify by looking at the actual directories.

**Step 2: Find the entry point**

```
@workspace Identify the main entry point of this application and summarize what it does. Include the file path.
```

**Coach check:** Ask them to open that file. Does it match Copilot's description?

**Step 3: Understand dependencies**

```
@workspace List the key dependencies in this project and explain what each one is used for.
```

**Coach check:** Compare with `package.json`, `requirements.txt`, `.csproj`, or equivalent.

**Step 4: Find configuration**

```
@workspace What environment variables or configuration files does this project use? Where are they defined?
```

---

## Documentation Generation

### Step-by-step coaching flow for Day 2

**Create a README:**

```
@workspace Create a README for this project. Include:
- What the application does
- Prerequisites
- How to set up and run locally
- Environment variables needed
- Architecture overview
Reference actual files and code in the repository.
```

**Coach reminder:** "This is a draft. Verify every statement against the actual code before committing."

**Improve existing docs:**

```
@workspace Review the existing README for accuracy. Identify any statements that don't match the current code. Suggest corrections with file references.
```

**Create setup guide:**

```
@workspace Create step-by-step instructions for a new developer to set up and run this project locally. Include all commands they need to run.
```

---

## Code Auditing

### Step-by-step coaching flow for Day 3

**General audit:**

```
@workspace Audit this repository for security, maintainability, and deployment risks. For each finding:
1. State the risk
2. Reference the specific file and line
3. Explain the impact
4. Suggest a fix
Prioritize by severity.
```

**Security-focused audit:**

```
@workspace Scan this repository for security risks:
- Hardcoded secrets or credentials
- Missing input validation
- Insecure dependencies
- Overly permissive configurations
- Exposed endpoints without authentication
Reference specific files and lines for each finding.
```

**Infrastructure audit:**

```
@workspace Review the infrastructure configuration files (Bicep, Terraform, ARM, Docker, CI/CD) for:
- Security risks (permissions, networking, secrets)
- Reliability risks (missing health checks, no retry logic)
- Cost risks (over-provisioned resources, missing autoscaling)
Reference specific files.
```

**Targeted file audit (for stuck participants):**

```
Review this file for risks. What could go wrong? What's missing? Reference specific lines.
```

(Use this when a participant is stuck — point them at one specific file.)

---

## Ticket Creation

### Step-by-step coaching flow for Day 4

**Convert finding to ticket:**

```
Convert this audit finding into a GitHub issue:
[paste the finding]

Include:
- Clear problem statement
- Evidence (file, line)
- Impact description
- Suggested fix
- Testable acceptance criteria
- Priority and effort estimate
```

**Refine a vague finding:**

```
Rewrite this vague finding into an actionable engineering ticket:
"[paste vague finding]"
Make it specific: reference files, explain the actual risk, and include acceptance criteria.
```

**Generate acceptance criteria:**

```
Write testable acceptance criteria for this fix:
[describe the fix]
Include: what "fixed" looks like, how to verify it, and edge cases to test.
```

---

## Troubleshooting

### Copilot Not Responding

1. Check the Copilot icon in the status bar
2. Click on it — does it show errors?
3. Try: `Ctrl+Shift+P` → "Copilot: Sign Out" → Sign back in
4. Restart VS Code
5. Check network: can the IDE reach `api.github.com`?

### Copilot Gives Poor Answers

- **Too generic?** Add `@workspace` to give it repository context
- **Wrong language?** Specify: "Using TypeScript..." or "In this .NET project..."
- **Hallucinating files?** Ask: "Only reference files that actually exist in this repository"
- **Too verbose?** Ask: "Be concise. List findings as bullet points."

### Copilot Not Available for This Repo

- Check organization settings: Copilot may be disabled for specific repos
- Check content exclusion policies
- Fallback: all activities work without Copilot — just slower

---

## Prompt Engineering Tips for Coaches

### Make prompts specific

❌ Bad: "Review this code"
✅ Good: "Review this file for security risks. Reference specific lines. Explain the impact of each finding."

### Give context

❌ Bad: "What's wrong here?"
✅ Good: "This is a payment processing service. Review the error handling in this function. What could go wrong during a payment failure?"

### Request evidence format

✅ "For each finding, include: file path, line number, risk description, and severity."

### Chain prompts

1. First: "What does this service do?"
2. Then: "What are the security risks?"
3. Then: "Convert the top risk into a GitHub issue with acceptance criteria."

This mirrors the event flow: understand → audit → ticket.
