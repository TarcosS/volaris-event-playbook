---
title: "If/Else Playbook"
layout: default
nav_order: 8
---

> The core operational decision guide for coaches. Use this document during live sessions to handle any situation quickly and consistently.

---

## How to Use This Document

This is your primary reference during the event. Each scenario describes a situation you may encounter, what signals to look for, what to do, what to say, what to fall back to, and what output to expect. When in doubt, find the closest scenario and follow it.

**Quick navigation:** Each scenario has a consistent format: Signal → Coach Action → Suggested Script → Fallback → Expected Output.

---

## Scenario 1: Participant Level Is Unclear

**Signal:**  
The participant gives vague or inconsistent answers to diagnostic questions. You cannot confidently classify them as beginner, intermediate, or advanced.

**Coach Action:**  
Run the diagnostic task. Ask them to use Copilot to inspect the repository and answer four questions (see [Participant Diagnosis](03-participant-diagnosis.md)). Observe their process, not just their answers.

**Suggested Script:**  
> "Let me give you a quick task so we can find the right pace. Use Copilot to explore this repository and tell me: what does the app do, where is the entry point, what risks do you see, and what is one thing you would improve?"

**Fallback:**  
If the diagnostic task does not clarify their level, start them on the baseline path. You can always upgrade later. Starting too advanced is riskier than starting too simple.

**Expected Output:**  
A completed diagnostic task that allows classification. Record the result in the [Participant Diagnosis Sheet](../templates/participant-diagnosis-sheet.md).

---

## Scenario 2: Participant Is a Beginner

**Signal:**  
The participant has limited experience with Azure, GitHub, or Copilot. They struggle with codebase navigation and need step-by-step guidance. They may not know what a "risk" or "audit finding" means in this context.

**Coach Action:**  
Use the baseline path for every session. Provide structured, step-by-step guidance. Pair them with an intermediate participant if possible. Set micro-goals (5–10 minute tasks). Celebrate small wins.

**Suggested Script:**  
> "We are going to start with the fundamentals and build from there. First, let's make sure you can navigate the repository and understand what the application does. From there, we'll find one thing to improve."

**Fallback:**  
If they struggle even on the baseline path, narrow the scope further. Instead of "find a risk," try "find one file that looks important and tell me what it does." Build confidence before introducing audit concepts.

**Expected Output:**  
Baseline outputs: one documented understanding, one identified risk (even if simple), one GitHub issue (coached through the process).

---

## Scenario 3: Participant Is Intermediate

**Signal:**  
The participant has some Azure/GitHub experience but limited audit or documentation skills. They can use Copilot but may not verify its output. They can navigate code but struggle to identify meaningful risks versus cosmetic issues.

**Coach Action:**  
Use the baseline path with faster pacing. Skip step-by-step explanations they do not need. Focus coaching on evidence quality and risk identification. Challenge them to go deeper than surface observations.

**Suggested Script:**  
> "You clearly have a solid foundation. Let's move at a faster pace and focus on the quality of what we find. I want to see specific evidence for every finding — not just what Copilot suggests, but what the code actually shows."

**Fallback:**  
If they plateau, switch to a specific category they have experience with (e.g., security if they have security background). Give them a focused target.

**Expected Output:**  
Baseline outputs plus an attempt at one advanced output (e.g., a more detailed audit finding or a second GitHub issue).

---

## Scenario 4: Participant Is Advanced

**Signal:**  
The participant explains systems confidently with specific references. They use Copilot as a reasoning tool and actively verify output. They identify risks from code and configuration evidence. They have IaC experience.

**Coach Action:**  
Move them to the advanced path immediately. Provide the audit category list and let them self-direct. Check in periodically (every 15–20 minutes) to review findings and challenge assumptions. Do not over-coach — stay out of their way.

**Suggested Script:**  
> "You know what you're doing. Here are the audit categories and templates. Run through the codebase and infrastructure, document your findings, and we'll review together in 20 minutes. Focus on the highest-severity items first."

**Fallback:**  
If they finish early, have them help coach others (peer coaching) or tackle a second repository. They can also create implementation plans or hardening recommendations.

**Expected Output:**  
Audit report, risk register, prioritized issue backlog, and optionally a PR implementation plan or hardening recommendations.

---

## Scenario 5: Participant Is Passive

**Signal:**  
The participant is physically present but not engaging. They are not asking questions, not using their computer, or are waiting to be told exactly what to do at every step.

**Coach Action:**  
Give them a specific, small, achievable task with a clear deliverable. Do not give them time to drift. Set a 5-minute micro-goal and check back.

