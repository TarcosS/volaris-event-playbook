# Coaching Principles

> The operating rules that guide every coaching decision during the event.

---

## How to Use This Document

These principles are not aspirational guidelines. They are operational rules. When you are unsure what to do during a session, return to this list and apply the most relevant principle.

---

## Principle 1: Diagnose Before Teaching

**Never assume a participant's skill level.** Always run a diagnostic step before selecting a coaching path. A senior developer may be unfamiliar with Copilot. A junior developer may have deep Azure experience. Assumptions waste time and frustrate participants.

**In practice:**
- Use the [Participant Diagnosis](03-participant-diagnosis.md) flow at the start of every session
- Ask the diagnostic questions before giving any instructions
- Observe what the participant does, not just what they say

---

## Principle 2: Evidence Before Conclusions

**Every finding must be backed by evidence from the code, configuration, infrastructure, or logs.** Do not accept claims based on intuition, general knowledge, or Copilot output alone.

**In practice:**
- Ask: "Where in the code or configuration do you see this?"
- Ask: "Can you show me the evidence?"
- If there is no evidence, the finding is a hypothesis, not a conclusion

---

## Principle 3: No Evidence, No Ticket

**Do not create a GitHub issue unless the underlying finding has evidence.** Vague tickets create noise. Every issue must reference specific code, configuration, or behavior.

**In practice:**
- Before a participant creates an issue, verify they can point to the evidence
- If evidence is weak, help them refine the finding first
- A well-scoped investigation ticket is acceptable if the evidence suggests a problem but cannot confirm it

---

## Principle 4: Use Copilot as a Reasoning Assistant, Not an Authority

**Copilot generates useful hypotheses, but it is not a source of truth.** Participants must verify Copilot's output against the actual codebase, configuration, and infrastructure.

**In practice:**
- When a participant says "Copilot told me X," ask: "Can you verify that in the code?"
- Model this behavior yourself — always cross-reference Copilot suggestions
- Frame Copilot as a tool that accelerates investigation, not one that replaces it
- See [Scenario: Participant trusts Copilot without verification](08-if-else-playbook.md#scenario-7-participant-trusts-copilot-without-verification)

---

## Principle 5: Prefer Small Concrete Outputs Over Broad Discussion

**A single documented finding is worth more than an hour of general discussion.** Push participants toward producing something tangible as early as possible.

**In practice:**
- Redirect broad conversations: "This is interesting — let's capture one specific finding from it."
- Use output templates to give structure: [Output Templates](11-output-templates.md)
- Set micro-goals: "In the next 10 minutes, let's produce one audit finding with evidence."

---

## Principle 6: Reduce Scope When Blocked

**When a participant is stuck, reduce the scope of the task.** Do not let them spin on a large, undefined problem. Narrow the focus to something they can accomplish in the next 5–10 minutes.

**In practice:**
- Ask: "What is the smallest thing we can verify right now?"
- Offer a simpler version of the current task
- Switch from creating to analyzing if the creation task is too complex
- See [Scenario: Participant gets stuck for more than 3 minutes](08-if-else-playbook.md#scenario-14-participant-gets-stuck-for-more-than-3-minutes)

---

## Principle 7: Escalate Environment Problems Early

**Do not spend more than 5 minutes troubleshooting an access or environment issue.** If it cannot be resolved quickly, escalate to the event technical team and switch the participant to an alternative path.

**In practice:**
- Follow the [Troubleshooting Guide](09-troubleshooting-guide.md) for quick resolution steps
- If the issue persists, use the [Escalation Matrix](12-escalation-matrix.md)
- Switch the participant to read/analyze mode, pairing mode, or documentation mode immediately
- Never let access issues take a participant out of the learning flow entirely

---

## Principle 8: Do Not Let Access Issues Remove Someone from the Learning Flow

**Every participant should be engaged at all times, even if their tools are not working.** There is always an alternative activity that provides value.

**In practice:**
- Switch to pairing mode: the participant works alongside someone with working access
- Switch to coach demo mode: the coach demonstrates while the participant observes and takes notes
- Switch to documentation mode: the participant documents findings, creates templates, or writes tickets based on observed work
- Switch to architecture review: the participant reviews and documents system design on paper or a whiteboard
- See [Troubleshooting Guide](09-troubleshooting-guide.md) for the complete fallback path list

---

## Principle 9: Pairing and Demo Mode Are Valid Fallback Paths

**Pairing a blocked participant with a working one is a legitimate coaching strategy**, not a failure. Demo mode — where the coach drives while the participant observes — is also a valid approach when tools are broken.

**In practice:**
- Frame pairing positively: "Let's team up so we can keep moving while we sort out your access."
- In demo mode, narrate your reasoning: "I'm looking at this file because…"
- Ensure the blocked participant has a specific role: note-taker, ticket writer, reviewer

---

## Principle 10: Adapt the Path, Not the Standard

**Every participant should produce evidence-backed outputs, regardless of their path.** The baseline path is simpler, not lower quality. The advanced path is deeper, not better. Both paths demand evidence and concrete outputs.

**In practice:**
- Baseline participants produce fewer outputs, but each output meets the same evidence standard
- Advanced participants produce more outputs across more categories
- Never accept "good enough" findings that lack evidence, regardless of the participant's level

---

## Principles Summary

| # | Principle | One-Line Rule |
|---|---|---|
| 1 | Diagnose before teaching | Ask first, teach second |
| 2 | Evidence before conclusions | Show me the code |
| 3 | No evidence, no ticket | Hypotheses are not issues |
| 4 | Copilot is an assistant, not an authority | Verify everything |
| 5 | Small concrete outputs over discussion | Ship something tangible |
| 6 | Reduce scope when blocked | Go smaller, not broader |
| 7 | Escalate environment problems early | 5-minute rule |
| 8 | Keep everyone in the learning flow | No one sits idle |
| 9 | Pairing and demo mode are valid | Alternative paths work |
| 10 | Adapt the path, not the standard | Evidence required always |
