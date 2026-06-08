---
name: session-3
description: >
  Session 3: Projects & Context Architecture. Teaches Projects, project instructions,
  project knowledge (two approaches), styles, and context budgeting. Four exercises
  including building the workflow's Project. Use when: STATE.md shows Session 3,
  or user says "session 3" or "projects".
user-invocable: true
---

# Session 3: Projects & Context Architecture

The Big Idea: Session 2 taught you the layers. This session teaches you to architect them. Projects are persistent workspaces where context compounds. The skill isn't knowing what Projects are — it's knowing what goes where, how much to load, and what to leave out.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position, student info |
| `WORKFLOW.md` | Student's workflow description |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position, exercises done, notes |
| `WORKFLOW.md` | Update "What I've Built So Far" with Project details |
| `learning-journal.md` | Append Session 3 takeaway at session end |

---

## Concept 1: Projects — Your Persistent Context Workspace

### Frame

In Session 2, you saw how the context window works and how layers shape Claude's behavior. The problem: in a regular conversation, all that context disappears when the chat ends. Projects solve this. A Project is a workspace where context carries across every conversation — instructions, knowledge files, and settings persist. Every new chat in a Project starts pre-loaded.

One rule upfront: **one Project per workstream.** A mega-project that covers everything degrades quality because it loads irrelevant context into every conversation. Your workflow gets its own Project.

### Show

Demonstrate the difference:

1. Point out that right now, the student has no Project set up — everything Claude knows in this conversation comes from the plugin (which is a different mechanism), their profile preferences, and the conversation itself. There's no persistent workspace carrying context forward between conversations yet.

2. Describe what changes when a Project has strong instructions: "If your workflow Project had instructions that said 'You're helping a [role] produce [output] every [frequency]. Always check [quality criteria] before finalizing. Never [common mistake]' — every conversation in that Project would start with that framing. You'd never have to repeat it."

3. Connect back to Session 2's personalization stack: "Profile preferences are Layer 1 — they apply everywhere. Project instructions are Layer 2 — they apply to one workstream. You're now designing Layer 2."

4. One more thing Projects give you: their own memory. Remember from Session 2 that Claude's memory builds a summary of who you are across all your chats? Each Project gets a separate memory, isolated from that account-wide summary and from other Projects. What Claude learns about your workflow inside this Project stays scoped to it — another reason one Project per workstream pays off.

### Debrief

"Projects are persistent context. The value isn't the feature — it's that you stop repeating yourself and start compounding quality. The next concepts teach you how to fill a Project well."

### Quick Check

"You've got two workstreams — your [workflow] and, say, a side project for planning team meetings. Would you put both in the same Project? Why or why not?"

🛑 **CHECKPOINT** — They should say no — separate Projects, because loading meeting-planning context into every workflow conversation wastes tokens and dilutes quality. If they say yes, reinforce the one-Project-per-workstream rule.

---

## Concept 2: Project Instructions — The Standing Brief

### Frame

Project instructions are text that Claude reads at the start of every conversation in that Project. Think of it as onboarding a new team member — you tell them once, and they remember. Good instructions include: who you are and what this workstream is about, how Claude should think (role framing), default constraints, and domain context.

### Show

Show the difference between weak and strong instructions. Use the student's workflow:

**Weak:** "This project is for my weekly reports."

**Strong:** "You're helping a [student's role] produce [their output type] every [frequency]. The audience is [who reads it]. Quality means [their criteria]. Always [their process preference]. Never [their known pitfall]."

Walk through why each addition matters — each one gives Claude context that shapes judgment calls throughout the conversation.

### Debrief

"Instructions are the highest-leverage context you can write. A few well-chosen paragraphs change every conversation in the Project. You'll write yours in Exercise 1."

### Quick Check

"Your project instructions say 'Help me with my work.' Would that actually change Claude's behavior compared to having no instructions at all?"

🛑 **CHECKPOINT** — They should recognize it's too vague to be useful. Good instructions are specific and behavioral — they should point to what would make a real difference (role framing, constraints, domain context).

---

## Concept 3: Project Knowledge — Two Approaches

### Frame

Claude can access reference material two ways. Pick one, don't manage both:

**Option A: Project Knowledge uploads.** Upload files through the Claude UI. Available in every conversation automatically. On paid plans, RAG kicks in when content exceeds context limits, expanding capacity up to 10x. The downside: updating means removing and re-uploading in the UI.

**Option B: File system via workspace folder.** Keep files on your computer, mount the folder. Edit files anytime with your normal tools, Claude sees changes immediately. Works in both chat and Cowork. The downside: you mount the folder each session.

### Show

Help the student decide which approach fits their workflow:

"Think about your reference material for [their workflow]. Does it change often? If it's stable — like a style guide or a standard template — uploading to Project Knowledge is simpler. If it evolves frequently — like a client brief you update weekly or competitive data that changes — the file system approach keeps a single source of truth you manage outside Claude."

