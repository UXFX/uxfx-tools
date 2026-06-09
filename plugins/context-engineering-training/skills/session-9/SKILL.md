---
name: session-9
description: >
  Session 9: Designing Your System. Teaches the full Claude Stack, context engineering
  principles, file system architecture, and designing for teams. Four exercises
  including the capstone full-stack run and designing a second workstream.
  Use when: STATE.md shows Session 9, or user says "session 9" or "system design".
user-invocable: true
---

# Session 9: Designing Your System

The Big Idea: You now have all the building blocks. This session zooms out — how all these pieces connect across your entire work, not just one workflow. The goal: a production capability that's greater than the sum of its parts. Context engineering at the system level.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position, student info |
| `WORKFLOW.md` | Student's workflow and everything built across S2-S8 |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position, exercises done, training completion |
| `WORKFLOW.md` | Final update with full system status |
| `learning-journal.md` | Append Session 9 takeaway at session end |

---

## Concept 1: The Claude Stack

### Frame

Everything you've learned layers together. Present the full stack:

```
Profile Preferences (account-wide defaults)
  └── Projects (persistent context per workstream)
        ├── Project Instructions (standing brief)
        ├── CLAUDE.md (file-system configuration)
        ├── Project Knowledge (reference library, RAG-enabled)
        ├── Skills (reusable expertise + voice/tone)
        ├── Skill Orchestration (state files, gates, orchestrator)
        ├── Plugins (bundled capabilities)
        ├── Connectors (external tool integrations)
        ├── Scheduled Tasks (recurring automation)
        └── Conversations
              ├── Memory (cross-session continuity)
              ├── Handoff Files (project state persistence)
              ├── Transition Prompts (session bootstrapping)
              ├── Cowork Context Layers (global + folder instructions, Cowork projects)
              ├── Sub-Agents (parallel work + context isolation)
              └── Artifacts (deliverables + live, refreshing views)
```

### Show

Point to the student's progress portal: "Open your training portal. The Claude Stack section has been building incrementally — after each session, new layers appeared. Now the full stack is visible. Every layer maps to a session you completed. You've built or used every component in this stack."

Walk through the stack connecting each layer to the student's experience:
- "Profile preferences — you wrote these in Session 0, refined in Session 2"
- "Project instructions — you wrote these in Session 3"
- "Skills — you built one in Session 7, orchestrated them in Session 8"
- "Connectors — you connected [service] in Session 6"

### Debrief

"A well-designed system means each layer handles what it's best at. The audit in Exercise 1 checks whether your system achieves this."

### Quick Check

"Pick one piece of context you've built for [your workflow] — a project instruction, a skill, a handoff file, anything. What layer of the stack does it live on, and why is that the right layer instead of one above or below it?"

🛑 **CHECKPOINT** — They should justify the placement by what that layer provides (persistence scope, loading behavior, audience). If they can't articulate why, that's a signal the concept needs reinforcement before moving on.

---

## Concept 2: Context Engineering Principles

### Frame

You've been learning these one at a time. Now see them as a single decision framework.

### Show

Present the information placement framework:

| If information... | Put it in... | Learned in... |
|---|---|---|
| Applies to every conversation | Profile preferences | Sessions 0, 2 |
| Applies to every conversation in a workstream | Project instructions or CLAUDE.md | Sessions 3, 7 |
| Applies to every Cowork task | Cowork global instructions | Session 5 |
| Applies to Cowork work in one folder | Folder instructions | Session 5 |
| Needs to be referenced but not always loaded | Project knowledge | Session 3 |
| Specific to one session | Conversation or transition prompt | Session 4 |
| Needs to persist across sessions precisely | Handoff file | Session 4 |
| Needs to persist approximately | Memory | Session 2 |

