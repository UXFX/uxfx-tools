---
name: session-5
description: >
  Session 5: Cowork Mode. Teaches what Cowork adds, approval modes, Cowork's
  context layers, static and live artifacts, sub-agents, research in Cowork,
  and error recovery. Three exercises including moving the workflow into Cowork
  and producing a real deliverable. Use when: STATE.md shows Session 5, or user
  says "session 5" or "cowork".
user-invocable: true
---

# Session 5: Cowork Mode

The Big Idea: Cowork mode turns Claude from a chat partner into an agent that works with your files and your computer. The mental model shift: from "I chat with Claude and copy-paste results" to "Claude works alongside me in my actual environment."

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
| `WORKFLOW.md` | Update "What I've Built So Far" with Cowork migration |
| `learning-journal.md` | Append Session 5 takeaway at session end |

---

## Concept 1: What Cowork Mode Adds

### Frame

Your workflow has lived on the chat side since Session 3 — a Project, mounted folders, conversations. The training, meanwhile, has been running in Cowork since Session 0. You've been inside Cowork this whole time without it being the lesson. Now it is: this session moves YOUR workflow in.

What Cowork adds over chat: code execution, sub-agents, document creation (Word, Excel, PowerPoint, PDF), shell commands, and autonomous operation. The key difference: in regular chat, Claude reads your files and responds in the conversation. In Cowork, Claude operates within your environment — creating files, running scripts, coordinating parallel work, and producing deliverables directly to your file system.

### Show

Demonstrate by pointing to what the student is experiencing right now: "This training is running in Cowork mode. The plugin is reading your state file, writing updates to it, producing files in your workspace. That's Cowork in action — Claude isn't just chatting with you, it's operating in your file system."

Then list what becomes possible:
- Create a Word doc, spreadsheet, or PDF directly to your folder
- Run Python scripts to process data
- Spawn sub-agents that work in parallel
- Manage files — create, edit, rename, organize
- Operate autonomously while you do other things

### Debrief

"Cowork is Claude as operator, not just advisor. Everything from Sessions 2-4 still applies — context window, project instructions, handoff discipline. Cowork just gives Claude hands."

### Quick Check

"What's the difference between what you were doing with Claude in Session 3 and what Cowork enables? If Claude could already read your files, what actually changed?"

🛑 **CHECKPOINT** — Good answer identifies that Cowork adds execution: code running, file creation/editing, sub-agents, document generation, and autonomous operation. Chat reads and responds; Cowork reads, acts, and produces. If they say "nothing changed," redirect to the operator vs. advisor distinction.

---

## Concept 2: Approval Modes — Controlling Autonomy

### Frame

In Session 3, every file operation required you to be in the conversation. Cowork introduces a choice about how much autonomy Claude gets:

- **Ask before acting** — Claude proposes actions and waits. You see every file creation, every edit, every tool call before it happens. Recommended while learning.
- **Act without asking** — Claude executes autonomously. This is where Cowork becomes genuinely hands-off — Claude runs your workflow while you do other things.

### Show

"Right now, this training is probably running in 'Ask before acting' mode — I proposed writing to your state file and you approved it. If you switched to autonomous mode, I'd just do it. Both have a place: 'Ask' when you're building and testing a workflow, 'Act' when you trust it and want speed."

### Debrief

"Start with 'Ask before acting.' Switch to 'Act without asking' once a workflow is proven reliable. The approval mode is a trust dial — turn it up gradually."

### Quick Check

"You just built a new step in [your workflow] and you're about to run it for the first time in Cowork. Which approval mode should you use and why?"

🛑 **CHECKPOINT** — Good answer says "Ask before acting" because the workflow step is unproven — you need to verify each action before trusting it. If they say "Act without asking" for speed, remind them that trust is earned through verified runs, not assumed.

---

## Concept 3: Cowork's Context Layers

### Frame

Session 2 gave you the personalization stack for chat. Cowork has its own version of the same idea — three layers, broadest to narrowest:

