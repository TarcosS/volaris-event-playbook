# Copilot Instructions Guide

> How to create and manage project-level Copilot custom instructions and prompt files.

---

## What Are Copilot Instructions?

Copilot instructions are project-level configuration files that tell Copilot about your repository's conventions, patterns, and domain-specific rules. They make Copilot's suggestions more accurate and contextually relevant.

**Why this matters for the event:** Advanced participants can create these as a concrete Day 2 output. It also makes subsequent audit work more effective because Copilot understands the project better.

---

## `.github/copilot-instructions.md`

This is the primary way to give Copilot project-level context.

### Setup Steps

1. **Create the directory and file:**

```bash
mkdir -p .github
touch .github/copilot-instructions.md
```

2. **Write instructions for the project:**

```markdown
# Copilot Instructions for [Project Name]

## Project Overview
This is a [type of application] built with [technologies].
It [what it does] for [who].

## Architecture
- Frontend: [framework/location]
- Backend: [framework/location]
- Database: [type/location]
- Infrastructure: [cloud provider, IaC tool]

## Coding Conventions
- Use [naming convention] for variables and functions
- Error handling: [pattern — e.g., "always use try/catch with specific error types"]
- Logging: [library and format]
- Testing: [framework and coverage expectations]

## Domain Terminology
- [Term 1]: [definition]
- [Term 2]: [definition]

## Important Rules
- Never hardcode secrets or connection strings
- All API endpoints must have input validation
- All database queries must use parameterized queries
- [Project-specific rules]
```

3. **Verify it works:**
   - Open a file in the repository
   - Ask Copilot Chat: "What are the coding conventions for this project?"
   - Copilot should reference your custom instructions

### Coach Checklist for This Activity

- [ ] Participant creates `.github/copilot-instructions.md`
- [ ] File includes: project overview, architecture, conventions, terminology
- [ ] Content is specific to the actual project (not generic)
- [ ] Verified: Copilot references the instructions when asked about the project

---

## Prompt Files (`.github/prompts/`)

Prompt files are reusable prompts stored in the repository. They appear as slash commands in Copilot Chat.

### Setup Steps

1. **Create the directory:**

```bash
mkdir -p .github/prompts
```

2. **Create a prompt file (`.prompt.md`):**

```bash
# Example: audit prompt
cat > .github/prompts/audit.prompt.md << 'EOF'
---
description: Run a security and reliability audit on the current file or workspace
---

Audit this code for:
1. Security risks (hardcoded secrets, missing validation, injection vulnerabilities)
2. Reliability risks (missing error handling, no retry logic, silent failures)
3. Maintainability issues (complex functions, tight coupling, missing abstractions)

For each finding:
- State the risk clearly
- Reference the specific file and line number
- Explain the impact
- Suggest a concrete fix
- Rate severity: Critical / High / Medium / Low

Prioritize by severity. Be specific — reference actual code, not general advice.
EOF
```

3. **More prompt file examples:**

**Documentation prompt:**
```markdown
---
description: Generate living documentation for the current file
---

Generate documentation for this code:
1. What it does (purpose and behavior)
2. Input/output specifications
3. Dependencies and side effects
4. Error handling behavior
5. Usage examples
6. Known limitations

Reference the actual implementation. Do not describe what the code should do — describe what it actually does.
```

**Ticket creation prompt:**
```markdown
---
description: Convert a finding into a GitHub issue
---

Convert the following finding into a well-structured GitHub issue:

Include:
- Problem: clear statement of what is wrong
- Evidence: specific file, line number, and code snippet
- Impact: what happens if this is not addressed
- Suggested fix: step-by-step resolution
- Acceptance criteria: how to verify the fix is complete
- Priority: Critical / High / Medium / Low
- Effort: Small (hours) / Medium (days) / Large (weeks)
```

4. **Using prompt files:**
   - In Copilot Chat, type `/` to see available prompts
   - Select the prompt file to execute it
   - The prompt runs with the current file/workspace context

### Coach Checklist for This Activity

- [ ] Participant creates `.github/prompts/` directory
- [ ] At least one prompt file created (audit, documentation, or ticket)
- [ ] Prompt file has YAML frontmatter with description
- [ ] Prompt file tested in Copilot Chat
- [ ] Output is specific and references actual code

---

## VS Code Settings for Copilot

### Recommended settings for the event

```json
{
  "github.copilot.enable": {
    "*": true
  },
  "github.copilot.chat.localeOverride": "en",
  "chat.promptFiles": true
}
```

### Enabling prompt files

If prompt files don't appear in Chat:
1. Open VS Code Settings (`Cmd+,` / `Ctrl+,`)
2. Search for "chat prompt files"
3. Enable the setting
4. Reload VS Code

---

## Coaching Flow: Day 2 Advanced Activity

1. **Explain the concept** (2 min)
   > "Custom instructions tell Copilot about your project's rules and patterns. This makes its suggestions much more accurate."

2. **Create copilot-instructions.md** (15 min)
   - Guide participant through the template above
   - Emphasize: content must come from the actual codebase
   - Ask: "What conventions does this project follow? What domain terms are used?"

3. **Create a prompt file** (10 min)
   - Start with the audit prompt — it's directly useful for Day 3
   - Test it on a real file

4. **Verify** (3 min)
   - Ask Copilot about the project: does it reference the instructions?
   - Run the prompt file: does it produce better results than a generic prompt?

### Output

A committed `.github/copilot-instructions.md` and optionally `.github/prompts/*.prompt.md` files that enhance Copilot's accuracy for the project.