Then the design principles:
- **Design for the user who isn't you.** On Team and Enterprise plans, Projects can be shared with two permission levels: "Can use" (runs conversations in the Project) and "Can edit" (modifies instructions and knowledge). When designing for teammates, match permissions to responsibility. On Pro/Max there's no Project sharing — your sharing layer is files: CLAUDE.md, skills, and handoff files travel with a folder.
- **Start with one workflow end-to-end.** Don't build everything at once. You've done this.
- **Maintain your system.** Stale instructions and outdated skills degrade quality. Build maintenance into your workflow.

### Debrief

"These principles are your operating framework going forward. When you're unsure where to put something, check the placement table. When you're building for others, design for the user who isn't you."

### Quick Check

"You have a piece of information that applies to every session in [your workflow] but only to that workflow, not your other work. Using the placement table, where does it go and why?"

🛑 **CHECKPOINT** — The answer is project instructions or CLAUDE.md (workstream-scoped, always loaded). If they say profile preferences, remind them that's account-wide. If they say project knowledge, ask whether it should be always-loaded or on-demand.

---

## Concept 3: File System Architecture

### Frame

For sustained AI-assisted work, your directory structure IS your operating system:
- Operational files (handoffs, plans, skills, reviews) in a dedicated directory
- Content/deliverables in their own directories
- Prompts/kickoffs in their own directory
- Clear naming conventions that Claude can navigate without guidance

### Show

Look at the student's current workspace folder together. Is it organized or has it accumulated files organically? Help them see what a well-structured workspace looks like for their workflow:

```
[workflow-name]/
├── _ops/                    (handoffs, checklists, kickoffs)
├── skills/                  (SKILL.md files)
├── inputs/                  (reference material, source files)
├── outputs/                 (deliverables)
└── CLAUDE.md               (optional: project-level config)
```

### Debrief

"Structure is invisible infrastructure. When it's good, Claude navigates without guidance. When it's bad, you spend tokens explaining where things are. Exercise 1 audits your current structure."

---

## Exercise 1: Audit Your Workflow System (Throughline)

### Frame

"Take stock of everything you've built across Sessions 2-8. What's working, what's broken, what's missing?"

### Do

Walk the student through a systematic audit:

**Project instructions**
Ask: "Open your workflow Project. Read the instructions. Are they still accurate? Missing anything you keep repeating in conversations?"

**Project knowledge / workspace files**
Ask: "What reference material is loaded? Is all of it being used? Is anything loaded that's never referenced?"

**Handoff file**
Ask: "Is it current? Does it reflect the actual state of your workflow?"

**Skills**
Ask: "Does your skill chain work reliably? Which skill is weakest?"

**Connectors and scheduled tasks**
Ask: "What's connected? What's running? Are the automated outputs matching manual quality?"

**Directory structure**
Ask: "Can Claude navigate your workspace without guidance, or do you spend tokens explaining where things are?"

🛑 **CHECKPOINT** — "What's the weakest link? The part most likely to break or produce bad output?"

Help them fix the weakest link before moving on.

### Debrief

"An audit isn't a one-time event. Build it into your maintenance cycle — every few weeks, check: are the instructions current, are the skills working, is the handoff file accurate? Systems that aren't maintained degrade."

---

## Exercise 2: The Full-Stack Run (Throughline — Capstone)

### Frame

"Run your complete workflow end-to-end using everything you've built. This is the capstone."

### Do

Guide the student through the full stack:

1. Start in their fully-configured Project
2. Load the workflow skill chain
3. Pull inputs from a connected tool (if applicable)
4. Use project knowledge or workspace files for reference
5. Produce a real deliverable through the skill chain
6. Run the review skill
7. Update the handoff file

🛑 **CHECKPOINT** — At each step, note: did it work? If something broke, what type of failure was it (context, tool, scope)?

After the run, debrief: "What worked end-to-end? What broke? A workflow that runs with known limitations is more valuable than one that looks complete on paper."

### Debrief

"That's your system in action. Every component you built across 8 sessions contributed to that run. The gaps you found are your maintenance backlog — not failures, just next iterations."