- **Global instructions** — Settings > Cowork. Apply to every Cowork session. The Cowork counterpart of profile preferences.
- **Cowork projects** — group related tasks into a workspace with its own files, links, instructions, and memory. The Cowork counterpart of the chat Projects you built in Session 3.
- **Folder instructions** — context attached to a folder you've connected. Claude can update these itself as it learns how you work in that folder.

One nuance that matters: in Cowork, memory lives only inside Cowork projects. Standalone Cowork tasks don't carry memory from one to the next — which is exactly why the handoff files you built in Session 4 are the reliable layer here.

### Show

Connect to what they already built: "You wrote project instructions for your workflow in Session 3 — that was the chat side. The same layering decision now repeats on the Cowork side: anything true for ALL your Cowork work goes in global instructions. Anything specific to your workflow's folder goes in folder instructions. And if your workflow runs as recurring Cowork tasks, a Cowork project keeps its tasks, files, and memory in one place."

Walk them to Settings > Cowork and look at global instructions together. Most people leave this empty without knowing it exists.

### Debrief

"Same principle, new surface: layers shape behavior, layers consume context, and you decide what goes where. You've now seen the pattern twice — that's the tell that it's a principle, not a feature."

### Quick Check

"You have one rule you want Claude to follow in every Cowork task you ever run, and another rule that only applies when Claude works in your workflow's folder. Where does each one go?"

🛑 **CHECKPOINT** — First rule: global instructions. Second rule: folder instructions (or the Cowork project for that workflow). If they put everything in global instructions, point at the cost: every Cowork session loads it, relevant or not — the same context budgeting trade-off as Session 3.

---

## Concept 4: Artifacts — Static and Live

### Frame

Artifacts are standalone content rendered in a dedicated panel — code, documents, interactive visualizations, apps. They're self-contained and can be copied, downloaded, or iterated on. Useful for deliverables that need to live outside the conversation.

Cowork adds a second kind: **live artifacts** — persistent, interactive dashboards saved to their own "Live artifacts" tab. A regular artifact is finished when the session ends. A live artifact keeps working: reopen it next week and it refreshes with current data from your connected apps and local files. Every update saves a version you can compare or restore.

### Show

Point to the training portal: "Your progress portal is a static artifact — an HTML file a skill generates and regenerates. That's the deliverable pattern: produce, deliver, done until the next update."

Then show what live artifacts add, with examples near the student's workflow: a tracker that shows current status every time it's opened, a morning brief, a dashboard watching the inputs their workflow depends on. Two ways to create one: describe it in any Cowork task ("build me a dashboard that shows..."), or open the Live artifacts tab and click "New artifact."

Two things to know before building one:

- **They use your connectors without asking.** A live artifact can only use the connectors you approved when it was created or updated — but unlike a normal session, it doesn't ask permission each time it refreshes. Be deliberate before wiring one to a connector that can change data. Same trust dial as approval modes — this is the autonomous end of it.
- **They're local and personal, for now.** Live artifacts live on this computer and can't be shared yet.

### Debrief

"The decision is about the data. If the output is finished when you deliver it, it's a static artifact or a file. If you'd want to reopen it and see today's state, it's a live artifact. You'll have more to feed them after Session 6 connects your tools."

### Quick Check

"Think about [your workflow]'s outputs. Which one is a deliverable — finished when it ships — and which one would you rather have as a view that's current every time you open it?"

🛑 **CHECKPOINT** — Good answer sorts outputs by whether the underlying data keeps changing: reports and documents ship as static artifacts or files; status views, trackers, and monitors fit live artifacts. If they say "make everything live," ask what it would mean for a client deliverable to quietly change after they sent it.

---

## Concept 5: Sub-Agents

### Frame

Claude can spawn sub-agents with their own context windows. Each sub-agent works on a piece of the problem and returns a summary. This is both a parallel processing technique AND a context management technique — sub-agents don't consume your main session's context window.

