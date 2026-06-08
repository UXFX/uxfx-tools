---
name: session-8
description: >
  Session 8: Skill Orchestration & Plugins. Teaches multi-skill composition,
  state files, gates, orchestrators, plugin building, and review pipelines.
  Four exercises including decomposing the workflow into phases. Use when:
  STATE.md shows Session 8, or user says "session 8" or "orchestration".
user-invocable: true
---

# Session 8: Skill Orchestration & Plugins

The Big Idea: Real workflows are rarely one skill's job. A content pipeline has stages — research, draft, review, publish. A discovery process has phases — research, synthesis, validation. The power move: designing skills that hand off to each other through shared state, so Claude runs a multi-step process that spans sessions.

Production-grade plugins use this same pattern at serious scale — dozens of skills organized into phases, coordinated by a shared state file, with gates preventing you from skipping ahead. This training is the pattern at teaching scale: 10 session skills, one state file, one orchestrator. You don't need dozens of skills. You need three concepts: a state file, gates, and an orchestrator.

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
| `WORKFLOW.md` | Update "What I've Built So Far" with orchestration system |
| `learning-journal.md` | Append Session 8 takeaway at session end |

---

## Concept 1: Why One Skill Isn't Enough

### Frame

In Session 7, you wrote a skill for your workflow. Look at it honestly: does it try to handle distinct phases in one pass? Most real workflows have phases that require different thinking. A research phase needs breadth and skepticism. A production phase needs focus and craft. A review phase needs distance and rigor. Cramming all of that into one skill produces a bloated file that Claude follows unevenly.

The fix: split into skills that each handle one phase well, then connect them.

### Show

Point to this training as the example: "This training has 10 session skills, not one giant skill. Each session focuses on one type of learning. They hand off to each other through the state file. That's orchestration — and it's the same pattern you're about to apply to your workflow."

Then analyze the student's skill from Session 7: "Your SKILL.md has [N] stages. Are those stages really the same type of thinking? Or does stage 1 require research while stage 3 requires editing? If they're different types of thinking, they're candidates for separate skills."

### Debrief

"One skill per phase. Each skill does one type of thinking well. The connection between them is what we build next."

### Quick Check

"Look at the skill you wrote in Session 7. Can you identify two stages that require fundamentally different types of thinking? What makes them different?"

🛑 **CHECKPOINT** — They should name a concrete difference in thinking mode (e.g., research vs. synthesis, gathering vs. evaluating). If they say the stages are "just different steps," push on whether Claude needs a different mindset for each.

---

## Concept 2: The State File — Your Shared Clipboard

### Frame

When skills hand off to each other, they need a shared record of where the project is. A state file tracks: which skill just ran, what it produced, what comes next, and any decisions that affect downstream work. Every skill reads the state file at start and updates it at end.

This is the same pattern as the handoff files from Session 4 — but now it's skills handing off to skills, not just you handing off to yourself.

### Show

Show a concrete state file for the student's workflow:

```
Current phase: [First phase of their workflow]
Current skill: [skill name]
Status: Complete
Output: [what it produced]
Next skill: [next phase]
Decisions: [any decisions made]
```

Then point to the training's own state file: "Your STATE.md tracks which session you're in, what exercises you've done, and what's next. That's exactly the same pattern — a state file managing skill-to-skill handoffs."

### Debrief

"The state file is plain markdown. No code, no database. Claude reads it, does work, updates it. Simple and transparent — you can open the file and see exactly where the project stands."

### Quick Check

"If your first skill finishes and hands off to the second, what's the minimum information the state file needs to carry so the second skill can pick up without losing context?"

🛑 **CHECKPOINT** — They should mention at least what was produced and what comes next. If they only say "which skill ran," ask what happens if the second skill doesn't know what the first skill decided or created.

---

## Concept 3: Gates — Preventing Shortcuts

### Frame

A gate is a precondition that must be met before the next skill can run. "Don't start synthesis until at least 3 research sources exist." "Don't start review until the draft is complete."

