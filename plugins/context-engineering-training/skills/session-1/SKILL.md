---
name: session-1
description: >
  Session 1: How to Think About AI. Teaches the mental model shift (thinking partner, not search engine),
  what AI is good and bad at, prompt anatomy (Role, Task, Context, Constraints), and separating
  thinking from execution. Two standalone exercises. Use when: STATE.md shows Session 1, or user
  says "session 1" or "how to think about AI".
user-invocable: true
---

# Session 1: How to Think About AI

The Big Idea: Most people treat AI like a search engine or command line. The real shift: stop asking questions, start giving context. Claude is a thinking partner — the quality of what you get back depends entirely on how well you brief it.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position, student info |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position, exercises done, notes |
| `learning-journal.md` | Append Session 1 takeaway at session end |

---

## Concept 1: The Mental Model Shift — Thinking Partner, Not Search Engine

### Frame

Set up the foundational reframe. Most people's instinct when AI produces bad output is to blame the AI. The productive instinct is to ask: what context was I not providing?

A search engine needs a keyword. A thinking partner needs to understand your situation, your goal, and your standards. Claude is like a capable colleague who just walked into the room — smart, well-read, eager to help, but with zero context about your situation.

### Show

Demonstrate the shift with a quick example from the student's work domain (ask what they do if you don't already know):

1. Frame a task the way you'd type it into a search engine: "best practices for [their domain topic]"
2. Show the output — it'll be generic, surface-level, could-apply-to-anyone.
3. Now reframe the same need as a briefing to a thinking partner: "I'm a [role] at [type of company]. I'm dealing with [specific situation]. My audience is [who]. I need to [specific outcome]. Here's what I've already tried..."
4. Show how the output fundamentally changes — not just better words, but different thinking.

Point out: "I didn't use any tricks. I just told you more about the situation. That's the shift — context over cleverness."

### Debrief

"When output disappoints you, the question isn't 'Is the AI dumb?' It's 'What did I assume it knew?' That reframe is the foundation of everything in this training."

### Quick Check

"Think about the last time you used Claude (or any AI) and the output wasn't great. Was the problem the AI's ability, or was it missing context about your situation?"

🛑 **CHECKPOINT** — Wait for the student's answer. Any answer that identifies missing context is correct. If they genuinely think the AI was the problem, probe: "What would a smart colleague have needed to know to give you a better answer?"

---

## Concept 2: What AI Is Good At (and Bad At)

### Frame

Setting realistic expectations prevents two failure modes: over-reliance (trusting everything Claude produces) and dismissal (giving up when the first output is mediocre). Understanding the boundary helps you know when to lean in and when to verify.

### Show

Walk through both sides concretely:

**Good at:** Drafting, brainstorming, restructuring, summarizing, expanding, translating between formats, applying consistent style, generating variations, thinking through problems with you, researching and synthesizing information, processing repetitive tasks at scale.

**Bad at:** Knowing things about your company or situation it hasn't been told, verifying its own accuracy, replacing domain expertise you haven't provided, reading your mind about what "good" looks like for your specific context, maintaining perfect precision on specific facts and numbers.

Then land the critical habit: **Evaluate before you trust.** Claude can be confidently wrong. It will produce well-structured, authoritative-sounding output based on incorrect assumptions or stale data — without flagging the uncertainty. Give a brief example: "If I asked Claude about your company's Q1 revenue without providing any data, it would either refuse or guess. But if I asked it to analyze 'industry trends,' it might mix current facts with outdated training data and present both with equal confidence."

### Debrief

"You are always the expert, the editor, and the quality gate. AI drafts; you decide. This isn't a limitation — it's how the partnership works. The best users aren't the ones who get perfect output on the first try. They're the ones who evaluate effectively and refine quickly."

### Quick Check

"Can you think of a task from your work where you'd trust AI output with minimal checking, versus one where you'd need to verify carefully? What makes the difference?"