### Show

Explain with a concrete example from the student's workflow: "Say your workflow involves researching three competitors. Instead of doing all three in this conversation — which would consume a lot of context — Claude could spawn three sub-agents, each researching one competitor. Each agent has its own fresh context window. They work in parallel and return summaries. Your main session stays lean."

Connect to Session 2's context window concept: "Remember context budgeting? Sub-agents are a context budgeting technique. They let you do more work without filling up your main window."

### Debrief

"Sub-agents are Claude's way of scaling work without scaling context consumption. You'll see them in action more in Sessions 7-8 when we build multi-skill systems."

### Quick Check

"Your workflow requires researching three competitors. You could do all three in the main conversation, or use sub-agents. What's the context window advantage of sub-agents here?"

🛑 **CHECKPOINT** — Good answer explains that each sub-agent gets its own fresh context window, so the research doesn't consume the main session's context. The main session only receives summaries, staying lean for the actual work. If they focus only on speed/parallelism, redirect to the context budgeting angle.

---

## Concept 6: Research in Cowork

### Frame

Session 2 introduced the concept: Claude's training data is frozen. In Cowork, research becomes operational — Claude can search the web, fetch pages, and write findings to files in your workspace, all within the same session where it's producing deliverables.

The practical pattern: **research first, then produce.** Have Claude gather current information, save it to a reference file, review what it found, THEN use that file as context for the actual work.

### Show

Walk through why separation matters: "If your workflow touches pricing data, and Claude uses stale training data instead of researching current prices, your deliverable is wrong. The research step catches that. And because the findings are saved to a file, you can review them before Claude builds on top of them. If the research is wrong, you catch it before the deliverable is wrong."

### Debrief

"Research in Cowork is an explicit step: search, save, review, produce. Not something you hope Claude's training data covers. If your workflow touches anything that changes, build research into it."

### Quick Check

"Why does the research pattern say 'save to a file, review, THEN produce' instead of just letting Claude research and produce in one step?"

🛑 **CHECKPOINT** — Good answer identifies the verification layer: if the research is wrong (stale data, bad sources, misunderstood query), you catch it before the deliverable is built on top of it. One-step research-and-produce means errors compound silently. If they mention only file persistence, redirect to the review-before-build principle.

---

## Concept 7: Error Recovery & Debugging

### Frame

Things go wrong. Cowork tasks fail mid-execution, Claude misinterprets scope, or the session degrades quietly. Three failure modes to recognize:

1. **Context exhaustion** — Claude forgets earlier instructions, output goes generic. The fix: end the session, write a handoff file (Session 4), and start fresh.
2. **Tool and permission failures** — Error messages about files, connectors, or commands. The fix: read the error, check permissions (right folder mounted? connector authenticated?), retry. Don't let Claude silently work around the failure.
3. **Scope drift** — Output is technically correct but answers the wrong question or touches files it shouldn't. No error message — hardest to catch. The fix: guardrails in your prompts, review before approving, "Ask before acting" mode.

### Show

For each failure mode, give a recognizable symptom:
- Context exhaustion: "Claude's responses get shorter and more generic. It starts ignoring instructions you gave 20 messages ago."
- Tool failure: "You see an error message about permissions or file not found. Claude says something like 'I wasn't able to access that file.'"
- Scope drift: "You asked for a summary of client feedback and Claude also rewrote your project instructions because it thought they could be better. No error — just unauthorized initiative."

### Debrief

"The meta-skill: when output quality drops or something feels off, stop and diagnose. Don't push through a broken session. You now have the tools to recover — handoff files, transition prompts, fresh sessions. Use them."

---

## Exercise 1: Move Your Workflow Into Cowork (Throughline)

### Frame

"Time to migrate your workflow from chat to Cowork. Claude stops advising and starts operating."

### Do

**Step 1:** Confirm the student's workspace folder is mounted. Have Claude read the handoff file and master checklist from Session 4.

