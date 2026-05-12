---
title: "CLI Tools"
layout: default
parent: "Tool Guides"
nav_order: 4
---

> Essential command-line tools coaches will use and teach. Copy-paste ready commands.

---

## GitHub CLI (`gh`)

### Installation

```bash
# macOS
brew install gh

# Windows
winget install GitHub.cli

# Linux (Debian/Ubuntu)
sudo apt install gh
```

### Authentication

```bash
# Login (interactive)
gh auth login

# Check status
gh auth status

# Switch accounts (if multiple)
gh auth switch
```

### Repository Operations

```bash
# Clone a repository
gh repo clone <owner>/<repo>

# View repo in browser
gh repo view --web

# List repos in an organization
gh repo list <org-name> --limit 50
```

### Issue Operations (Day 4 — Ticket Creation)

```bash
# Create an issue
gh issue create --title "Title" --body "Body" --label "security"

# Create issue from a file
gh issue create --title "Title" --body-file ./finding.md

# List issues
gh issue list

# View an issue
gh issue view <number>
```

### Pull Request Operations

```bash
# Create a PR
gh pr create --title "Title" --body "Description"

# List PRs
gh pr list

# View PR diff
gh pr diff <number>
```

### Useful for Coaches

```bash
# Quickly check org membership
gh api orgs/<org>/members --jq '.[].login'

# Check if Copilot is enabled for a repo
gh api repos/<owner>/<repo> --jq '.permissions'

# Check user's Copilot status
# (user must check themselves at https://github.com/settings/copilot)
```

---

## Azure CLI (`az`)

See the full [Azure Guide](azure-guide.md) for detailed commands.

### Quick Reference

```bash
# Login
az login
az login --use-device-code    # fallback

# Current context
az account show --output table

# List resources
az resource list -g <rg-name> --output table

# RBAC check
az role assignment list --assignee <email> --output table
```

---

## Git

### Essential Commands

```bash
# Clone
git clone <url>

# Status
git status

# Stage and commit
git add .
git commit -m "Description of change"

# Push
git push origin main

# Pull latest
git pull origin main

# View log
git log --oneline -20

# View diff
git diff
git diff --staged
```

### Useful for Auditing

```bash
# Search for patterns in code (secrets, hardcoded values)
git log --all --oneline -S "password"
git log --all --oneline -S "secret"
git log --all --oneline -S "api_key"

# Check for large files that shouldn't be committed
git rev-list --objects --all | git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' | sort -k3 -n -r | head -20

# Show file history
git log --follow -p -- <file-path>

# Check .gitignore coverage
git status --ignored
```

---

## Node.js / npm

```bash
# Check version
node --version
npm --version

# Install dependencies
npm install

# Run scripts
npm run build
npm run test
npm run start

# Audit dependencies for vulnerabilities
npm audit
npm audit --json    # machine-readable output

# List outdated packages
npm outdated
```

---

## .NET

```bash
# Check version
dotnet --version
dotnet --list-sdks

# Restore dependencies
dotnet restore

# Build
dotnet build

# Run
dotnet run

# Test
dotnet test

# List outdated packages
dotnet list package --outdated

# Check for vulnerable packages
dotnet list package --vulnerable
```

---

## Python

```bash
# Check version
python3 --version
pip3 --version

# Install dependencies
pip3 install -r requirements.txt

# Run
python3 app.py

# Check for vulnerabilities (with pip-audit)
pip3 install pip-audit
pip-audit

# List installed packages
pip3 list
pip3 list --outdated
```

---

## Quick Troubleshooting

### "Command not found"

| Command | Install |
|---|---|
| `gh` | `brew install gh` / `winget install GitHub.cli` |
| `az` | `brew install azure-cli` / [aka.ms/installazurecli](https://aka.ms/installazurecli) |
| `git` | `brew install git` / [git-scm.com](https://git-scm.com) |
| `node` | [nodejs.org](https://nodejs.org) / `brew install node` |
| `dotnet` | [dot.net](https://dot.net) |
| `python3` | [python.org](https://python.org) / `brew install python` |

### Permission Issues

```bash
# macOS: if brew fails
xcode-select --install

# npm global installs fail
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH

# pip permission denied
pip3 install --user <package>
```

### Proxy / Network Issues

```bash
# Check if the network is blocking
curl -I https://github.com
curl -I https://portal.azure.com
curl -I https://registry.npmjs.org

# Git proxy configuration (if behind corporate proxy)
git config --global http.proxy http://proxy:port

# npm proxy
npm config set proxy http://proxy:port

# Azure CLI proxy
export HTTPS_PROXY=http://proxy:port
```

---

## Coach Quick Reference

| I need to... | Command |
|---|---|
| Check participant's GitHub auth | `gh auth status` |
| Check participant's Azure auth | `az account show` |
| Check Git config | `git config --list` |
| Audit npm packages | `npm audit` |
| Audit .NET packages | `dotnet list package --vulnerable` |
| Audit Python packages | `pip-audit` |
| Search for secrets in git history | `git log -S "password" --all` |
| Check what's not in .gitignore | `git status --ignored` |