🛑 **CHECKPOINT** — Wait for the student's answer. They should distinguish between tasks where Claude has enough context to be reliable (formatting, restructuring, brainstorming) versus tasks requiring domain-specific accuracy (facts, figures, company-specific claims). If they say "I'd always check everything," that's fine — acknowledge the caution and point out that some tasks genuinely need less scrutiny than others.

---

## Concept 3: Prompt Anatomy — The Four Parts

### Frame

When output disappoints, it's almost always because the prompt was missing one of four things. Prompt anatomy gives you a diagnostic checklist — not a rigid template, but a way to figure out what's missing.

### Show

Walk through the four parts with examples adapted to the student's domain:

1. **Role** — Who should Claude be for this task? A role sets expertise, tone, and perspective. "You are a senior [relevant role] who specializes in [relevant area]..." changes the output fundamentally.

2. **Task** — What specifically do you need? Vague tasks produce vague output. "Write a summary" vs. "Write a one-page summary of the three key risks, structured as a briefing for [audience]."

3. **Context** — What does Claude need to know about your situation? Background, audience, what's already been done, what matters most. "I'm preparing this for [who]. They already know [X] but need to understand [Y]."

4. **Constraints** — What are the guardrails? What to avoid, limits, rules, tone. "Keep it under 300 words. Don't use jargon. Lead with the recommendation, not the analysis."

Then show the diagnostic use: "When your output is too generic, you're probably missing Context. When it's the wrong format or length, you're missing Constraints. When it sounds wrong, you're missing Role. When it answers the wrong question, you're missing a clear Task."

### Debrief

"You don't always need all four. A quick brainstorming request might just need a Task. But when output disappoints, run through the checklist — Role, Task, Context, Constraints — and you'll almost always find the gap."

### Quick Check

"If Claude wrote you something that was well-written but felt like it could have been written for anyone — not specifically for your situation — which part of prompt anatomy was probably missing?"

🛑 **CHECKPOINT** — Wait for the student's answer. Context is the right answer. If they say Role, that's partially right — probe further. The key insight is that Context is what makes output specific to your situation.

---

## Exercise 1: The Bad Prompt / Good Prompt Comparison (Standalone)

### Frame

"Let's make the difference concrete on something from your actual work."

### Do

**Step 1:** Ask the student to think of a real task from their work — something they might ask Claude to help with.

If the student struggles, offer 2-3 suggestions based on what you know about their role and work. Examples: "Based on what you've told me, you could try: writing a status update for your team, drafting an outline for a client presentation, or summarizing notes from a recent meeting. Or pick something completely different — whatever feels real."

🛑 **CHECKPOINT** — Wait for their task.

**Step 2:** Have them write a bare prompt — just the task, no role, no context, no constraints. Something they might naturally type. Run it and look at the output together.

**Step 3:** Now rewrite it using all four parts of prompt anatomy. Walk them through it:
- "Who should Claude be for this?" (Role)
- "What specifically do you need?" (Task — make it precise)
- "What does Claude need to know about your situation?" (Context)
- "What are the boundaries?" (Constraints)

Run the structured prompt.

**Step 4:** Compare the two outputs explicitly. Point to specific differences: "Notice how the first version [specific issue]. The second version [specific improvement] because you gave it [which part of prompt anatomy]."

Ask: "Which of the four parts made the biggest difference for your task?"

🛑 **CHECKPOINT** — Wait for their assessment.

### Debrief

"The difference isn't about writing more words. It's about giving Claude the information it needs to think the way an expert would. That's context engineering in its simplest form — and it scales all the way up to the systems you'll build by Session 9."

---

## Concept 4: Separate Thinking from Execution

### Frame

One of the most powerful patterns in working with AI: don't ask it to do the thing. Ask it to *think about* the thing first. Then do it.

This mirrors how experts actually work. A beginner sits down and writes the report. An expert asks who the audience is, clarifies the goal, identifies the key tension, proposes a structure, gets feedback — and *then* writes.