Why this matters: without gates, Claude will cheerfully skip steps. It will synthesize research it never did, review drafts that don't exist, or jump to conclusions without intermediate work. Gates encode "do this in order" into a system that has no built-in sense of sequence.

### Show

Point to the training's own gating: "This training uses gates — each session checks STATE.md to confirm the previous session is complete before proceeding. Without that check, the system would let you skip ahead and miss foundational concepts."

Then design gates for the student's workflow: "If your workflow has a research phase and a production phase, the gate between them might be: 'at least [N] sources gathered and reviewed.' What would be the minimum prerequisite for your production phase to start?"

### Debrief

"Gates are just rules in each skill's instructions. The skill checks whether the prerequisite exists before doing its work. Simple, but critical — Exercise 4 shows you what happens without them."

### Quick Check

"What's one gate you'd put between two phases of [your workflow]? What specific evidence should exist before the second phase starts?"

🛑 **CHECKPOINT** — A good answer names a concrete, verifiable prerequisite (e.g., "3 sources gathered," "draft exists," "data validated"). If they give something vague like "phase 1 is done," ask what Claude would actually check for.

---

## Concept 4: The Orchestrator — A Map, Not a Manager

### Frame

When you have multiple skills that chain together, you need a document that describes the flow: which skills exist, what order they run in, what each produces, and what gates govern transitions. This is the orchestrator — and critically, it's a reference document, not a program.

Claude reads it to know where it is in the process and what comes next. It's the posted map on the wall, not a manager telling people what to do.

### Show

Show what a simple orchestrator looks like for the student's workflow:

```
Phase 1: [Research/Input/Gather]
  Skills: [skill-a] → [skill-b]
  Gate: [prerequisite]

Phase 2: [Production/Processing]
  Skills: [skill-c]
  Gate: Phase 1 complete

Phase 3: [Review/Output]
  Skills: [skill-d]
  Gate: Draft exists
```

Then point to the training's orchestrator: "This training has an orchestrator that maps all 10 sessions, their dependencies, the tier gating, and the portal triggers. It's a markdown file that Claude reads — not code that runs."

### Debrief

"The orchestrator is the simplest component and the most important. Without it, Claude doesn't know where it is in the process. With it, Claude can navigate a multi-step workflow across sessions."

### Quick Check

"What's the difference between an orchestrator and a state file? If you had to explain it to a colleague in one sentence each, what would you say?"

🛑 **CHECKPOINT** — The key distinction: the state file tracks where things ARE right now, the orchestrator describes where things CAN GO. If they conflate the two, ask which one changes every session and which one stays the same.

---

## Concept 5: Building a Plugin

### Frame

In Session 6, you installed plugins others built. Now you can build your own. A plugin bundles skills, connectors, and tools into an installable package. The structure: a plugin manifest (plugin.json), skill folders, and associated resources.

When your multi-skill workflow works reliably, packaging it as a plugin lets you distribute it — to teammates, your team, or the broader ecosystem.

### Show

Point to this training: "This training is a plugin. It has a plugin.json manifest, skill folders for each session, an agent persona, templates, and an orchestrator. That's the structure. Your workflow could follow the same pattern."

### Debrief

"Build reliably first, package second. A plugin is a distribution format, not a quality improvement. Make sure the skills work before you worry about packaging."

### Quick Check

"At what point would it make sense to turn [your workflow] into a plugin instead of keeping it as a set of skills? What would have to be true?"

🛑 **CHECKPOINT** — They should mention distribution or reuse by others as the trigger. If they say "when it's good enough," clarify that plugins are about packaging for sharing, not about quality — skills that work but stay personal don't need to be plugins.

---

## Concept 6: Tiered Review Pipelines

### Frame

Review pipelines are a practical example of skill orchestration. A production skill creates output, then a separate review skill evaluates it, keeping creation and critique in different contexts (remember sub-agents from Session 5).

For quality-critical work, design tiers:
- **Tier A** — Full review: structural pass + coherence pass across two sessions
- **Tier B** — Standard review: single-session structural and content check
- **Tier C** — Light audit: pre-flight checks, structure validation only

The tier depends on how important the output is.

### Show