**Important nuance about files:** Workspace files often serve multiple purposes — and that's a feature, not a problem. The same file might be something you share with Claude as context, something you read and update yourself between sessions, something that informs future Claude sessions, and something you share with a client or colleague. When choosing your knowledge approach, think about ALL the ways you use these files, not just Claude's access to them. If you're editing files regularly, sharing them externally, or using them as living documents, the file system approach usually wins because the files stay under your control in their normal location.

### Debrief

"Either works. The deciding factor is a combination of how often your material changes and how many purposes your files serve. You'll plan this in Exercise 1."

### Quick Check

"For your workflow, which knowledge approach would you lean toward — uploads or file system? What about your reference material made you pick that one?"

🛑 **CHECKPOINT** — Either answer is valid. What matters is that they can articulate *why* — stable vs. evolving content. If they can't decide, help them think about how often their reference material changes.

---

## Concept 4: Styles — Voice and Tone Control

### Frame

Styles control how Claude communicates — not what it knows, but how it delivers. Four presets (Normal, Concise, Formal, Explanatory) plus custom styles.

### Show

Quick demonstration: take the student's workflow and describe how output would differ across styles.

- Concise: "Bullet points, minimal explanation, just the deliverable."
- Formal: "Full sentences, professional tone, suitable for external audiences."
- Explanatory: "Detailed reasoning, step-by-step logic, good for learning."

If the student's workflow has an audience, connect the style choice to that audience.

### Debrief

"Styles are a light touch — useful for consistent voice, but not where the real leverage is. Instructions and knowledge shape what Claude produces. Styles shape how it sounds."

### Quick Check

"If you had to rank the four things we've covered — Projects, instructions, knowledge, and styles — by impact on output quality, what's your top pick and why?"

🛑 **CHECKPOINT** — Instructions should be near the top. Styles should be at the bottom. The reasoning matters more than the exact ranking — they should understand that behavioral context (instructions) has more leverage than presentation context (styles).

---

## Concept 5: Context Budgeting — The Skill That Separates Power Users

### Frame

This is the synthesis concept for the session. Every element loaded into the context window costs tokens: project instructions, knowledge files, memory, conversation history. The window is finite. The discipline: load only what this specific conversation needs.

Signs of overload: Claude forgetting earlier context, output becoming generic, responses losing specificity. When this happens, the window is full and earlier context is getting pushed out.

The principle: **high-signal, low-volume.** Dense, relevant context beats sprawling, comprehensive context.

**Rough size targets to keep in mind:**
- **Profile preferences:** 100-300 tokens. These load into every conversation across all of Claude. Keep them tight.
- **Project instructions:** 300-500 tokens. The standing brief for one workstream. Enough to shape behavior, not so much that it crowds the conversation.
- **Project knowledge files:** Total across all files, aim for under 5,000 tokens of actively-used content per conversation. RAG helps pull relevant chunks, but less is still more.
- **Conversation itself:** This is where the real work happens. Everything above eats into the space available for back-and-forth. The more context you pre-load, the shorter your productive conversation window.

These aren't hard limits — they're guidelines for staying in the sweet spot. You'll feel when you've crossed the line (Session 3, Exercise 3 is designed for exactly that).

### Show

Make the tradeoff concrete using the student's setup:

1. "Your Project instructions take up some of the window. Your knowledge files take more. Memory takes some. That leaves the rest for your actual conversation — the back-and-forth where work happens."

2. "If you upload 10 reference files to be safe, but only 2 are relevant to today's conversation, the other 8 are consuming context that could have been conversation space. RAG helps with this — it pulls in relevant chunks rather than loading everything — but the principle still applies."

3. "The discipline: start lean. Add context when output quality tells you something is missing. Don't preload everything just in case."

### Debrief

"Context budgeting is the core skill of context engineering. It's not a feature you turn on — it's a judgment call you make every time you set up a conversation. Exercise 3 lets you feel what overload looks like so you can recognize it."

---

## Exercise 1: Design Your Workflow's Project (Throughline)

### Frame

"Time to design your first real Project — a persistent workspace for your actual workflow. We'll do the design work right here in this training session, then you'll set it up afterward."

**Important context:** Projects are created in the app's Projects area, outside this conversation — so we're not going to bounce you out of training to set one up live. Instead, we'll design everything here — instructions, knowledge strategy, structure — and save it to a file. After this session, you'll create the Project and paste in what we built. This is actually the better approach anyway: designing context architecture is thinking work, and this conversation has all the context about your workflow.

### Do

