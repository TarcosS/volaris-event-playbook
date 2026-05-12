---
title: "Coach Runbook"
layout: default
nav_order: 6
---

> Day-by-day interactive checklist for Kaan & KaanTurgut. Tick boxes as you go. Follow the links when you need detail.

---

## How to Use This Runbook

This is your **operational to-do list** for the entire event. Open it at the start of each day, follow the checkboxes in order, and tick them off as you complete them. Each item tells you what to do, which guide to reference, and what output to capture.

**Legend:**
- ☐ = To do
- ✅ = Done (change `[ ]` to `[x]` as you go)
- 🔀 = Decision point — follow the branch
- 📖 = Reference link to a guide or doc
- ⏱️ = Time indicator

---

## Pre-Event Preparation (Before Day 1)

### Coach Setup — Both Coaches

- [ ] **Verify your own Azure access** ⏱️ 10 min
  - [ ] Log in to the event Azure tenant → 📖 [Azure Guide](guides/azure-guide.md#logging-in)
  - [ ] Confirm you can see the event subscription and resource groups
  - [ ] Run `az account show` to confirm correct tenant
  - [ ] Test resource group access: `az group list --output table`

- [ ] **Verify your own GitHub access** ⏱️ 5 min
  - [ ] Log in to the event GitHub organization
  - [ ] Confirm you can access all participant repositories
  - [ ] Run `gh auth status` to verify CLI access → 📖 [CLI Tools Guide](guides/cli-tools-guide.md#github-cli)

- [ ] **Verify Copilot is working** ⏱️ 5 min
  - [ ] Open VS Code, confirm Copilot icon is active
  - [ ] Test Copilot Chat: ask a question about an open file → 📖 [Copilot Chat Guide](guides/copilot-chat-guide.md)
  - [ ] Verify Copilot suggestions appear when typing code

- [ ] **Set up MCP (if using for advanced participants)** ⏱️ 15 min
  - [ ] Install and configure MCP servers → 📖 [MCP Guide](guides/mcp-guide.md#setup)
  - [ ] Test connection from IDE
  - [ ] Prepare a demo-ready MCP configuration

- [ ] **Review Skills setup** ⏱️ 10 min
  - [ ] Verify Copilot extensions/skills are available → 📖 [Skills Guide](guides/skills-guide.md)
  - [ ] Prepare a list of recommended skills for participants

- [ ] **Prepare materials**
  - [ ] Print or bookmark the [Quick Reference](13-quick-reference.md)
  - [ ] Open the [If/Else Playbook](08-if-else-playbook.md) in a pinned tab
  - [ ] Have all [templates](../templates/) accessible
  - [ ] Confirm participant list and assigned repositories

- [ ] **Coach alignment meeting** ⏱️ 15 min
  - [ ] Agree on room split: who covers which tables/groups?
  - [ ] Agree on escalation contact: who is the event tech team lead?
  - [ ] Review Day 1 plan together → 📖 [Day-by-Day Flow](04-day-by-day-flow.md)
  - [ ] Decide: who handles access issues vs. who handles coaching?

---

## Day 1: Orientation, Setup, and Diagnosis

### Opening (First 15 min)

- [ ] **Introduce yourselves and the event**
  - [ ] Use the opening script → 📖 [Coach Scripts](10-coach-scripts.md#opening-a-session)
  - [ ] Explain the 4-day structure briefly
  - [ ] Set expectations: "You will all leave with concrete outputs"

### Setup Validation (30 min)

**Goal: Every participant has working tools or a fallback path.**

- [ ] **Azure access check** — walk the room
  - [ ] Ask everyone to log in to `portal.azure.com`
  - [ ] 🔀 **Can they log in?**
    - ✅ YES → Check subscription visibility → continue
    - ❌ NO → 📖 [Azure Guide — Troubleshooting](guides/azure-guide.md#troubleshooting)
    - ⏱️ Apply 5-minute rule. If unresolved → escalate → assign fallback

- [ ] **GitHub access check**
  - [ ] Ask everyone to open their assigned repository on GitHub
  - [ ] 🔀 **Can they see the repo?**
    - ✅ YES → continue
    - ❌ NO (404/403) → Verify URL, account, org membership → 📖 [CLI Tools Guide](guides/cli-tools-guide.md#github-cli)
    - ⏱️ If unresolved → pair mode

- [ ] **Copilot access check**
  - [ ] Ask everyone to open VS Code and check Copilot icon
  - [ ] 🔀 **Is Copilot active?**
    - ✅ YES → Test with a quick prompt
    - ❌ NO → 📖 [Copilot Chat Guide — Troubleshooting](guides/copilot-chat-guide.md#troubleshooting)
    - ⏱️ If unresolved → participant works without Copilot (all activities still possible)

- [ ] **Log all blockers** — use [Session Output Template](../templates/session-output-template.md) to track

### Participant Diagnosis (20 min)

- [ ] **Run quick diagnosis for each group/table** → 📖 [Participant Diagnosis](03-participant-diagnosis.md)
  - [ ] Ask the 6 diagnosis questions (don't read like a checklist — be conversational)
  - [ ] For unclear cases: run the diagnostic task (10 min, Copilot + repo inspection)
  - [ ] Record results → [Participant Diagnosis Sheet](../templates/participant-diagnosis-sheet.md)

- [ ] **Classify each participant/group:**
  - [ ] 🔀 **Can they explain a system, use Copilot with evidence, reason about risks?**
    - ✅ YES → **Advanced path**
    - ❌ NO → **Baseline path**
    - ❓ UNCLEAR → Start baseline, upgrade later if warranted

- [ ] **Communicate paths**
  - [ ] Use the baseline assignment script → 📖 [Coach Scripts](10-coach-scripts.md#moving-someone-to-the-baseline-path)
  - [ ] Use the advanced assignment script → 📖 [Coach Scripts](10-coach-scripts.md#moving-someone-to-the-advanced-path)

### Baseline Alignment (30 min)

- [ ] **For baseline participants:** guided repository walkthrough
  - [ ] Show how to use Copilot Chat to explore a repo → 📖 [Copilot Chat Guide](guides/copilot-chat-guide.md#exploring-a-repository)
  - [ ] Demo: "Explain this repository structure" prompt
  - [ ] Demo: "Find the main entry point" prompt
  - [ ] Let them try on their own assigned repo

- [ ] **For advanced participants:** self-directed exploration
  - [ ] Point them to the repo and audit categories
  - [ ] Offer MCP/Skills setup if interested → 📖 [MCP Guide](guides/mcp-guide.md) / [Skills Guide](guides/skills-guide.md)
  - [ ] Check in after 15 minutes

### Day 1 Close (15 min)

- [ ] **Confirm readiness for Day 2**
  - [ ] Every participant diagnosed and classified ✅ / ❌
  - [ ] Every participant has access or fallback ✅ / ❌
  - [ ] All blockers logged and escalated ✅ / ❌
  - [ ] Preview Day 2: Living Documentation

- [ ] **Coach debrief (just the two of you)**
  - [ ] How many beginner / intermediate / advanced / blocked?
  - [ ] Any unresolved access issues?
  - [ ] Adjustments for tomorrow?

---

## Day 2: Living Documentation

### Quick Check (10 min)

- [ ] **Day 1 issues resolved?**
  - [ ] Check with previously blocked participants
  - [ ] 🔀 Resolved → proceed | Still blocked → confirm fallback path

- [ ] **Quick re-diagnosis** — has anyone's level changed?
  - [ ] Anyone who was unclear → reclassify based on Day 1 observations

### Session: Living Documentation (75 min)

📖 Full session guide: [Living Documentation Session](05-living-documentation-session.md)

#### Baseline Participants

- [ ] **Step 1: Repository understanding** ⏱️ 20 min
  - [ ] Guide them through Copilot prompts → 📖 [Copilot Chat Guide — Repository Understanding](guides/copilot-chat-guide.md#exploring-a-repository)
  - [ ] Prompts to use:
    ```
    Explain this repository structure in simple terms.
    Identify the main entry point and summarize what it does.
    List the key dependencies and explain what each one is used for.
    ```
  - [ ] 🔀 **Can they explain the project in 2-3 sentences?**
    - ✅ YES → move to Step 2
    - ❌ NO → more guided exploration needed

- [ ] **Step 2: Identify documentation gaps** ⏱️ 10 min
  - [ ] Checklist: setup? architecture? dependencies? env vars? deployment? limitations?

- [ ] **Step 3: Create documentation** ⏱️ 30 min
  - [ ] Guide them to write a README or improve existing docs
  - [ ] Use Copilot to draft sections → 📖 [Copilot Chat Guide — Documentation](guides/copilot-chat-guide.md#documentation-generation)
  - [ ] **Remind:** verify Copilot output against actual code
  - [ ] ⏱️ Coach check at 15 min: "Is there content? Is it specific?"

#### Advanced Participants

- [ ] **Evaluate existing documentation** ⏱️ 15 min
  - [ ] Accuracy, completeness, currency, AI-usability

- [ ] **Create advanced artifacts** ⏱️ 30 min
  - [ ] Option A: Architecture Decision Records (ADRs)
  - [ ] Option B: Copilot instructions file → 📖 [Copilot Instructions Guide](guides/copilot-instructions-guide.md)
  - [ ] Option C: Begin audit preparation
  - [ ] 🔀 If they set up custom instructions, show them MCP → 📖 [MCP Guide](guides/mcp-guide.md)

### Output Capture (20 min)

- [ ] **Every participant documents their output** → [Session Output Template](../templates/session-output-template.md)
- [ ] **Coach spot-check:**
  - [ ] Is the output specific (not generic)?
  - [ ] Is it evidence-based (references actual code)?
  - [ ] 🔀 If vague → "What specifically did you find? Point to a file."

### Day 2 Close (15 min)

- [ ] **Definition of done check:**
  - [ ] Every participant has at least one documentation artifact ✅ / ❌
  - [ ] Artifacts reference actual code ✅ / ❌
  - [ ] Advanced participants have enhanced docs or started audit ✅ / ❌
- [ ] **Preview Day 3:** Code and Infrastructure Audit

---

## Day 3: Code and Infrastructure Audit

### Quick Check (10 min)

- [ ] **Review Day 2 outputs** — quick scan
- [ ] **Upgrade candidates?** — anyone from baseline ready for advanced?

### Session: Code/Infrastructure Audit (75 min)

📖 Full session guide: [Code/Infrastructure Audit Session](06-code-infrastructure-audit-session.md)

#### Baseline Participants

- [ ] **Confirm they understand the codebase** ⏱️ 10 min
  - [ ] 🔀 **Can they explain the app?**
    - ✅ YES → proceed to audit
    - ❌ NO → 10 min repo understanding first (borrow from Day 2)

- [ ] **Select audit category** ⏱️ 5 min
  - [ ] Recommend: Security, Testing, or Developer Experience
  - [ ] Let them pick one they feel confident about

- [ ] **Guided audit** ⏱️ 30 min
  - [ ] Walk them through using Copilot for auditing → 📖 [Copilot Chat Guide — Auditing](guides/copilot-chat-guide.md#code-auditing)
  - [ ] Audit prompt:
    ```
    Audit this repository for security, maintainability, and deployment risks.
    Prioritize by severity. Reference specific files.
    ```
  - [ ] **Remind:** verify every Copilot finding in the actual code
  - [ ] ⏱️ Coach check at 15 min: found anything? If not, suggest a specific file.
  - [ ] 🔀 **Finding specific and evidence-backed?**
    - ✅ YES → document it
    - ❌ NO → "Can you point to the file and line? What's the actual risk?"

- [ ] **Document the finding** ⏱️ 15 min → [Audit Finding Template](../templates/audit-finding-template.md)

#### Advanced Participants

- [ ] **Multi-category audit** ⏱️ 40 min
  - [ ] Security → Infrastructure → Reliability → Observability → Cost
  - [ ] Use advanced tooling if set up: MCP for deeper analysis → 📖 [MCP Guide](guides/mcp-guide.md#using-mcp-for-audits)
  - [ ] Use Azure CLI for infrastructure inspection → 📖 [Azure Guide](guides/azure-guide.md#resource-inspection)
  - [ ] ⏱️ Check in at 20 min: review findings, challenge assumptions

- [ ] **Create audit report + risk register** ⏱️ 20 min
  - [ ] → [Audit Finding Template](../templates/audit-finding-template.md)
  - [ ] → [Risk Register Template](../templates/risk-register-template.md)

### Output Capture (20 min)

- [ ] **Quality check every finding:**
  - [ ] Has evidence (file, line, config)? ✅ / ❌
  - [ ] Has clear impact? ✅ / ❌
  - [ ] Has recommended fix? ✅ / ❌
  - [ ] 🔀 If no evidence → refine, do not accept

### Day 3 Close (15 min)

- [ ] **Definition of done:**
  - [ ] Every baseline participant: at least one evidence-backed finding ✅ / ❌
  - [ ] Every advanced participant: audit report or risk register ✅ / ❌
- [ ] **Preview Day 4:** Ticket Triage — converting findings into GitHub issues

---

## Day 4: Ticket Triage, Backlog, and Wrap-Up

### Quick Check (10 min)

- [ ] **Day 3 findings ready?**
  - [ ] 🔀 **Does every participant have at least one finding?**
    - ✅ YES → proceed to ticket creation
    - ❌ NO → use first 10 min to find one risk (compressed audit)

### Session: Ticket Triage (45 min)

📖 Full session guide: [Ticket Triage Session](07-ticket-triage-session.md)

#### Baseline Participants

- [ ] **Review and refine findings** ⏱️ 10 min
  - [ ] 🔀 **Findings actionable?**
    - ✅ YES → create ticket
    - ❌ NO (vague) → refine: add evidence, clarify impact

- [ ] **Create GitHub issue** ⏱️ 25 min → [GitHub Issue Template](../templates/github-issue-template.md)
  - [ ] Problem statement ✅
  - [ ] Evidence (file/line) ✅
  - [ ] Impact ✅
  - [ ] Suggested fix ✅
  - [ ] Acceptance criteria ✅
  - [ ] Priority + effort ✅
  - [ ] Use Copilot to help draft → 📖 [Copilot Chat Guide — Ticket Creation](guides/copilot-chat-guide.md#ticket-creation)

- [ ] **Review ticket together** ⏱️ 10 min
  - [ ] "Would an engineer who hasn't seen this code know what to do?"
  - [ ] 🔀 **Passes review?**
    - ✅ YES → submit as GitHub issue (or save as draft)
    - ❌ NO → fix gaps, resubmit

#### Advanced Participants

- [ ] **Convert all findings to tickets** ⏱️ 20 min
- [ ] **Prioritize using matrix** ⏱️ 15 min
  - [ ] High impact / low effort → 🟢 Do first
  - [ ] High impact / high effort → 🟡 Plan
  - [ ] Low impact / low effort → 🔵 Quick win
  - [ ] Low impact / high effort → ⚪ Defer
- [ ] **Create implementation plan** ⏱️ 10 min
  - [ ] Order of execution, dependencies, PR grouping

### Final Output Capture (20 min)

- [ ] **⚠️ STOP all activity — output capture mode**
  - [ ] Every participant documents their final output
  - [ ] Use [Session Output Template](../templates/session-output-template.md)

- [ ] **Quality gate — every participant must have:**
  - [ ] One documented understanding ✅ / ❌
  - [ ] One identified risk with evidence ✅ / ❌
  - [ ] One actionable GitHub issue ✅ / ❌
  - [ ] One recommended next step ✅ / ❌

- [ ] **Advanced participants additional outputs:**
  - [ ] Audit report ✅ / ❌
  - [ ] Risk register ✅ / ❌
  - [ ] Prioritized backlog ✅ / ❌

### Event Wrap-Up (25 min)

- [ ] **Summary to participants**
  - [ ] Acknowledge what was accomplished
  - [ ] Highlight best findings (anonymized if needed)
  - [ ] Emphasize: outputs are real and actionable, not just exercises
  - [ ] Use the closing script → 📖 [Coach Scripts](10-coach-scripts.md#closing-a-session)

- [ ] **Next steps for participants**
  - [ ] Follow up on tickets
  - [ ] Apply the audit/documentation practices to their own projects
  - [ ] Keep using Copilot as a reasoning tool (verify, don't trust blindly)

- [ ] **Coach final debrief**
  - [ ] Total participants diagnosed: ___
  - [ ] Baseline path: ___ | Advanced path: ___ | Blocked/fallback: ___
  - [ ] Total outputs produced: ___
  - [ ] Major blockers encountered: ___
  - [ ] What worked well: ___
  - [ ] What to improve for next event: ___

---

## Cross-Day Quick Decisions

Use these inline during any session — no need to look up the full [If/Else Playbook](08-if-else-playbook.md).

| I see this... | I do this... |
|---|---|
| Participant staring at screen > 3 min | Walk over. "What's the smallest thing we can check in 5 min?" |
| Copilot output accepted without checking | "That's a good hypothesis. Can you verify it in the code?" |
| Finding is vague | "Point me to the file and line. What specifically is the risk?" |
| Access issue | 5-minute rule → [Troubleshooting Guide](09-troubleshooting-guide.md) → fallback → [Escalation Matrix](12-escalation-matrix.md) |
| Participant finished early | Deepen (more categories), advance (next session), or peer coach |
| Running out of time | "Stop working, start documenting. Capture what you have now." |
| Participant is passive | Give a specific 5-min micro-goal with a clear deliverable |
| I don't know the answer | "Good question. Let's investigate together." → 📖 relevant guide |

---

## Tool Guide Quick Access

| Tool | Guide | When to Use |
|---|---|---|
| Copilot Chat | 📖 [Copilot Chat Guide](guides/copilot-chat-guide.md) | Every session — prompts, exploration, auditing, documentation |
| Copilot Instructions | 📖 [Copilot Instructions Guide](guides/copilot-instructions-guide.md) | Day 2 advanced — custom instructions, prompt files |
| Azure | 📖 [Azure Guide](guides/azure-guide.md) | Setup, infrastructure audit, resource inspection |
| CLI Tools | 📖 [CLI Tools Guide](guides/cli-tools-guide.md) | Throughout — gh, az, git commands |
| MCP | 📖 [MCP Guide](guides/mcp-guide.md) | Advanced path — enhanced code understanding |
| Skills | 📖 [Skills Guide](guides/skills-guide.md) | Advanced path — specialized Copilot capabilities |
| SDK | 📖 [SDK Guide](guides/sdk-guide.md) | Day 3 audit — understanding SDK code patterns |