### Show

Demonstrate with a concrete example:

**One-stage approach (beginner):** "Write a project update email for my team about [topic]."

**Two-stage approach (expert):**
- Stage 1: "I need to send a project update to my team about [topic]. Before writing it, help me think through: What's the most important thing they need to know? What might they be worried about? What's the right tone — reassuring, urgent, or matter-of-fact? What should I definitely NOT include?"
- Stage 2: "Good — now write the email based on what we discussed."

Show both outputs. The two-stage version will be noticeably more targeted because bad assumptions got caught in the thinking stage.

### Debrief

"When you separate thinking from execution, you catch bad assumptions before they become bad output. This pattern becomes more important as tasks get more complex. By Session 5, you'll be using it routinely in Cowork mode — research first, then produce."

### Quick Check

"Think about a complex task from your work. If you asked Claude to just do it in one shot, what assumption might it get wrong? How would a thinking-first stage catch that?"

🛑 **CHECKPOINT** — Wait for the student's answer. Any answer that identifies a specific assumption that could go wrong is good. The insight: the thinking stage is where you align on approach before committing to output.

---

## Exercise 2: Think First, Then Produce (Standalone)

### Frame

"Let's practice the two-stage pattern on a real task."

### Do

**Step 1:** Ask the student to pick a task from their work that has some complexity — not a simple lookup, but something where approach matters (a report, a plan, an analysis, a communication).

If the student struggles to pick something, offer suggestions based on what you know: "Something like: planning an approach for [thing they mentioned], writing a recommendation for [their domain], or structuring a briefing on [relevant topic]. Anything where the approach matters as much as the output."

🛑 **CHECKPOINT** — Wait for their task.

**Step 2 (Thinking stage):** Have them ask Claude to think through the approach before producing anything. Guide them: "Ask Claude to consider the audience, the goal, the structure, potential pitfalls — whatever matters for this specific task."

🛑 **CHECKPOINT** — Let the thinking conversation happen. Student and Claude should go back and forth until the approach feels right.

**Step 3 (Execution stage):** Now have them ask Claude to produce the output based on the thinking they just did.

**Step 4 (Comparison):** Ask: "How does this compare to what you'd have gotten from a single 'just do it' prompt? What did the thinking stage catch or improve?"

🛑 **CHECKPOINT** — Wait for their assessment.

### Debrief

"The two-stage pattern takes a bit longer, but it produces better output because you're catching bad assumptions before they compound. As you get faster with it, the thinking stage gets shorter — you learn which tasks need it and which don't."

---

## Session Completion

### What to Remember

Present these as a summary, not a lecture:

1. Context over cleverness. A simple prompt with great context beats a clever prompt with none.
2. AI is a thinking partner, not a search engine. Brief it like a smart colleague who just walked into the room.
3. Evaluate before you trust. Claude can be confidently wrong — you are always the quality gate.
4. Prompt anatomy (Role, Task, Context, Constraints) is your diagnostic checklist when output disappoints.
5. Separate thinking from execution. Think first, produce second — catch bad assumptions early.

### Append to Learning Journal

Create or append to `learning-journal.md` in the student's workspace. Include:

1. **Session 1: How to Think About AI** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific prompts and outputs from Exercises 1–2.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas where the student's instincts still default to the old mental model. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts (not abstract — tied to their actual exercises).

Keep it concise — under 30 lines. This is a personalized takeaway, not a transcript.

### Update State

Update STATE.md:
- Set Session 1 status to "Complete"
- Set Exercises Done: count of completed exercises (out of 2)
- Add any instructor Notes about what clicked vs. what was hard

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 2

"Session 1 gave you the mental models — how to think about working with AI. Session 2 teaches you how Claude specifically works: the context window, the personalization stack, memory, research, and models. You'll also choose the real workflow you'll build across the rest of the training."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-2`
- If they want to break → "When you're ready to continue: open the Cowork tab, select this training folder, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
