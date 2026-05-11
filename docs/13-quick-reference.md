# Quick Reference

> One-page cheat sheet for live event use. Keep this open at all times.

---

## Diagnosis Questions (Ask First)

1. Have you deployed to Azure before?
2. Have you used GitHub Actions?
3. Do you actively use Copilot?
4. Have you used AI-assisted coding for a real task?
5. Do you have IaC experience (Bicep/Terraform/ARM)?
6. What do you want to leave with today?

---

## Level Classification

| Level | Key Signal | Path |
|---|---|---|
| **Beginner** | Limited Azure/GitHub, struggles with navigation | Baseline (guided) |
| **Intermediate** | Has experience but weak on evidence/auditing | Baseline (accelerated) |
| **Advanced** | Reasons from evidence, verifies Copilot, identifies real risks | Advanced |
| **Blocked** | Cannot access tools | Fallback → troubleshoot or escalate |
| **Unclear** | Vague answers | Run diagnostic task |

---

## Core Decision Rule

> **IF** they can explain the system, use Copilot with evidence, and reason about risks → **Advanced path**  
> **ELSE** → **Baseline path**

---

## Coaching Loop

```
1. Diagnose → 2. Select path → 3. Guide → 4. Validate evidence → 5. Capture output
```

---

## Key If/Else Rules

| Situation | Action |
|---|---|
| Level unclear | Run diagnostic task |
| Stuck > 3 min | Reduce scope: "smallest thing in 5 min" |
| Vague findings | "Point to the file/line" |
| Trusts Copilot blindly | "Verify in the code" |
| Access blocked | 5-minute rule → fallback → escalate |
| Finishes early | Deepen, advance, or peer coach |
| Running out of time | Stop activity → capture outputs immediately |
| Coach doesn't know | "Let's investigate together" |
| Passive participant | Assign specific micro-goal |
| Too many findings | "Pick your top 3 by severity" |

---

## Coach Scripts (Short Version)

**Diagnosis:**  
> "Have you worked with Azure, Copilot, or code auditing in a real project?"

**Baseline assignment:**  
> "Let's start with the structured flow — step by step."

**Advanced assignment:**  
> "Here are the categories and templates. Self-direct, check in at 20 min."

**Verification:**  
> "Copilot gave us a hypothesis. Where is the evidence in the code?"

**Scope reduction:**  
> "What is the smallest thing we can verify in 5 minutes?"

**Output capture:**  
> "Let's capture one concrete output before we move on."

**Access issue:**  
> "Let's fix this quickly. If not in 5 min, we'll switch to a different activity."

---

## Troubleshooting Shortcuts

| Issue | Quick Fix |
|---|---|
| Azure login | Incognito browser, `az login --use-device-code` |
| Wrong tenant | Switch directory in portal, `az login --tenant <id>` |
| No subscription | Check subscription filter bar |
| Copilot not working | Check license at `github.com/settings/copilot`, reinstall extension |
| Repo 404 | Verify URL, check org membership, correct account |
| Network blocked | Disconnect VPN, try mobile hotspot |
| IDE broken | `code --disable-extensions`, or use GitHub web editor (press `.`) |

---

## Output Checklist

Every output must have:

- [ ] **Clear problem statement** — what is wrong or missing
- [ ] **Evidence** — file, line, config, or behavior
- [ ] **Impact** — what happens if not addressed
- [ ] **Recommended action** — what should be done
- [ ] **Acceptance criteria** — how to verify the fix (for tickets)

---

## Definition of Done (Per Day)

| Day | Done When |
|---|---|
| **Day 1** | All participants diagnosed, access confirmed or fallback assigned |
| **Day 2** | Every participant has one documentation artifact |
| **Day 3** | Every participant has one evidence-backed finding |
| **Day 4** | Every participant has one actionable GitHub issue |

---

## Templates Quick Links

- [Audit Finding](../templates/audit-finding-template.md)
- [GitHub Issue](../templates/github-issue-template.md)
- [Session Output](../templates/session-output-template.md)
- [Participant Diagnosis](../templates/participant-diagnosis-sheet.md)
- [Risk Register](../templates/risk-register-template.md)

---

## Escalation Quick Rules

| Type | Coach handles? | Escalate to |
|---|---|---|
| Copilot prompt/methodology | ✅ Yes | — |
| Azure access/provisioning | Try 5 min | Event tech team |
| GitHub org/license | No | Org admin |
| Network/firewall | Try hotspot | Event tech team |
| Security finding | Document only | Org admin (private) |
