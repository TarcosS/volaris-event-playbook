# Coach Scripts

> Ready-to-use phrases for common coaching situations. Read these verbatim or adapt as needed.

---

## How to Use This Document

These are practical scripts you can use during live sessions. They are written in a natural tone — direct, professional, and respectful. Use them as-is or modify to fit your style. The goal is to have something ready when you need it, so you do not have to compose under pressure.

---

## Opening a Session

### Standard Opening

> "Welcome to today's session. Here is what we are going to do: I'll start by understanding where you are with these tools, and then we'll pick the right pace and depth for you. There is no single right level — some of you will go deep, some will focus on fundamentals, and all of you will leave with something concrete."

### Opening When Returning from Previous Day

> "Welcome back. Before we jump in, let me do a quick check. Did anything change since yesterday? Any blockers resolved? Any new questions? Let's make sure we are all set up before we start."

---

## Diagnosing Participant Level

### Initial Diagnosis

> "Before we decide how deep to go, I want to quickly understand your current experience. Have you worked with Azure, GitHub Copilot, or infrastructure/code auditing in a real project before?"

### Follow-Up for Vague Answers

> "Can you give me a specific example? What did you deploy? What did the Copilot session look like? I'm trying to find the right starting point for you."

### Launching the Diagnostic Task

> "Let me give you a quick task so we can find the right pace. Use Copilot to explore this repository and tell me: what does the app do, where is the entry point, what risks do you see, and what is one thing you would improve? Take about 10 minutes."

---

## Moving Someone to the Baseline Path

> "Based on what I'm hearing, I think we should start with the structured flow. We'll go step by step — understand the system, find something to improve, and document it. This is the foundation, and it's where most of the real learning happens."

### If the Participant Seems Disappointed

> "The baseline path is not a slow lane — it's the path that builds the strongest foundation. Developers who nail the fundamentals here move to advanced work much faster. And we can upgrade at any time if you are ready."

---

## Moving Someone to the Advanced Path

> "You clearly know what you are doing. Here are the audit categories, templates, and tools. Run through the codebase, document your findings, and we will review together in 20 minutes. Focus on the highest-severity items. Ask me if you need a sounding board."

### If the Participant Seems Overconfident

> "Great — let's see it in action. I'll check in after 15 minutes and we'll review your findings together. I'll be looking for specific evidence for each one."

---

## Handling Access Issues

### Initial Response

> "Let's try a couple of quick things to fix this. If we can't sort it out in a few minutes, we'll get the tech team on it and switch you to a different activity so you don't lose time."

### Switching to Fallback

> "We are going to work around this while the tech team sorts out your access. You can still do valuable work — let's [pair you with someone / switch to documentation / review the code without running it]. You will not miss anything critical."

### After Access Is Restored

> "Good news — your access is working. Let me give you a quick recap of where the group is and get you caught up in the next 5 minutes."

---

## Handling Vague Answers

### When Findings Are Vague

> "This is a good observation. Let's make it concrete. Can you point to a specific file or line of code where you see this? What exactly is the risk — what could go wrong?"

### When the Participant Says "It Needs Improvement"

> "I agree it could be better. But before we write that down, I need you to tell me specifically what is wrong, where you see it, and why it matters. 'It needs improvement' is a hypothesis, not a finding."

### When Copilot Gives a Generic Answer

> "Copilot's suggestion is a starting point. Now I need you to verify it. Does the code actually do what Copilot says? Can you find the line that confirms this?"

---

## Handling Unsupported Copilot Output

### When Copilot Suggests Something Incorrect

> "Copilot gave us a useful hypothesis. Now we need evidence from the actual code or infrastructure before we treat it as a finding. Can you verify this?"

### When the Participant Copied Copilot Verbatim

> "This is a good draft from Copilot. Now let's make it yours. Does this match what you actually see in the code? Let's verify each point and adjust where needed."

### Teaching the Verification Habit

> "Here is how I use Copilot: I ask it a question, it gives me an answer, and then I go check. Copilot is fast but not always right. The evidence is what makes our work trustworthy."

---

## Helping a Stuck Participant

### General Unsticking

> "I noticed you might be stuck. Let's reduce the scope. What is the smallest thing we can verify in the next five minutes? Just one file, one function, or one configuration."

### When They Cannot Find Risks

> "Let me give you a starting point. Open this file — [specific file]. Read through it and tell me: what does it do, and what could go wrong? You do not need to know the whole system to find a risk in one file."

### When They Do Not Know What to Write

> "Let's just start with the facts. What did you look at? What did you see? Was there anything surprising or missing? Start there — we can structure it afterward."

---

## Reducing Scope

> "Let's reduce the scope. We do not need to audit the entire system. Pick one module, one service, or one configuration file. Go deep on that one thing and produce a solid finding."

### When the Participant Is Overwhelmed

> "I know this feels like a lot. Here is what matters right now: pick one file, understand what it does, and find one thing that could be improved. That's it. One file. One finding."

### When Time Is Running Short

> "We have limited time left. Let's focus. What is the one thing you are most confident about? Let's capture that — evidence, impact, and a recommendation."

---

## Encouraging Evidence-Based Reasoning

> "I need you to show me the evidence. It's not enough to say 'this could be a problem.' Where in the code do you see it? What configuration causes it? Let's trace it."

### When the Participant Relies on Intuition

> "Your instinct might be right. But right now, we need proof. Let's find the file, the line, or the configuration that confirms or denies this. Copilot can help us look."

### When Evidence Is Ambiguous

> "The evidence does not clearly confirm this as a risk. That's OK — let's document it as an investigation item instead of a confirmed finding. That is still a valid output."

---

## Closing a Session

### Standard Close

> "Let's wrap up. Before we move on, I want to make sure everyone has captured their output. If you have a finding, document it. If you have a ticket, make sure it has evidence and acceptance criteria. No output left behind."

### Close with Preview

> "Great session. Here is what we will do tomorrow: [brief preview]. If you have unfinished work, don't worry — you will have time to complete it. For now, make sure your current output is documented."

### Final Day Close

> "This is our last session. Let's make sure everything is captured and submitted. Your outputs — documentation, findings, tickets — are the real deliverables. They do not disappear after today. Make them good enough that someone could act on them next week."

---

## Capturing Final Outputs

### Prompting Output Capture

> "Before we close, let's capture one concrete output. It can be a documentation update, an audit finding, or a GitHub issue. Whatever you have, let's finalize it now."

### When the Participant Has Nothing to Submit

> "That's OK. Let's work together for the next 5 minutes and produce something. Tell me what you observed today — what stood out? Let's turn that into a documented finding."

### Quality Check Before Submission

> "Before you submit, let me do a quick review. Does your output have: a clear problem statement, evidence from the code, impact description, and a recommended action? If yes, submit it. If not, let's fill in the gaps."