**Suggested Script:**  
> "Here is what I need from you in the next 5 minutes: open this file, read it, and tell me what the application does based on what you see. Just the facts from the code."

**Fallback:**  
If they remain passive, pair them with an engaged participant. Give the passive participant a specific role: note-taker, ticket writer, or reviewer. Being accountable to a peer often activates engagement.

**Expected Output:**  
At least one small deliverable per session, even if it is simpler than the baseline target.

---

## Scenario 6: Participant Is Overconfident

**Signal:**  
The participant claims extensive experience but produces shallow work. They skip steps, declare findings without evidence, or dismiss coaching guidance. They may say "I already know this" frequently.

**Coach Action:**  
Do not confront. Instead, challenge with specifics. Ask for evidence. Ask probing questions that reveal whether their confidence is backed by depth.

**Suggested Script:**  
> "That sounds right. Can you show me where in the code or configuration that is? I want to make sure our finding is strong enough to survive review."

**Fallback:**  
If they produce genuinely strong work, acknowledge it and move them to the advanced path. If their work is shallow, keep asking for evidence. The evidence requirement levels the playing field without creating conflict.

**Expected Output:**  
Evidence-backed findings that match their claimed skill level — or a recalibration to the correct path.

---

## Scenario 7: Participant Trusts Copilot Without Verification

**Signal:**  
The participant accepts Copilot's answer without checking the repository, code, logs, or configuration. They copy Copilot's output directly into their findings or tickets.

**Coach Action:**  
Ask them to find evidence before treating Copilot's output as a conclusion. Frame it as strengthening their work, not correcting them.

**Suggested Script:**  
> "Copilot gave us a useful hypothesis. Now we need evidence from the actual code or infrastructure before we treat it as a finding. Can you find the file or config that confirms this?"

**Fallback:**  
If they cannot find evidence, downgrade the item to a question or investigation task rather than a confirmed finding. This teaches the verification habit without discarding useful leads.

**Expected Output:**  
An evidence-backed finding or a clearly scoped investigation ticket. The participant learns to use Copilot as a starting point, not an endpoint.

---

## Scenario 8: Participant Is Blocked by Azure Access

**Signal:**  
The participant cannot log in to Azure, is assigned to the wrong tenant, has no subscription access, lacks resource group permissions, or cannot deploy resources. MFA may be causing issues.

**Coach Action:**  
Apply the 5-minute rule. Try the quick fixes from the [Troubleshooting Guide](09-troubleshooting-guide.md). If not resolved in 5 minutes, escalate to the event technical team using the [Escalation Matrix](12-escalation-matrix.md) and switch the participant to a fallback path.

**Suggested Script:**  
> "Let's try a couple of quick things to fix this. If we can't sort it out in a few minutes, we'll get the tech team on it and switch you to a different activity so you don't lose time."

**Fallback:**  
Switch to: read/analyze mode (review code without deploying), pairing mode, documentation mode, or architecture review. See [Troubleshooting Guide](09-troubleshooting-guide.md) for the full fallback path list.

**Expected Output:**  
Either resolved access or a productive fallback activity. The participant should not sit idle.

---

## Scenario 9: Participant Is Blocked by GitHub or Copilot Access

**Signal:**  
GitHub login fails, Copilot license is not active, Copilot extension is not working, or organization policy blocks Copilot. Repository access may be denied.

**Coach Action:**  
Apply the 5-minute rule. Check license status, extension installation, and organization settings. If not resolved quickly, escalate using the [Escalation Matrix](12-escalation-matrix.md) and switch to fallback.

**Suggested Script:**  
> "Let's check a few things — your Copilot license, the extension, and your organization settings. If we can't get it working quickly, we'll partner you up so you can keep moving."

**Fallback:**  
Without Copilot: participant can still do manual code review, documentation, and ticket writing. Without GitHub: pair them with someone who has access and give them the reviewer/writer role.

**Expected Output:**  
Either resolved access or productive participation through fallback activities.

---

## Scenario 10: Participant Cannot Access the Repository

**Signal:**  
The participant gets a 404 or permission denied when trying to access the assigned repository. They may have the wrong URL or lack organization membership.

**Coach Action:**  
Verify the URL. Check if they are logged in to the correct GitHub account. Check organization membership. If it is a permissions issue, escalate to the org admin.

**Suggested Script:**  
> "Let's verify you're on the right account and have the right URL. If it's a permissions issue, I'll get the admin to add you."