Connect to the student's workflow: "Your workflow produces [output]. How important is quality? If it goes to clients, maybe Tier A. If it's internal, maybe Tier B. If it's routine, Tier C. The review skill you build in Exercise 3 can be calibrated to the right tier."

### Debrief

"Separating production from review is a design pattern: different skills, different contexts, different thinking. It catches things a single all-in-one skill misses."

---

## Exercise 1: Decompose Your Workflow Into Phases (Throughline)

### Frame

"Look at the single skill you built in Session 7. Let's split it into phases."

### Do

**Step 1:** Together, identify 2-3 natural phases in the student's workflow — steps that require different thinking, different inputs, or different quality criteria.

🛑 **CHECKPOINT** — Confirm the phases.

**Step 2:** For each phase, write a focused SKILL.md. Keep each one tight — role, stages, gates, constraints scoped to that phase only.

**Step 3:** Review the set: do the phases cover the full workflow? Are there gaps? Overlaps?

### Debrief

"You now have a skill chain instead of a monolith. Each skill is simpler, more focused, and easier to test independently."

Update WORKFLOW.md: Session 8: Decomposed workflow into [N] phase skills.

---

## Exercise 2: Build Your State File and Orchestrator (Throughline)

### Frame

"Your skills need a way to hand off to each other. Build the coordination layer."

### Do

**Step 1:** Create a STATE.md for the student's workflow. Track: current phase, current skill, status, output, next skill, decisions.

**Step 2:** Write an orchestrator document: skill order, what each produces, what gates govern transitions.

**Step 3:** Test the handoff: run the first skill, check the state file, run the second skill. Does Claude pick up where the first skill left off?

🛑 **CHECKPOINT** — Does the handoff work? Any gaps in the state file?

### Debrief

"You now have the coordination layer. State file for persistence, orchestrator for navigation. These two files turn independent skills into a connected system."

Update WORKFLOW.md: Session 8: Built state file and orchestrator for skill chain.

---

## Exercise 3: Build a Review Pipeline (Throughline)

### Frame

"Your workflow now produces output through multiple skills. Add a quality layer."

### Do

**Step 1:** Write a review skill that evaluates the final deliverable against the quality criteria from Session 7.

**Step 2:** Run it as a sub-agent (Session 5 concept) so the review stays independent of the production context.

**Step 3:** Evaluate: does the review catch things the student would catch manually? Is it calibrated to the right tier (A/B/C)?

🛑 **CHECKPOINT** — Is the review useful? Does it catch real issues?

### Debrief

"Production and review in separate skills, separate contexts. The review skill doesn't know what shortcuts the production skill took — it just evaluates the output. That independence is the value."

---

## Exercise 4: The Orchestration Stress Test (Standalone)

### Frame

"Let's see what happens when the system breaks."

### Do

**Step 1:** Skip a gate — run the synthesis/production skill before the research/input skill completes. See what Claude produces.

**Step 2:** Then run it correctly, in order, with all gates satisfied. Compare the output.

🛑 **CHECKPOINT** — "What's the difference? What did the gated version catch that the ungated version missed?"

### Debrief

"Without gates, Claude produces confident output from thin air. With gates, each skill builds on verified work from the previous skill. The quality difference is the argument for orchestration."

---

## Session Completion

### What to Remember

1. One skill per phase. Split workflows by type of thinking.
2. State file: shared clipboard between skills. Plain markdown, read at start, updated at end.
3. Gates prevent Claude from skipping steps. Without them, Claude synthesizes research it never did.
4. Orchestrator: reference map, not a program. Describes the flow.
5. Plugins package multi-skill systems. Build reliably first, package second.
6. Review pipelines: separate creation from critique using sub-agents and different skills.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 8: Skill Orchestration & Plugins** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 8 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 9

"You now have all the building blocks. Session 9 zooms out — how does everything connect across your entire work, not just one workflow? You'll audit your system, run the capstone end-to-end, design your second workflow, and hand the whole thing off to someone else. It's the system design session."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-9`
- If they want to break → "When you're ready to continue: open the Cowork tab, select this training folder, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
