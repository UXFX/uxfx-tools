---
name: session-4
description: >
  Session 4: Session Management & Handoff Discipline. Teaches why sessions end,
  handoff files, transition prompts, the two-layer system, context budgeting across
  sessions, and guardrails. Four exercises including writing the workflow's first
  handoff file. Use when: STATE.md shows Session 4,
  or user says "session 4" or "handoff".
user-invocable: true
---

# Session 4: Session Management & Handoff Discipline

The Big Idea: A single conversation is not the unit of work — a project is. Projects span days, weeks, months. The skill that separates one-off Claude users from sustained productivity is handoff discipline: maintaining continuity across sessions so every new conversation picks up where the last one left off. This is where most people fail. The solution is a system, not a feature.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position, student info |
| `WORKFLOW.md` | Student's workflow and what's been built so far |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position, exercises done, notes |
| `WORKFLOW.md` | Update "What I've Built So Far" with handoff system |
| `learning-journal.md` | Append Session 4 takeaway at session end |

---

## Concept 1: Why Sessions End

### Frame

In Session 3, you built a Project that persists context across conversations. But conversations themselves are finite. Sessions end for three reasons, and recognizing which one is happening is the first skill:

1. **Context exhaustion** — The window fills up and quality degrades. You felt this in Session 3's overload experiment.
2. **Topic drift** — The conversation wanders and becomes unfocused. Claude starts mixing up different threads.
3. **Natural breakpoint** — The task is done, or you've reached a logical stopping point.

### Show

Point to this training itself as an example: "This plugin manages session boundaries for you — each session is a self-contained unit with a start and end. But when you're doing real work with your workflow, YOU have to recognize when a session should end. The training won't always be there to structure it."

Describe what each failure mode looks like in practice:
- Context exhaustion: "Claude starts giving generic responses, forgetting instructions you gave earlier, or repeating itself."
- Topic drift: "You started working on research but now you're also editing a document and planning next steps — the conversation has three threads and Claude is handling none of them well."
- Natural breakpoint: "The deliverable is done. You've reached a decision. The research phase is complete and production is next."

### Debrief

"The meta-skill: when output quality drops or something feels off, stop and diagnose before continuing. Pushing through a broken session wastes more time than starting a clean one."

### Quick Check

"You're working on [your workflow] and Claude starts giving vague, generic responses that ignore instructions you gave 15 messages ago. Which of the three session-ending reasons is this, and what should you do?"

🛑 **CHECKPOINT** — Good answer identifies context exhaustion (not topic drift or natural breakpoint) and says to stop, write a handoff, and start fresh. If they say "topic drift," clarify that drift is about multiple threads competing, not quality degradation from a full window.

---

## Concept 2: The Session Handoff File

### Frame

When a session ends — for any of the three reasons — what happens to the context? Without a system, it's gone. The next conversation starts fresh. You've been compensating for this with memory (unreliable, as Session 2 showed — and standalone Cowork sessions, where you'll work from Session 5 on, don't retain memory between tasks at all) or by manually re-explaining everything (wasteful).

A handoff file solves this. It's a structured document that captures the state of a project at the end of a session. It lives in your file system — not in Claude's memory — and contains: session number and date, what was completed, what decisions were made, what's next, and any open questions or blockers.

Every session starts by reading this file. Every session ends by updating it. This is the connective tissue between conversations.

### Show

Show the student what a handoff file looks like. Use the training itself as an example — describe what a handoff file for their training progress would contain:

```
## Session Handoff — [Student's Workflow Name]
Updated: [today's date]
Session: 4

### Completed
- Chose workflow: [their workflow] (S2)
- Built workflow Project with instructions and knowledge (S3)
- Refined profile preferences (S0, S2)

### Decisions Made
- Project knowledge approach: [Option A or B] (S3)
- Workflow description: [one line] (S2)

### Next Session
- Write handoff file for the workflow itself
- Write first transition prompt
- Design two-layer system

### Open Questions
- [Any unresolved questions from S3]
```

Point out the principles: "Notice it's state, not narrative. Under 40 lines. Every fact is traceable to a session. The 'Next Session' section scopes what comes next so Claude doesn't have to guess."

### Debrief

"The handoff file is the cheapest, highest-impact technique in this entire training. It takes 5 minutes to write and saves you 20 minutes of re-explaining next session. You'll write your first one in Exercise 1."

### Quick Check

"If your handoff file for [your workflow] just said 'Worked on the project, made good progress, will continue next time' — what's wrong with it?"

🛑 **CHECKPOINT** — Good answer identifies that it's narrative, not state. It lacks specifics: no session number, no concrete decisions, no traceable facts, no scoped 'Next Session.' If they focus only on length, redirect to the principle that handoff files capture state, not stories.

---

## Concept 3: Transition Prompts — Bootstrapping a Fresh Conversation

### Frame

In Session 2, you learned that a fresh conversation starts with an empty context window. The handoff file captures state. The transition prompt delivers it — a compressed brief designed to fill the context window with exactly the right context in a single message.