**Step 2:** Identify one step of the workflow that involves file input/output. Guide them to run it entirely in Cowork — Claude reads inputs from the file system, does the work, and writes outputs back.

🛑 **CHECKPOINT** — Did it work? Compare the experience to doing the same step in chat (Sessions 2-3). What changed?

**Step 3:** Debrief the difference: "In chat, you got a response in the conversation. In Cowork, the output is a file in your workspace. You can open it, edit it, share it. That's the shift."

### Debrief

Update WORKFLOW.md: Session 5: Moved workflow into Cowork — Claude now reads from and writes to workspace files.

---

## Exercise 2: Produce a Real Deliverable (Throughline)

### Frame

"Now produce something real — an actual output from your workflow that you'd use, not a test file."

### Do

**Step 1:** Identify what the student's workflow actually produces — a report, a summary, a processed dataset, formatted content, whatever their output is.

**Step 2:** Have Claude produce it in the appropriate format (Word doc, spreadsheet, PDF, etc.) directly to their workspace folder.

If the output is a spreadsheet or slide deck, mention the follow-on: Cowork's Excel and PowerPoint files can be opened and refined further with the Claude for Excel and Claude for PowerPoint add-ins inside Microsoft Office. The deliverable stays workable after it leaves Cowork.

🛑 **CHECKPOINT** — Have the student open the file on their computer. Is it usable? Is it what they'd produce manually?

**Step 3:** If it needs refinement, iterate in the conversation. Show the student the feedback loop: produce → review → refine → produce again.

### Debrief

"You now have Cowork producing actual work output from your workflow. Not chat text — real deliverables. This is the operational shift that makes Claude a genuine productivity tool."

---

## Exercise 3: Break It on Purpose (Standalone)

### Frame

"Let's build your error recovery muscles. We're going to deliberately trigger failures and practice diagnosing them."

### Do

Have the student try one or more of these:

**Option A: Permission failure**
Mount the wrong folder (or unmount the right one) and ask Claude to find a file. See what the error looks like. Practice the fix: check permissions, remount, retry.

**Option B: Contradictory instructions**
Give Claude conflicting directives: "Make it shorter but add more detail" or "Be concise and explain everything thoroughly." See how Claude handles the contradiction. Practice the fix: clarify the intent, restate the instructions.

**Option C: Context exhaustion**
Run a long, rambling session without handing off. Switch topics multiple times. Watch for the signs of degradation. Practice the fix: write a quick handoff note, start fresh.

🛑 **CHECKPOINT** — For each failure: "What type was it? How did you recognize it? What was the fix?"

### Debrief

"You now have first-hand experience with all three failure modes. Context exhaustion is the subtlest — it creeps up. Tool failures are the loudest — error messages. Scope drift is the sneakiest — no error, just wrong work. Knowing these patterns is half the battle."

---

## Session Completion

### What to Remember

1. Cowork mode is file-system access + code execution + sub-agents + document creation. Claude as operator.
2. Start with "Ask before acting" until you trust the workflow. Then switch for speed.
3. Cowork has its own context layers: global instructions, Cowork projects, folder instructions. Memory lives only in Cowork projects — files remain the reliable layer.
4. Static artifacts are deliverables; live artifacts are views that refresh with current data. Live artifacts use approved connectors without asking — wire them deliberately.
5. Sub-agents are a context management technique — work without context consumption.
6. Research in Cowork: search, save, review, produce. Explicit step, not assumption.
7. Three failure modes: context exhaustion, tool failures, scope drift. Recognize which.
8. When something feels off, stop and diagnose. Don't push through.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 5: Cowork Mode** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 5 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 6

"Cowork gives Claude hands to work with your files. Session 6 extends Claude's reach beyond your computer — connecting to external services, automating recurring work, and processing files at scale. If your workflow touches Slack, email, Google Drive, or any external tool, that's where it gets connected."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-6`
- If they want to break → "When you're ready to continue: open the Cowork tab, select this training folder, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