Update WORKFLOW.md with final status of the full-stack run.

---

## Exercise 3: Design Your Second Workstream (Throughline — Graduation)

### Frame

"You've built one workflow. Now design a second — on paper, not built yet. This is the graduation exercise: can you architect a full system from scratch?"

### Do

Guide the student through designing a complete system:

**Step 1:** Pick the second workflow. Same criteria as Session 2: real work, at least weekly, multiple steps, involves judgment.

🛑 **CHECKPOINT** — Confirm the choice.

**Step 2:** Design the full system on paper:
1. **Project** — Name, instructions, knowledge approach
2. **Skills** — What repeatable expertise does this workstream need? How many skills? What gates?
3. **Connectors** — What external tools feed into this work?
4. **Handoff protocol** — How will sessions chain together?
5. **Scheduled tasks** — What should run automatically?
6. **Directory structure** — How will files be organized?

**Step 3:** Have Claude challenge the design: "Based on what you learned building the first workflow, where will this design break? What's over-engineered? What's missing?"

🛑 **CHECKPOINT** — "Notice how much faster this goes now that you've done it once?"

### Debrief

"You just architected a production system in a fraction of the time it took to build the first one. That's the return on investing in one workflow end-to-end: the second one is mostly pattern recognition."

---

## Exercise 4: The Handoff Test — Full System (Standalone)

### Frame

"The ultimate quality test: give your entire system to someone who didn't build it."

### Do

**Step 1:** Give the student's workflow system to another person — not just the skill, but the whole thing: directory, handoff file, skills, CLAUDE.md, connected tools. On Team/Enterprise, also share the Project itself.

**Step 2:** Start them at use-level access — on Team/Enterprise, share the Project as "Can use"; on Pro/Max, hand them the folder and have them run it in their own Claude. Can they run a session and get useful output without asking questions?

**Step 3:** Then edit-level: "Can edit" on Team/Enterprise, or on Pro/Max have them modify the skill or CLAUDE.md in the shared folder. Can they make a change without breaking anything?

🛑 **CHECKPOINT** — "Where did they get confused? Those confusion points are design failures."

If they don't have someone available, simulate: have them walk through the system as if encountering it fresh. What would confuse a newcomer?

### Debrief

"Their confusion is your roadmap. The best systems feel invisible — users get great output without thinking about the architecture. Every confusion point is an opportunity to simplify."

---

## Training Completion

### What to Remember

1. Systems beat individual prompts. The goal is a production capability.
2. Context engineering: right information at the right level of the stack.
3. File system is your operating system. Design it deliberately.
4. Design for the teammate who didn't build it. Use-level access before edit-level access.
5. Start with one workstream end-to-end. Don't boil the ocean.
6. Maintain your system. Stale instructions degrade quality.
7. The best systems feel invisible.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 9: Designing Your System** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 9 status to "Complete"
- Set all tier statuses to "Complete"
- Update WORKFLOW.md with final status
- Add instructor Notes

Invoke `portal` skill to generate the final progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Closing

This is the end of the structured training. Acknowledge the student's journey:

"You started in Session 0 with a blank profile and no system. You now have: a configured Claude environment, a purpose-built Project, handoff discipline, a workflow running in Cowork with connected tools and automation, a custom skill chain with orchestration, and a designed second workstream ready to build."

Then the forward-looking guidance:

**What's next:**
1. **Build your second workstream.** You designed it in Exercise 3 — now build it. It'll go faster.
2. **Expand your skill library.** Every time you explain a process to Claude more than twice, write a skill.
3. **Share and scale.** Train a colleague using Sessions 0-1. Set up shared Projects. Publish skills as plugins.
4. **Evolve your handoff protocol.** After 20+ sessions, you'll spot patterns. Refine the format.
5. **Stay current.** Claude's capabilities evolve. Build maintenance into your workflow.

End with: "The training is a plugin. The portal shows your journey. Both were built using the concepts you just learned. Go build."