Structure:
- **CONTEXT** — What project, what files, what is NOT this project
- **WHAT JUST HAPPENED** — Summary of the previous session
- **TASK** — Numbered steps for this session
- **GUARDRAILS** — What to avoid, scope boundaries, known pitfalls

### Show

Show the student a real transition prompt. Use the training as the example — if they were starting a fresh conversation to continue their workflow work, what would the transition prompt look like?

```
CONTEXT: I'm building [workflow name] as a Claude workflow.
My project is in [Project name]. Reference files are in [folder].
This is my workflow project — do not reference training exercises.

WHAT JUST HAPPENED: In my last session, I built the Project with
instructions covering [role, constraints, domain context] and added
[2-3 knowledge files]. I tested the output and [what they learned
from the A/B comparison].

TASK:
1. Write a handoff file capturing current state
2. Test the handoff by starting a fresh conversation
3. Design the two-layer system for ongoing work

GUARDRAILS:
- Do not modify my project instructions — those are stable
- Do not create files I didn't ask for
- This session covers handoff discipline only — do not start on
  Cowork features (that's Session 5)
```

Walk through why each section matters: "CONTEXT tells Claude what's in scope. WHAT JUST HAPPENED prevents re-explaining. TASK prevents scope drift. GUARDRAILS prevent the three failure modes we just discussed."

### Debrief

"Transition prompts solve a specific problem: Claude has no reliable memory of previous sessions. The transition prompt gives it everything it needs in a single message. You'll write and test one in Exercise 2."

### Quick Check

"You're writing a transition prompt for [your workflow]. You include CONTEXT, WHAT JUST HAPPENED, and TASK — but skip GUARDRAILS. What's the most likely thing that goes wrong in that session?"

