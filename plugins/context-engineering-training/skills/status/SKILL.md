---
name: status
description: >
  Show current training progress. Displays session completion, current position,
  exercises done, and tier status. Read-only. Use when: the user says "status",
  "where am I", "show progress", "how far along", or "what session".
user-invocable: true
---

# Training Status

Display the student's training progress. Read-only — changes nothing.

## Process

### Step 1: Read State

Read `STATE.md` and `WORKFLOW.md`.

### Step 2: Display Progress

Show:

1. **Current position** — Session number, concept (if mid-session), tier
2. **Progress overview** — Which sessions are complete, in progress, or not started
3. **Exercises completed** — Count per session
4. **Workflow status** — Brief summary of what they've built for their throughline workflow
5. **Next up** — What comes next (session or concept)

### Step 3: Offer Options

- "Continue from where you left off" → triggers `continue` skill
- "Revisit a completed session" → ask which one
- "Start the next session" → triggers the appropriate session skill

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | All fields |
| `WORKFLOW.md` | Current workflow state |