**Fallback:**  
While waiting for access, have the participant work on documentation, review another participant's findings, or do architecture review on a different (public) repository.

**Expected Output:**  
Resolved access or an alternative productive activity.

---

## Scenario 11: Participant Has Read-Only Permissions

**Signal:**  
The participant can view the repository but cannot push commits, create issues, or open PRs. They can read but not write.

**Coach Action:**  
Determine if write access is needed immediately. For audit and documentation sessions, read access may be sufficient — they can draft outputs locally or in a separate document.

**Suggested Script:**  
> "Read-only access is actually fine for what we're doing right now. You can inspect, audit, and draft your findings locally. When write access is fixed, you can submit everything at once."

**Fallback:**  
Draft all outputs in local files or a personal repository. Submit them later when access is resolved. The learning is not blocked by write permissions.

**Expected Output:**  
Drafted outputs ready to submit once permissions are fixed.

---

## Scenario 12: Participant Has No Deployment Permissions

**Signal:**  
The participant can view infrastructure configurations but cannot deploy or modify Azure resources. This may limit infrastructure audit activities.

**Coach Action:**  
Focus on review and analysis rather than deployment. The participant can still audit IaC templates, review pipeline configurations, and document findings — all without deployment permissions.

**Suggested Script:**  
> "We don't need deployment access for the audit. You can review the infrastructure configurations, Bicep/Terraform files, and pipeline definitions as code. The findings are the same — you just document what you observe."

**Fallback:**  
If the participant's only goal was hands-on deployment experience, pivot to architecture review and deployment planning. They can create a deployment plan as an output.

**Expected Output:**  
Audit findings based on configuration review rather than live deployment testing.

---

## Scenario 13: Participant Finishes Early

**Signal:**  
The participant completes their assigned activity ahead of schedule and has produced quality outputs.

**Coach Action:**  
Verify the quality of their outputs first. If quality is solid, offer progression options. Do not let them sit idle.

**Suggested Script:**  
> "Great work. Let's review what you have, and if it's solid, I have some options for you: you could go deeper on another audit category, help a neighbor, or start on the next session's activities."

**Fallback:**  
Options for early finishers:
1. Deepen existing work (additional audit categories, more detailed tickets)
2. Start next day's activities early
3. Peer coaching — help another participant (with your guidance)
4. Tackle a second repository or service
5. Create implementation plans or hardening recommendations

**Expected Output:**  
Additional outputs beyond the baseline or advanced target. Peer coaching creates multiplier effects.

---

## Scenario 14: Participant Gets Stuck for More Than 3 Minutes

**Signal:**  
The participant is visibly stuck — staring at the screen, switching tabs aimlessly, or rereading the same section without progress. They have not asked for help.

**Coach Action:**  
Intervene proactively. Do not wait for them to ask. Reduce the scope of what they are trying to do.

**Suggested Script:**  
> "I noticed you might be stuck. Let's reduce the scope. What is the smallest thing we can verify in the next five minutes? Just one file, one function, or one configuration."

**Fallback:**  
If scope reduction does not help, switch to a different activity. If they are stuck on auditing, try documentation. If stuck on documentation, try a simpler exploratory task. Movement is better than stagnation.

**Expected Output:**  
Progress on a reduced-scope task. Momentum restored.

---

## Scenario 15: Participant Produces Vague Findings

**Signal:**  
The participant submits findings like "security could be better," "code needs refactoring," or "documentation is incomplete" without evidence or specifics.

**Coach Action:**  
Do not reject the finding. Refine it. Ask probing questions to extract specifics.

**Suggested Script:**  
> "This is a good observation. Let's make it stronger. Can you point to a specific file or line where you see this? What exactly is the risk? What could go wrong?"

**Fallback:**  
If they genuinely cannot find evidence, convert the finding to an investigation ticket: "Investigate whether [vague concern] is a real risk in [area]. Check [specific files or configurations]."

**Expected Output:**  
A refined, evidence-backed finding or a well-scoped investigation ticket.

---

## Scenario 16: Participant Creates Too Many Findings

**Signal:**  
The participant has a long list of findings (10+) but most are shallow. They are going for volume over quality.

**Coach Action:**  
Apply the prioritization matrix. Force them to select their top 3 and make those excellent.

**Suggested Script:**  
> "You have found a lot. That is good for awareness. Now let's pick the top 3 by severity and impact. I want each of those to be strong enough that an engineer would act on it immediately."

**Fallback:**  
If they cannot prioritize, help them by asking: "If you could only fix one thing before the next deployment, which one would it be and why?"