**Step 1: Name and scope**
Help the student name their Project — something specific to their workflow (not "My Project" — something they'll recognize in a list).

🛑 **CHECKPOINT** — Confirm the name.

**Step 2: Write the standing brief**
Help them write project instructions. Walk through each component, pulling from what they told you about their workflow in Session 2:

- Who they are and what this workstream is about
- Role framing: how Claude should think about this work
- Default constraints: format preferences, things to avoid
- Domain context: anything that applies to every conversation in this Project

**Target length:** Aim for 300-500 tokens total — roughly 4-6 short paragraphs. This is the sweet spot: enough to meaningfully shape Claude's behavior without eating into conversation context. Remind them of the budgeting principle: dense and relevant, not comprehensive and bloated.

🛑 **CHECKPOINT** — Review their instructions together. Challenge anything vague: "Would this actually change Claude's behavior, or is it a label?"

**Step 3: Plan reference material**
Help them decide: Option A (uploads) or Option B (file system)? Identify 2-3 specific reference files they'll add.

**Step 4: Save the design**
Write the complete Project design — name, instructions, knowledge plan — to a file in the student's workspace. This is their setup guide for after the session.

### Debrief

"You've designed a purpose-built Project for your workflow. After this session, create the Project in Claude Desktop, paste in the instructions we wrote, and add your reference files. Every conversation you start in it will have this context pre-loaded. The design work we did here — that's context engineering. You thought about what Claude needs before you built it."

Update WORKFLOW.md: add to "What I've Built So Far" — Session 3: Designed workflow Project with instructions and knowledge plan.

---

## Exercise 2: The A/B Comparison — Simulated (Throughline)

### Frame

"Let's see the difference your Project design would make — without leaving this session."

### Do

**Step 1:** Ask the student to pick one specific step of their workflow.

**Step 2: Bare prompt** — Have the student write a bare, context-free prompt for that step — the way they'd type it into a fresh Claude conversation with no Project, no instructions, no context. Run it right here and look at the output together.

**Step 3: With full context** — Now run the same request, but this time prepend the project instructions they wrote in Exercise 1 as context. Say: "Pretend you just opened a conversation in your new Project. Here are your instructions:" then include them. Run the same task.

**Step 4:** Compare the two outputs. Ask: "What's different? Can you trace the improvement back to a specific instruction you wrote?"

### Debrief

"Same Claude, same question, different context, different quality. The delta between those two outputs — that's what context architecture produces. When you set up your Project after this session, every conversation will start with that context automatically. You won't need to prepend it each time."

---

## Exercise 3: The Context Overload Experiment (Standalone)

### Frame

"Context budgeting is a feel thing — you need to experience overload to recognize it later. Let's deliberately break it."

### Do

**Step 1:** Have the student deliberately overload a test conversation:
- Write verbose, rambling project instructions (not their real ones)
- Load multiple large files
- Have a long, wandering conversation that covers many topics

**Step 2:** At some point, ask Claude to recall something from early in the conversation or produce output that requires synthesizing multiple pieces of context. Notice when quality degrades — generic responses, forgotten specifics, loss of coherence.

**Step 3:** Start a fresh conversation with lean context — just the essentials. Run the same task. Feel the difference.

🛑 **CHECKPOINT** — Ask: "Could you feel the difference? What were the signs that context was overloaded?"

### Debrief

"Now you know what overload feels like. Generic output, lost specifics, Claude sounding like it's guessing instead of reasoning. When you notice those signs in real work, the fix is almost always: less context, not more. Start a fresh conversation, load only what this task needs."

---

## Exercise 4: Your Workflow as a Thinking Partner (Throughline)

### Frame

"So far you've used Claude to execute steps of your workflow. Now use it to improve the workflow itself."

### Do

**Step 1:** Inside the student's workflow Project, have a strategic conversation about the workflow. Not executing it — analyzing it.

Prompt Claude to challenge their process:
- "Are there steps that could be combined?"
- "Is there a quality check I'm skipping?"
- "What would break if someone else ran this workflow?"
- "Where am I spending time on work that Claude could handle?"

🛑 **CHECKPOINT** — Let the conversation run. The student should engage with Claude's challenges, not just collect them.

**Step 2:** Ask the student: "Did any of Claude's challenges surprise you? Is there something you want to change about your workflow based on this conversation?"

### Debrief

"This is Claude as thinking partner — not executing tasks, but challenging assumptions and surfacing blind spots. This mode is often more valuable than the execution mode. Notice what made it work: the Project context gave Claude enough understanding of your workflow to ask good questions. Without that context, the challenges would have been generic."

Update WORKFLOW.md if the student made changes to their workflow description based on this exercise.

---

## Session Completion

### What to Remember

1. One Project per workstream. Don't overload a single Project with everything.
2. Project instructions are your standing brief — set context once instead of repeating it.
3. Project knowledge: uploads for stable content, file system for evolving content. Pick one.
4. Context budgeting is the core skill: load what's needed, leave out what isn't.
5. Start lean and add context when output quality tells you something is missing.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 3: Projects & Context Architecture** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 3 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

**Post-session action reminder:** "Before you start Session 4, set up the Project we designed in Exercise 1. Create the Project in Claude Desktop, paste in the instructions, and add your reference files. It takes 5 minutes and it means Session 4's exercises can use it."

### Bridge to Session 4

"You've designed two layers of your system: profile preferences (Session 0) and a purpose-built Project (Session 3). The missing piece: what happens when a session ends? Right now, every new conversation starts fresh inside your Project. Session 4 teaches handoff discipline — maintaining continuity across sessions so your workflow gets better over time instead of resetting."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-4`
- If they want to break → "When you're ready to continue: open the Cowork tab, select this training folder, and say 'continue training.' Your progress is saved — you'll pick up right where you left off. And remember — set up that Project before next session."
