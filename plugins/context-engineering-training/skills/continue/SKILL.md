---
name: continue
description: >
  Resume the Context Engineering Training from where the last session left off.
  Reads STATE.md for position, loads instructor agent, and picks up at the
  documented session and concept. Use when: the user says "continue", "resume",
  "pick up where I left off", "keep going", or "next".
user-invocable: true
---

# Continue Training

Resume from the student's last documented position.

## Process

### Step 0: Environment Gate — Cowork Required

Before anything else, read `agents/instructor.md` from the plugin bundle. If you cannot reach it, you are in an environment that doesn't serve the full plugin (Claude Chat does this — skills load, templates and agents don't). Stop and tell the student:

> "Training resumes in Cowork, not in a regular chat. Open Claude Desktop, switch to the Cowork tab, select your training folder, and say 'continue training' there."

Do not attempt a partial resume in Chat.

### Step 1: Read State

Read `STATE.md` from the student's workspace. Extract:
- Current Session number
- Current Concept and Phase (if mid-session)
- Exercises completed in the current session
- Any instructor Notes

Read `WORKFLOW.md` to reload the student's workflow context.

### Step 2: Orient the Student

Briefly remind the student where they are:
- Which session they're in
- What concept/exercise they were working on (if mid-session)
- What they did last (one sentence)

Don't re-teach anything. Just orient and confirm they're ready to continue.

🛑 **CHECKPOINT** — "Ready to pick up from [position]?"

### Step 3: Resume

Route to the appropriate session skill at the correct position.
- If mid-session: resume at the documented concept/phase
- If between sessions: start the next session skill
- If a session is complete and no next session: congratulate and suggest review

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Position, progress, notes |
| `WORKFLOW.md` | Student's workflow context |
