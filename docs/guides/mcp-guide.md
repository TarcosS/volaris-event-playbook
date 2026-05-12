# MCP Guide (Model Context Protocol)

> What MCP is, how to set it up, and how to use it during the event for enhanced code understanding and auditing.

---

## What Is MCP?

The **Model Context Protocol (MCP)** is an open standard that allows AI tools (like Copilot, Claude, etc.) to connect to external data sources and tools through "MCP servers." Think of it as giving your AI assistant access to specialized capabilities — file systems, databases, APIs, documentation, and more.

**Why it matters for the event:** MCP can give Copilot (and other AI tools) deeper access to codebases, infrastructure, and documentation during audits. Advanced participants can set it up to enhance their audit capabilities.

---

## MCP Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   AI Tool    │────▶│  MCP Client  │────▶│  MCP Server  │
│ (Copilot,    │     │ (built into  │     │ (provides    │
│  Claude,     │     │  IDE/editor) │     │  tools and   │
│  etc.)       │     │              │     │  resources)  │
└──────────────┘     └──────────────┘     └──────────────┘
                                                │
                                          ┌─────┴─────┐
                                          │ Data      │
                                          │ Sources   │
                                          │ (files,   │
                                          │  APIs,    │
                                          │  DBs)     │
                                          └───────────┘
```

---

## Setup in VS Code

### Step 1: Check VS Code Version

MCP support requires VS Code 1.99+ (or VS Code Insiders).

```bash
code --version
```

### Step 2: Create MCP Configuration

MCP servers are configured in `.vscode/mcp.json` (project-level) or in VS Code user settings (global).

**Project-level configuration (recommended for the event):**

```bash
mkdir -p .vscode
```

Create `.vscode/mcp.json`:

```json
{
  "servers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "${workspaceFolder}"
      ]
    }
  }
}
```

### Step 3: Enable MCP in VS Code Settings

```json
{
  "chat.mcp.enabled": true
}
```

Or via the command palette: `Ctrl+Shift+P` → "MCP: Enable"

### Step 4: Verify

1. Open the Command Palette (`Ctrl+Shift+P`)
2. Type "MCP: List Servers"
3. You should see your configured servers
4. In Copilot Chat, MCP tools should be available

---

## Useful MCP Servers for the Event

### Filesystem Server

Gives the AI deep access to read and search files in the workspace.

```json
{
  "servers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "${workspaceFolder}"
      ]
    }
  }
}
```

### GitHub Server

Access GitHub issues, PRs, and repository data.

```json
{
  "servers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github-token}"
      }
    }
  }
}
```

### Fetch Server

Fetch and read web pages — useful for checking documentation URLs found in code.

```json
{
  "servers": {
    "fetch": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-fetch"]
    }
  }
}
```

### Azure MCP Server (if available)

Check the latest Azure MCP server packages for direct Azure resource inspection from within the AI conversation.

---

## Using MCP for Audits

### How It Enhances the Audit Flow

Without MCP, Copilot Chat with `@workspace` does a decent job of searching the workspace. With MCP, the AI gets:
- More precise file reading and searching
- Access to external data (GitHub issues, web docs)
- Tool-based interactions (structured queries vs. text search)

### Audit Workflow with MCP

1. **Setup:** Configure filesystem + GitHub MCP servers
2. **Explore:** Ask the AI to use MCP tools to deeply inspect the codebase
3. **Audit:** The AI can now cross-reference code with GitHub issues, check actual file contents precisely, and follow import chains
4. **Document:** Findings are more precise because the AI had better access to evidence

### Example Prompts with MCP

```
Use the filesystem tools to read the main configuration files in this project.
Identify any hardcoded secrets, connection strings, or API keys.
```

```
Search the codebase for all error handling patterns. Identify files where
errors are caught but not logged or re-thrown.
```

```
Use the GitHub tools to check if there are any open security-related issues
for this repository. Cross-reference with the risks I found in the code.
```

---

## Coach Checklist for MCP Setup

- [ ] Participant has VS Code 1.99+ (or Insiders)
- [ ] `.vscode/mcp.json` created with at least the filesystem server
- [ ] `chat.mcp.enabled` is true in VS Code settings
- [ ] MCP server appears in "MCP: List Servers"
- [ ] Test: ask Copilot Chat a question that uses MCP tools
- [ ] Verify: the response includes data retrieved via MCP (not just workspace search)

---

## Troubleshooting

| Issue | Fix |
|---|---|
| "MCP" option not visible | Update VS Code to 1.99+. Check `chat.mcp.enabled`. |
| Server fails to start | Check Node.js is installed (`node --version`). Run `npx` command manually to see error. |
| Server starts but no tools appear | Restart VS Code. Check MCP: List Servers output. |
| Permission denied on filesystem | Check the path in the args. Use `${workspaceFolder}`. |
| GitHub server auth fails | Verify the PAT has correct scopes (repo, read:org). |

### Fallback

If MCP cannot be set up:
- `@workspace` in Copilot Chat still provides good repo-wide context
- All audit activities work without MCP — it just adds depth
- Focus on Copilot Chat + manual code review instead
