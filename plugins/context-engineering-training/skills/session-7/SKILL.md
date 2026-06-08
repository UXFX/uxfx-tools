---
name: session-7
description: >
  Session 7: Building Skills. Teaches what skills are, the decision framework
  (Chat→Project→Skill→Plugin), creating skills through conversation ("Turn into
  skill"), SKILL.md anatomy for deeper control, and CLAUDE.md. Four exercises
  including extracting expertise and creating the workflow's skill file via
  conversation or manual writing. Use when: STATE.md shows Session 7, or user
  says "session 7" or "building skills".
user-invocable: true
---

# Session 7: Building Skills

The Big Idea: The skills and plugins you've used were built by someone. Now you learn to build your own — packaging expertise into executable specifications. From consumer to creator. This session focuses on building a single skill well. Session 8 teaches composition.

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
| `WORKFLOW.md` | Update "What I've Built So Far" with skill creation |
| `learning-journal.md` | Append Session 7 takeaway at session end |

---

## Concept 1: What a Skill Actually Is

### Frame

A skill is a folder containing instructions, scripts, and resources that Claude loads dynamically for specific tasks. At its simplest, a skill is a SKILL.md file — a structured document that defines how Claude should approach a specific type of work. Claude reads it and follows it as an SOP.

The key distinction: a skill encodes HOW to do something, not just WHAT to produce. A prompt says "write a competitive analysis." A skill says "when analyzing competitors, use only primary sources, never older than 30 days, always structure as SWOT, lead with strategic implication."

### Show

Point to the training itself: "You've been running inside a skill this entire time. This session — Session 7 — is a SKILL.md file that defines how I teach you. It has process stages (Frame, Show, Do, Debrief), quality gates (checkpoints where I wait for you), behavioral constraints (one concept at a time, never lecture for more than 4 paragraphs), and trigger conditions (when STATE.md shows Session 7)."

"That's not magic — it's a markdown file. Someone wrote it. And by the end of this session, you'll write one for your own workflow."

### Debrief

"Skills encode expertise. They make Claude consistently good at a specific type of work, across sessions, across users. The first version will be imperfect. That's fine — Exercise 3 is specifically about testing and refining."

### Quick Check

"Think about [your workflow]. What's one rule or judgment call you apply every time that a generic prompt would miss?"

🛑 **CHECKPOINT** — A good answer names something specific and behavioral, not just a topic area. If they give a vague answer like "quality" or "accuracy," push for the concrete rule behind it.

---

## Concept 2: The Decision Framework

### Frame

Not everything needs a skill. The decision framework helps you invest at the right level:

- **Chat** — Exploring, brainstorming, one-time tasks, heavy iteration
- **Project** — Recurring work that benefits from persistent context
- **Skill** — Specialized expertise or methodology that should be applied consistently
- **Plugin** — Bundled capabilities distributed as a package

The cost increases as you move up. So does the return — but only if the usage justifies the investment.

### Show

Map the student's experience to the framework:
- "In Sessions 1-2, you were in chat mode — exploring, learning."
- "In Session 3, you built a Project — persistent context for your workflow."
- "Now you're building a skill — encoding the expertise that makes your workflow work."
- "In Session 8, you might package it as a plugin."

Then help them evaluate: "Your workflow justified a Project because you use it weekly. Does it justify a skill? The test: are there rules, judgment calls, and quality criteria that you'd want applied consistently every time? If yes, a skill is the right investment."

### Debrief

"Most people's first instinct is to build a skill for everything. The framework prevents over-engineering. Chat for exploration, Projects for recurrence, skills for expertise, plugins for distribution."

### Quick Check

"Where does [your workflow] sit on the framework — Chat, Project, Skill, or Plugin? What's the specific reason it belongs at that level and not one level lower?"

🛑 **CHECKPOINT** — They should justify the level by naming what that level provides that the lower one doesn't. If they just repeat the label, ask them what would be lost by dropping down one level.

---

## Concept 3: Creating Skills Through Conversation

### Frame

You don't have to write a skill file from scratch. Cowork has a built-in path: click the dropdown arrow next to any chat name and select "Turn into skill." Claude reads an internal skill-creator, asks you about your process, and generates a complete skill — SKILL.md file, reference materials, scripts, the works. It even runs an evaluation before producing a downloadable skill file.

This is the accessible path. You describe your expertise in plain language, and Claude handles the formatting and structure. No file editing required.

### Show

Walk through the "Turn into skill" flow conceptually:

1. **Start from any conversation** — You've been doing a task in Cowork. You realize this is something you'd want Claude to do the same way every time. Click the dropdown → "Turn into skill."
2. **Claude asks questions** — About your process, what makes output good, when you'd use this skill, what materials it needs. Answer naturally — Claude is extracting your expertise the same way Exercise 1 will do explicitly.
3. **Claude builds the skill** — Generates a SKILL.md with proper YAML frontmatter, bundles any reference files or scripts, and packages it all.
4. **Claude evaluates it** — Runs a validation before producing the downloadable file.
5. **You activate it** — Save the file, then enable it in Settings > Capabilities > Skills.

"This is how most people will create their first skill. It works well for straightforward workflows. But when you need precise control — specific process stages, quality gates, behavioral constraints — you'll want to understand what's inside that file. That's Concept 4."

### Debrief

"Turn into skill" gets you 80% of the way through conversation. Concept 4 teaches the structure so you can read what Claude generated, spot what's missing, and edit it to get the last 20%. Both paths matter — accessible entry, then deeper control when you need it.

### Quick Check

"When would 'Turn into skill' be enough on its own, and when would you need to open the SKILL.md and edit it manually?"

🛑 **CHECKPOINT** — Good answer distinguishes simple/mechanical workflows (conversation path is fine) from workflows with nuanced judgment calls, specific quality criteria, or complex multi-stage processes (need manual editing for precision). If they can't distinguish, ask: "Would you trust someone to describe your workflow accurately just by interviewing you, or would you need to review and correct what they wrote?"

---

## Concept 4: Anatomy of a Good Skill File

### Frame

Whether Claude generated your skill file through conversation or you're writing one from scratch, you need to understand the structure. This is the "going deeper" layer — knowing what's inside the SKILL.md so you can read it, evaluate it, and improve it.

Remember the profile preferences you wrote in Session 0 — specific, behavioral instructions that change how Claude operates? A good skill file follows the same principle, scoped to a single task type.

A SKILL.md contains:
- **Role and mindset** — How Claude should think, not just what label to wear
- **Process stages** — Named steps that build on each other (3-5 stages)
- **Quality gates** — Specific criteria for evaluating output at each stage
- **Behavioral constraints** — What NOT to do, scope boundaries, known pitfalls (same instinct as the guardrails you wrote in Session 4)
- **Trigger conditions** — When this skill should be invoked

### Show

Walk through each component using a concrete example relevant to the student's domain. If they write reports, show what each component looks like for a report-writing skill. If they do research, show a research skill.

For each component, connect to earlier training:
- Role and mindset: "Like profile preferences (S0), but for this specific task"
- Process stages: "Like the Frame/Show/Do/Debrief this training uses"
- Quality gates: "Like the checkpoints where I stop and verify before moving on"
- Behavioral constraints: "Like the guardrails in your transition prompts (S4)"
- Trigger conditions: "Like the skill descriptions you've seen in the plugin ecosystem (S6)"

### Debrief

"These five components turn a vague instruction into a precise specification. Whether you wrote this yourself or Claude generated it via 'Turn into skill,' these are what you're checking for. Exercise 1 extracts your expertise, and Exercise 2 gives you both paths to create the skill."

### Quick Check

"Pick any one of the five components — role, process stages, quality gates, constraints, or triggers. What would go wrong in [your workflow] if that component were missing from the skill file?"

🛑 **CHECKPOINT** — A good answer connects the missing component to a specific failure mode, not a generic "it wouldn't work well." If they struggle, ask them to imagine Claude running the skill without that one piece.

---

## Concept 5: CLAUDE.md — Project-Level Configuration

### Frame

In Session 3, you wrote project instructions in Claude's UI. CLAUDE.md does the same thing, but as a file in your workspace folder. When Claude opens a folder containing a CLAUDE.md, it reads the file automatically.

Why a file instead of the UI? Two reasons. First, if you use the file system approach for project knowledge (Session 3), CLAUDE.md keeps all configuration in one place — your folder is the single source of truth. Second, when building for a team (Session 9), a CLAUDE.md travels with the project so everyone gets the same Claude behavior without configuring their UI.

### Show

"You already have a version of this — your Project instructions from Session 3 live in the UI. A CLAUDE.md would contain the same content but live in your workspace folder alongside your handoff file, skills, and reference material. It's the file-system equivalent of what you already built."

### Debrief

"CLAUDE.md is optional — your UI-based project instructions work fine. The file approach shines when you want configuration to travel with the project or when multiple people need the same setup. Consider it for Session 9 when you design for teammates."

---

## Exercise 1: Extract Your Workflow's Hidden Expertise (Throughline)

### Frame

"You've been running your workflow for several sessions. What makes YOUR version better than a generic attempt? The expertise you're about to extract is what makes a skill more than just a prompt."

### Do

Guide the student through extracting their tacit expertise:

**Step 1: The rules**
Ask: "What rules do you follow when doing this workflow? Not the steps — the rules. Things like 'always check X before Y' or 'never include Z without context' or 'when the input is ambiguous, default to [approach].'"

🛑 **CHECKPOINT** — Wait for their rules.

**Step 2: The quality criteria**
Ask: "How do you know when the output is good? What would you check? What would make you redo it?"

🛑 **CHECKPOINT** — Wait for their criteria.

**Step 3: The mistakes**
Ask: "What mistakes have you learned to avoid? What does bad output from this workflow look like? What causes it?"

🛑 **CHECKPOINT** — Wait for their mistakes.

**Step 4: The judgment calls**
Ask: "Where in the workflow do you have to make a judgment call — something that's not mechanical, where the right answer depends on context?"

🛑 **CHECKPOINT** — Wait for their judgment calls.

**Step 5: Document it**
Help them write all of this out in plain language — this is the raw material for the SKILL.md.

### Debrief

"That's your expertise, externalized. Most of it lives in your head and gets applied unconsciously. Now it's written down. Exercise 2 structures it into a skill file."

---

## Exercise 2: Create Your Workflow's Skill (Throughline)

### Frame

"Take the expertise from Exercise 1 and turn it into a working skill. You have two paths."

### Do

**Present both paths:**

"You can create your skill through conversation — using 'Turn into skill' from the chat dropdown — or by writing the SKILL.md manually. The conversation path is faster. The manual path gives you more control. I'd recommend trying the conversation path first, then reviewing and editing what Claude produces. But if you want to go hands-on from the start, the manual path is here."

🛑 **CHECKPOINT** — Let the student choose their path.

**Path A: Conversation ("Turn into skill")**

**Step 1:** In this Cowork session, describe your workflow expertise from Exercise 1 to Claude. Include the rules, quality criteria, mistakes to avoid, and judgment calls.

**Step 2:** Use "Turn into skill" from the chat dropdown (or start a new chat and trigger it there).

**Step 3:** Answer Claude's questions as it builds the skill. Reference the expertise you extracted in Exercise 1.

**Step 4:** Review what Claude generated. Open the SKILL.md and check for the five components from Concept 4: role and mindset, process stages, quality gates, behavioral constraints, trigger conditions. What's missing or weak?

**Step 5:** Edit the SKILL.md to fill gaps. This is where the Concept 4 knowledge pays off.

🛑 **CHECKPOINT** — Review the skill together. Does it capture the expertise from Exercise 1? What did Claude get right? What needed manual fixing?

**Path B: Manual SKILL.md**

**Step 1: YAML frontmatter**
Name, description, trigger conditions.

**Step 2: Role and mindset**
Turn their domain expertise into a role frame: "How should Claude think when doing this work?"

**Step 3: Process stages**
Organize their workflow steps into 3-5 named stages. Each stage should represent a distinct type of thinking.

**Step 4: Quality gates**
For each stage, write the check: what needs to be true before moving to the next stage?

**Step 5: Behavioral constraints**
Turn their "mistakes to avoid" into explicit constraints. Turn their "judgment calls" into decision rules where possible.

🛑 **CHECKPOINT** — Review the complete SKILL.md together. Target: under 100 lines. If it's longer, help them trim — the skill should be dense, not comprehensive.

### Debrief

"You have a skill file. Whether Claude drafted it or you wrote it, the same principle applies: it's going to be imperfect. The first version always is. Exercise 3 is where you find the gaps."

If the student used Path A, note what they learned: "You saw what Claude generates automatically and where it falls short. That's the value of understanding the anatomy — you can evaluate and improve what the tool produces."

Update WORKFLOW.md: Session 7: Created SKILL.md encoding workflow expertise [via conversation / manually].

---

## Exercise 3: Test and Refine the Skill (Throughline)

### Frame

"Load the skill and give it real work. See where it breaks."

### Do

**Step 1:** Load the SKILL.md in a Cowork session. Give Claude a real input from the student's workflow.

**Step 2:** Let the skill drive the process. Observe:
- Did Claude follow the stages?
- Did it hit the quality gates?
- Where did it deviate from how the student would do it?
- Were the behavioral constraints respected?

🛑 **CHECKPOINT** — Evaluate together. What worked? What didn't?

**Step 3:** Refine the skill file based on what happened. Common fixes:
- Stages that were too vague → make them more specific
- Quality gates that were skipped → make them explicit checkpoints
- Constraints that were too broad → scope them to specific failure modes

**Step 4:** Test again with a different input. Repeat until reliable.

### Debrief

"Skills improve through testing, not through design. The first version gets you 60% of the way. Testing and refining gets you to 90%. The last 10% comes from other people using it — that's Exercise 4."

---

## Exercise 4: The Handoff Test (Standalone)

### Frame

"The real quality bar: can someone who didn't build it use it?"

### Do

**Step 1:** Have the student give their SKILL.md to someone else — a colleague, a friend, anyone who didn't build it.

**Step 2:** Ask that person to use it in a Cowork session without guidance. The student watches but doesn't help.

**Step 3:** Note where the other person gets confused. Those confusion points are design failures in the skill file.

🛑 **CHECKPOINT** — What confusion points surfaced?

**Step 4:** Fix the skill file based on what happened.

If the student doesn't have someone available to test with, simulate it: have them approach the skill as if they'd never seen it. Read the SKILL.md cold and identify what would confuse a newcomer.

### Debrief

"The handoff test applies to everything you build — skills, projects, workflows, documentation. If the person who didn't build it can't use it, the design needs work. You'll apply this test to your full system in Session 9."

---

## Session Completion

### What to Remember

1. Skills encode expertise, not just instructions. They define HOW to think about a task.
2. The decision framework (Chat → Project → Skill → Plugin) prevents over-engineering.
3. "Turn into skill" is the accessible entry point — Claude builds the skill through conversation. Use it for straightforward workflows.
4. Good skill files: role + process stages + quality gates + constraints + triggers. Know the anatomy so you can evaluate and improve what Claude generates.
5. CLAUDE.md is project-level configuration in the file system. Use when config should travel with the project.
6. Test with real inputs, multiple times. First version always needs refinement.
7. The handoff test is the real quality bar: can someone who didn't build it use it?

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 7: Building Skills** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 7 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 8

"You've built a single skill for your workflow. But look at it honestly — does it try to do too much in one pass? Most real workflows have distinct phases that require different thinking. Session 8 teaches skill orchestration: splitting your workflow into multiple skills that hand off to each other through shared state. It's the same pattern this training uses — 10 session skills coordinated by an orchestrator through a state file. You're about to learn how that works."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-8`
- If they want to break → "When you're ready to continue: open the Cowork tab, select this training folder, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