**Expected Output:**  
A prioritized set of 3–5 high-quality findings with evidence and impact, rather than 15 shallow observations.

---

## Scenario 17: Group Is Moving Too Slowly

**Signal:**  
Most participants in the room are behind the expected pace. Activities that should take 30 minutes are taking an hour. The schedule is at risk.

**Coach Action:**  
Reduce scope for the entire group. Cut optional activities. Focus on the minimum viable output for each session.

**Suggested Script:**  
> "Let's adjust our pace. For this session, I want everyone to focus on producing one high-quality output. Let's skip [optional activity] and focus on [core activity]. Quality over quantity."

**Fallback:**  
If the group is stuck on a prerequisite (e.g., most people cannot access tools), pause the session and address the blocker for everyone at once. A group demo may be faster than individual troubleshooting.

**Expected Output:**  
At least the minimum baseline output per participant, even if the advanced activities are skipped.

---

## Scenario 18: Group Is Moving Too Fast

**Signal:**  
Most participants are finishing activities well ahead of schedule. The room has energy and capacity for more depth.

**Coach Action:**  
Increase challenge. Add advanced activities. Introduce deeper audit categories or cross-participant review.

**Suggested Script:**  
> "You are all ahead of schedule — that is excellent. Let's use this time to go deeper. Pick an additional audit category, review another team's findings, or start building the prioritized backlog now."

**Fallback:**  
Do not artificially slow them down. Always have a "next challenge" ready. Pull forward activities from the next day if appropriate.

**Expected Output:**  
Additional outputs beyond the standard target. The group produces advanced-level work.

---

## Scenario 19: Session Is Running Out of Time

**Signal:**  
There are 10–15 minutes left and participants have not captured their outputs. The session is at risk of ending without tangible deliverables.

**Coach Action:**  
Stop all activity and switch to output capture mode immediately. Whatever they have is what they submit.

**Suggested Script:**  
> "We have 10 minutes left. Let's stop working and start capturing. Whatever you have right now, document it using the template. An incomplete but documented finding is better than an undocumented complete one."

**Fallback:**  
If participants have nothing to document, do a rapid-fire round: each person states their main observation verbally, and the coach helps them write it as a one-paragraph finding with whatever evidence is available.

**Expected Output:**  
At least one documented output per participant, even if it is incomplete. Nothing is lost.

---

## Scenario 20: Coach Does Not Know the Answer Immediately

**Signal:**  
A participant asks a technical question the coach cannot answer on the spot. This will happen — especially with niche Azure configurations, unusual Copilot behavior, or specific codebase patterns.

**Coach Action:**  
Be honest. Do not guess. Model the investigation behavior you want participants to use.

**Suggested Script:**  
> "Good question — I'm not sure about that specific detail. Let's investigate together. Let me use Copilot to check, and then we'll verify against the docs or the code."

**Fallback:**  
If investigation takes too long, park the question: "Let's capture this as an investigation item and come back to it. I don't want to block your progress on this." Follow up during a break or after the session.

**Expected Output:**  
Either a verified answer or a parked investigation item. The coach maintains credibility by modeling honest, evidence-based behavior.

---

## Scenario Quick-Reference Table

| # | Scenario | Key Action |
|---|---|---|
| 1 | Level unclear | Run diagnostic task |
| 2 | Beginner | Baseline path, step-by-step |
| 3 | Intermediate | Baseline accelerated, challenge for evidence |
| 4 | Advanced | Advanced path, self-directed |
| 5 | Passive | Specific micro-goal, pair if needed |
| 6 | Overconfident | Ask for evidence, challenge with specifics |
| 7 | Trusts Copilot blindly | Require evidence verification |
| 8 | Azure access blocked | 5-minute rule, escalate, fallback |
| 9 | GitHub/Copilot blocked | 5-minute rule, escalate, fallback |
| 10 | Repo access denied | Verify URL/account, escalate |
| 11 | Read-only permissions | Draft locally, submit later |
| 12 | No deploy permissions | Audit as code review, no deployment needed |
| 13 | Finishes early | Deepen, advance, or peer coach |
| 14 | Stuck > 3 min | Reduce scope, intervene proactively |
| 15 | Vague findings | Probe for specifics and evidence |
| 16 | Too many findings | Prioritize top 3 |
| 17 | Group too slow | Reduce scope for all |
| 18 | Group too fast | Increase challenge |
| 19 | Running out of time | Stop and capture outputs |
| 20 | Coach doesn't know | Investigate together, park if needed |
