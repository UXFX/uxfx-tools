---
name: orchestrator
description: >
  Master routing reference for Context Engineering Training. Defines session flow,
  tier gating, teaching model enforcement, and progression rules. Reference document —
  not a session manager. Start and continue skills handle session entry.
user-invocable: false
---

# Orchestrator

This is the map. Consult it at session transitions, when checking gates, or when routing to the next skill.

## Training Structure

### Tier 1: Foundation — "I get consistently useful output"

| Session | Skill | Concepts | Exercises | Gate |
|---------|-------|----------|-----------|------|
| 0 | session-0 | Training overview, profile preferences, settings | Guided setup | None |
| 1 | session-1 | Mental model shift, what AI is good/bad at, prompt anatomy, thinking vs execution | 2 (2 standalone) | None |
| 2 | session-2 | Context window, personalization stack, memory, research, models, extended thinking | 4 (2 throughline, 2 standalone) | None |
| 3 | session-3 | Projects, instructions, knowledge, styles, context budgeting | 4 (3 throughline, 1 standalone) | None |
| 4 | session-4 | Session handoff, transition prompts, two-layer system, guardrails | 4 (3 throughline, 1 standalone) | None |

### Tier 2: Builder — "I work with Claude across sessions and tools"

| Session | Skill | Concepts | Exercises | Gate |
|---------|-------|----------|-----------|------|
| 5 | session-5 | Cowork mode, approval modes, Cowork context layers, static + live artifacts, sub-agents, research ops, error recovery | 3 (2 throughline, 1 standalone) | None |
| 6 | session-6 | Connectors, plugins, scheduled tasks, Chrome extension, batch processing | 4 (2 throughline, 2 standalone) | None |
| 7 | session-7 | Skills, decision framework, SKILL.md anatomy, CLAUDE.md | 4 (3 throughline, 1 standalone) | None |

### Tier 3: Architect — "I design reusable AI systems"

| Session | Skill | Concepts | Exercises | Gate |
|---------|-------|----------|-----------|------|
| 8 | session-8 | State files, gates, orchestrators, plugins, review pipelines | 4 (3 throughline, 1 standalone) | None |
| 9 | session-9 | Full stack, context engineering principles, system design, handoff | 4 (3 throughline, 1 standalone) | None |

## Session Flow

Each session follows this internal flow:

```
1. Read STATE.md → determine position
2. Read WORKFLOW.md → load student's workflow context
3. Load agent (agents/instructor.md)
4. For each concept in the session:
   a. Frame — brief concept intro
   b. Show — live demonstration
   c. Do — guided exercise (if applicable)
   d. Debrief — check understanding, bridge to next
   e. Quick Check — comprehension question (between concepts only, not before exercises)
5. Update STATE.md with completion status
6. Bridge to next session
```

## Teaching Model Enforcement

- **One concept at a time.** Never present two concepts in a single message.
- **Frame → Show → Do → Debrief** for every concept that has an exercise.
- **Frame → Show → Debrief** for concepts without a dedicated exercise.
- **Quick Check between concepts.** After each concept's Debrief, ask a comprehension question before starting the next concept. Skip Quick Checks before exercises (the exercise itself tests understanding). Each session skill provides specific Quick Check questions.
- **Student questions answered inline.** When a student asks a question mid-session, answer briefly and pick up where you left off. Don't defer or park questions.
- **Pause after each phase.** Wait for the student before proceeding.
- **Throughline exercises** use the student's workflow from WORKFLOW.md.
- **Standalone exercises** use isolated examples.

## Progression Rules

1. Sessions are sequential. Session N requires Session N-1 complete (except Session 0 can be skipped by experienced users).
2. A session is complete when all exercises are done OR the student explicitly skips remaining exercises.
3. Skipped exercises are noted in STATE.md so they can be revisited.
4. The student can revisit any completed session at any time.

## State File Updates

At session start:
- Set Position: Session, Concept (first concept), Phase (frame), Tier

During session:
- Update Concept and Phase as student progresses
- Update Exercises Done count after each exercise

At session end:
- Set session Status to Complete
- Update Exercises Done with final count
- Clear Position concept/phase
- Add instructor Notes if relevant
- **Append to `learning-journal.md`** — personalized session takeaway (key moments, what worked, what to practice, principles demonstrated). Under 30 lines per session.
- **Invoke `portal` skill** to regenerate the progress portal

## Portal Updates

The `portal` skill generates `training-portal.html` — a single-file interactive dashboard showing the student's progress, workflow evolution, Claude Stack visualization, and concept reference.

**Trigger points:**
- After every session completion (mandatory)
- On student request ("show portal", "my progress")
- After `start` skill completes initial setup

The portal builds incrementally. The Claude Stack diagram reveals new layers as the student learns them. The concept reference only shows concepts from completed sessions. The meta-teaching footer evolves after Sessions 5 and 8.

## Skill Dependencies

```
start → session-0 → session-1 → session-2 → session-3 → session-4 → session-5 → session-6 → session-7 → session-8 → session-9
                ↘          ↘           ↘           ↘                             ↘           ↘           ↘           ↘           ↘           ↘
              portal     portal      portal      portal                        portal      portal      portal      portal      portal      portal
```

Utility skills available at any time:
- `status` — Show training progress
- `continue` — Resume from last position
- `portal` — Regenerate progress portal