🛑 **CHECKPOINT** — Good answer connects to one of the three failure modes: scope drift (Claude starts working on something outside this session's scope), cross-project contamination, or tool misuse. If they can't answer, point back to the guardrails examples — the prompt without boundaries is an invitation for Claude to improvise.

---

## Concept 4: The Two-Layer System

### Frame

For multi-session projects, there's a tension: you need Claude to know the full project status, but loading everything into every session overloads the context window. The two-layer system resolves this:

1. **Master checklist** (~60 lines) — Overall project status, read every session. Lightweight.
2. **Session-specific kickoff prompt** — Loads only what this one session needs. Detailed but scoped.

### Show

Connect to the student's workflow: "Your workflow is going to span Sessions 4 through 9. By Session 7, there will be a lot of accumulated state — the Project, handoff history, skills, connectors. If you load all of that into every session, you're spending half your context window on backstory. The master checklist keeps the backstory lean. The kickoff prompt focuses on today's work."

Show what a master checklist looks like — abbreviated, using their workflow:

```
# [Workflow Name] — Master Checklist
Updated: [date]

## Status: Session 4 of training

## Built
- [x] Workflow identified (S2)
- [x] Project created with instructions (S3)
- [x] Knowledge files loaded: [list] (S3)
- [ ] Handoff file written (S4)
- [ ] Transition prompt tested (S4)
- [ ] Two-layer system designed (S4)
- [ ] Moved to Cowork (S5)
...

## Key Decisions
- Knowledge approach: [A or B]
- [Other decisions]

## Known Issues
- [Any open items]
```

### Debrief

"The master checklist is your 60-line project brain. The kickoff prompt is your session-specific focus. Together they prevent the trap of loading your entire project history into every conversation. You'll design both in Exercise 4."

### Quick Check

"By Session 7, your workflow has accumulated a lot of history. Why not just paste the entire handoff file history into every new session instead of using a master checklist?"

🛑 **CHECKPOINT** — Good answer connects to context budgeting: the full history would consume too much of the context window, leaving less room for actual work. The master checklist keeps backstory lean (~60 lines) while the kickoff prompt focuses on today's task. If they mention token limits but not the two-layer split, prompt them on how the layers divide the responsibility.

---

## Concept 5: Guardrails in Transition Prompts

### Frame

Claude can go off-script — invoking tools you didn't ask for, touching files from other projects, or expanding scope beyond what this session should cover. You may have already experienced this. Explicit guardrails prevent it.

### Show

Give concrete examples relevant to the student:
- "Do NOT touch files outside of [directory]" — prevents Claude from wandering into other projects
- "This session covers [X] only. Do not start on [Y]." — prevents scope creep
- "Do not invoke [tool/skill] — that's for a different project." — prevents cross-contamination

Then connect to their experience: "In Session 3, if Claude had started editing your profile preferences while working on your workflow Project, that would have been scope leakage. Guardrails make the boundaries explicit."

### Debrief

"Guardrails are cheap insurance. A few lines in your transition prompt prevent the most common session failure mode — scope drift. They're especially important when you have multiple projects running simultaneously."

---

## Exercise 1: Write Your Workflow's First Handoff File (Throughline)

### Frame

"You've done real work on your workflow across Sessions 2–3. Let's capture that state so it survives between sessions."

### Do

**Step 1:** Guide the student to write a SESSION-HANDOFF.md in their workspace folder. Walk through each section:

- **Session number and date**
- **Completed:** What they built in Sessions 2-3 (workflow choice, Project, instructions, knowledge)
- **Decisions made:** Which knowledge approach (A or B), any workflow refinements from the thinking partner exercise
- **Next session:** What comes next (Cowork migration in Session 5)
- **Open questions:** Anything unresolved

🛑 **CHECKPOINT** — Review the handoff file together. Challenge it: "Is this lean enough? Could Claude pick up from this without any additional explanation? Is anything missing that you'd have to re-explain?"

Target: under 40 lines. If it's longer, help them trim.

### Debrief

"That's your connective tissue. Every session going forward starts by reading this file and ends by updating it. It's 5 minutes of work that saves 20 minutes of re-explaining."

Update WORKFLOW.md: add to "What I've Built So Far" — Session 4: Created handoff file for workflow continuity.

---

## Exercise 2: Write a Transition Prompt (Throughline)

### Frame

"Now let's test whether the handoff file actually works. Write a transition prompt that could bootstrap a fresh conversation about your workflow."

### Do

**Step 1:** Help the student write a transition prompt using the four-section structure: CONTEXT, WHAT JUST HAPPENED, TASK, GUARDRAILS. Pull content from the handoff file they just wrote.

🛑 **CHECKPOINT** — Review the transition prompt. Check: Is the CONTEXT section specific enough? Does WHAT JUST HAPPENED capture the essential state? Are GUARDRAILS covering the most likely failure modes?

**Step 2: Evaluate the prompt together.** Since we can only have one conversation open at a time, we won't test it live right now. Instead, review it critically:
- Is the CONTEXT section specific enough that Claude would know exactly what project this is?
- Does WHAT JUST HAPPENED capture the essential state without bloating the context?
- Would the GUARDRAILS prevent the most likely failure modes?
- If you handed this to someone else and they pasted it into a fresh chat, would Claude behave correctly?

Save the transition prompt to a file in the student's workspace. They'll test it for real when they start their next workflow session after training.

**Step 3:** Refine based on the review. Trim anything that's narrative rather than state. Tighten guardrails to specific behaviors.

### Debrief

"You've built the full handoff system: do work → write handoff → compose transition prompt. After this session, test it for real — open your workflow Project, start a fresh chat, paste the transition prompt, and see if Claude picks up seamlessly. That's the system that makes multi-session projects work."

---

## Exercise 3: The Context Overload Breakpoint (Standalone)

### Frame

"In Session 3, you overloaded a Project deliberately. This time, overload a session — push through without handing off and see when quality breaks."

### Do

**Step 1:** Start a session and keep working on multiple tasks without ending. Pile on: different topics, switching between tasks, asking Claude to recall earlier instructions.

**Step 2:** Watch for the signs: generic responses, forgotten specifics, loss of coherence. Note when it happens and estimate how much context was loaded.

**Step 3:** When it breaks, stop. Don't push through. Write a quick handoff note of the current state and start a fresh conversation. Notice the quality difference.

🛑 **CHECKPOINT** — "When did you notice the degradation? What were the signs?"

### Debrief

"Now you have calibration. You know roughly how much a session can hold before quality degrades. That's your intuition for when to hand off. Better to hand off one prompt too early than one prompt too late."

---

## Exercise 4: Design Your Workflow's Two-Layer System (Throughline)

### Frame

"Your workflow will span Sessions 5–9. Let's set up the system that keeps it manageable."

### Do

**Step 1:** Help the student write a master checklist for their workflow. Track:
- Overall build status across the training
- What's been completed (with session references)
- Key decisions
- Known issues
- Target: under 60 lines.

🛑 **CHECKPOINT** — Review the checklist. Is it lean enough to read every session without consuming too much context?

**Step 2:** Help them write a kickoff prompt specifically for Session 5 — scoped to Cowork work only. It should reference the master checklist but not duplicate it.

**Step 3:** Test the pair: could Claude start Session 5 with just these two files and have everything it needs? If not, what's missing?

### Debrief

"You now have a two-layer system: lean checklist for continuity, focused kickoff for each session. This is the same pattern used in professional multi-session projects. As the training progresses, you'll update the checklist and write new kickoffs — the system scales."

Update WORKFLOW.md: add — Session 4: Designed two-layer system (master checklist + session kickoffs).

---

## Session Completion

### What to Remember

1. The handoff file is the connective tissue between sessions. No file, no continuity.
2. Transition prompts bootstrap fresh conversations with full context in a single message.
3. The two-layer system (master checklist + session kickoffs) prevents context overload in long-running projects.
4. Guardrails in transition prompts prevent scope leakage and off-script behavior.
5. Claude's memory is not reliable enough for project state. Use files.
6. Know when to end a session: context full, topic drifting, or natural breakpoint.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 4: Session Management & Handoff Discipline** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 4 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 5

"You've built the continuity system: handoff files, transition prompts, a two-layer system for long-running projects. The next question: what if Claude could do more than chat? Session 5 moves your workflow into Cowork mode — Claude working with your files, producing real deliverables, running sub-agents, and operating in your actual environment. The handoff discipline you just built becomes even more important when Claude is an operator, not just an advisor."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-5`
- If they want to break → "When you're ready to continue: go to your training project, start a new chat, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
