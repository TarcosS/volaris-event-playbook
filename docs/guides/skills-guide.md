---
title: "Skills"
layout: default
parent: "Tool Guides"
nav_order: 6
---

> How to install, use, and create Copilot skills and extensions for enhanced capabilities during the event.

---

## What Are Copilot Skills/Extensions?

Copilot extensions (also called skills or agents) are add-ons that give Copilot specialized capabilities beyond its default behavior. They can:
- Connect to external services (Azure, databases, monitoring)
- Provide domain-specific knowledge (security patterns, compliance rules)
- Automate multi-step workflows (audit → findings → tickets)

**Why this matters for the event:** Advanced participants can install or create skills that make their audit and documentation work more efficient.

---

## Types of Copilot Extensions

| Type | Description | Where |
|---|---|---|
| **Chat Extensions** | Add new `@agent` participants to Copilot Chat | GitHub Marketplace / VS Code |
| **VS Code Extensions with Copilot Integration** | VS Code extensions that enhance Copilot | VS Code Marketplace |
| **Custom Chat Participants** | Build your own `@agent` for Copilot Chat | VS Code Extension API |
| **Copilot Agent Skills (`.agents/`)** | Project-level skills defined in the repo | `.agents/` directory |

---

## Installing Extensions from Marketplace

### In VS Code

1. Open Extensions panel (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search for Copilot-related extensions
3. Look for extensions tagged with "Copilot" or "AI"
4. Install and reload VS Code

### Useful Extensions for the Event

| Extension | Purpose | Use Case |
|---|---|---|
| **GitHub Copilot** | Core AI coding assistant | Required — base functionality |
| **GitHub Copilot Chat** | Chat interface for Copilot | Required — conversation-based coding |
| **Azure Tools** | Azure resource management from VS Code | Day 3 — infrastructure inspection |
| **Docker** | Container management and Dockerfile support | Auditing containerized apps |
| **GitLens** | Enhanced Git capabilities | Audit — who changed what and when |
| **Error Lens** | Inline error/warning display | Quick visual audit of code issues |

---

## Project-Level Agent Skills (`.agents/`)

### What Are Agent Skills?

Agent skills are Markdown files in the `.agents/skills/` directory that define reusable instructions for Copilot. When invoked, they provide Copilot with specialized context and behavior.

### Structure

```
.agents/
└── skills/
    └── my-skill/
        └── SKILL.md
```

### Creating a Custom Skill

**Example: Audit Skill**

Create `.agents/skills/security-audit/SKILL.md`:

```markdown
---
name: security-audit
description: Perform a security audit on the codebase
---

# Security Audit Skill

When invoked, perform the following security audit:

## Audit Checklist

1. **Secrets and Credentials**
   - Search for hardcoded passwords, API keys, connection strings
   - Check for .env files committed to the repository
   - Verify .gitignore includes secret-containing files

2. **Input Validation**
   - Check all user-facing endpoints for input validation
   - Look for SQL injection, XSS, and command injection risks
   - Verify parameterized queries are used

3. **Authentication & Authorization**
   - Review auth middleware and access controls
   - Check for missing authentication on endpoints
   - Verify principle of least privilege in RBAC

4. **Dependencies**
   - Check for known vulnerabilities (npm audit, dotnet list package --vulnerable)
   - Identify outdated packages
   - Look for unmaintained dependencies

5. **Configuration**
   - Check for debug mode in production configs
   - Verify HTTPS is enforced
   - Check CORS configuration

## Output Format

For each finding, provide:
- **Risk**: What is the issue
- **Evidence**: File path and line number
- **Severity**: Critical / High / Medium / Low
- **Fix**: What to do about it
```

### Using the Skill

Once created, the skill can be invoked in Copilot Chat or referenced by name. The exact invocation method depends on the IDE and Copilot version.

---

## Creating Custom Chat Participants (Advanced)

For participants who want to build their own Copilot Chat extension:

### Concept

A custom chat participant adds a new `@agent-name` to Copilot Chat that handles specific types of queries.

### Basic Structure (VS Code Extension API)

```typescript
// In a VS Code extension's activate function:
const participant = vscode.chat.createChatParticipant(
  'my-event.auditor',
  async (request, context, response, token) => {
    // Handle the chat request
    const query = request.prompt;
    
    // Use Copilot's language model
    const model = await vscode.lm.selectChatModels({
      vendor: 'copilot',
      family: 'gpt-4o'
    });
    
    // Generate response with custom system prompt
    const messages = [
      vscode.LanguageModelChatMessage.User(
        `You are a security auditor. ${query}`
      )
    ];
    
    const chatResponse = await model[0].sendRequest(messages, {}, token);
    for await (const part of chatResponse.text) {
      response.markdown(part);
    }
  }
);

participant.iconPath = new vscode.ThemeIcon('shield');
```

**Note:** This is an advanced activity. Only suggest it to participants who are already comfortable with VS Code extension development.

---

## Coach Checklist for Skills Activities

### Basic (All Participants)

- [ ] Copilot and Copilot Chat extensions installed
- [ ] Extensions are active and functional
- [ ] Participant knows how to use `@workspace` in Chat

### Intermediate (Day 2 Advanced)

- [ ] Additional useful extensions installed (GitLens, Azure Tools, etc.)
- [ ] At least one project-level skill created in `.agents/skills/`
- [ ] Skill tested and producing useful output

### Advanced (If Time Permits)

- [ ] Custom prompt files created (see [Copilot Instructions Guide](copilot-instructions-guide.md))
- [ ] MCP servers configured (see [MCP Guide](mcp-guide.md))
- [ ] Custom chat participant concept understood (may not have time to implement)

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Extension won't install | Check VS Code version compatibility. Try updating VS Code. |
| Extension installed but not active | Reload VS Code (`Ctrl+Shift+P` → "Reload Window") |
| Custom skill not recognized | Check file path: must be `.agents/skills/<name>/SKILL.md` |
| Chat participant not showing | Extension must be activated. Check extension output logs. |
| Too many extensions causing slowness | Disable non-essential extensions. Use VS Code profiles. |

### Fallback

If skills/extensions cannot be set up:
- All audit work can be done with base Copilot + manual review
- Custom instructions (`.github/copilot-instructions.md`) provide similar benefits with simpler setup
- Focus on prompt engineering rather than tooling configuration
