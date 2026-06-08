---
name: session-6
description: >
  Session 6: Connected Tools & Automation. Teaches connectors (MCP), plugins,
  scheduled tasks, Claude in Chrome, and batch processing. Four exercises including
  connecting a tool and automating a workflow step. Use when: STATE.md shows
  Session 6, or user says "session 6" or "connectors" or "automation".
user-invocable: true
---

# Session 6: Connected Tools & Automation

The Big Idea: Session 5 taught what Claude can do on your computer. This session extends Claude's reach to external services and recurring workflows. From "Claude works with my files" to "Claude works across my entire toolchain."

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
| `WORKFLOW.md` | Update "What I've Built So Far" with connections and automation |
| `learning-journal.md` | Append Session 6 takeaway at session end |

---

## Concept 1: Connectors — Extending Claude's Reach

### Frame

Connectors integrate Claude with external services: Slack, Figma, Google Drive, GitHub, Linear, and more. Once connected, Claude can read from and write to these services directly. Access via Customize > Connectors.

Under the hood, connectors use the Model Context Protocol (MCP) — an open standard for connecting AI to external tools. You don't need to understand MCP to use connectors, but knowing the term helps when troubleshooting. If you see "MCP server" in an error message or tutorial, it's referring to the same thing as a connector.

### Show

Check what connectors are available and identify ones relevant to the student's workflow: "Your workflow involves [their input/output sources]. Let me check whether connectors exist for those services."

Browse available connectors and show what's possible. If their workflow touches Slack, show the Slack connector capabilities. If it touches Google Drive, show that.

### Debrief

"Connectors give Claude reach beyond your local files. The MCP term is worth remembering — it'll show up in error messages and community guides. You'll connect one to your workflow in Exercise 1."

### Quick Check

"If your workflow for [their workflow] needs data from an external service, what's the difference between using a connector and just copy-pasting data into the conversation?"

🛑 **CHECKPOINT** — Good answer identifies that connectors let Claude pull and push data directly within the session, making it part of the workflow rather than a manual step. Copy-pasting breaks the flow, consumes context with raw data, and doesn't scale. If they only mention convenience, push on the integration angle — connectors make external data part of Claude's operational reach.

---

## Concept 2: Plugins — Bundled Capabilities

### Frame

Plugins bundle skills, connectors, and tools into installable packages. Think of them as apps for Claude. Browse and install from the plugin ecosystem via Customize > Plugins.

A meta-moment: "This training you're taking right now IS a plugin. It bundles teaching skills, a state management system, and a progress portal into an installable package. That's the pattern."

### Show

Browse available plugins with the student. Point out the range: document creation, research tools, design tools, productivity tools. For each interesting one, note: "This is a bundle of skills — someone packaged their expertise the same way you'll package yours in Session 7."

### Debrief

"Evaluate before installing — not every plugin is worth the context cost. A plugin that loads heavy instructions into every conversation consumes tokens even when you're not using it. Install what you need, remove what you don't."

### Quick Check

"You find a plugin that looks useful but you're not sure it's worth installing. What's the hidden cost of installing it, even if you don't use it in every session?"

🛑 **CHECKPOINT** — Good answer identifies context cost: plugins load their instructions into the context window, consuming tokens even when inactive. That's less room for actual work. If they only mention disk space or clutter, redirect to the context window impact — it's a token budget issue, not a storage issue.

---

## Concept 3: Scheduled Tasks — Recurring Automation

### Frame

In Session 4, you built handoff discipline to maintain continuity across sessions you run manually. Scheduled tasks are the next step: sessions that run themselves. Claude can check your email every morning, generate a daily briefing, update a tracker, or run any repeatable workflow on a schedule — hourly, daily, weekly, or on specific days.

One practical constraint: the app needs to be open and the computer awake.

### Show

Walk through what a scheduled task looks like using the student's workflow: "You do [their workflow] every [frequency]. What if the [mechanical step] ran automatically? Claude could [specific action] every [day/morning/week] and have the output ready when you sit down."

Show the three ways to create a scheduled task:

1. **Chat dropdown** — Click the dropdown arrow next to any chat name and select "Schedule." Claude walks you through setup conversationally — asking about frequency, timing, and what you want done. This is the fastest path when you've just finished a task and think "I want this to run every week."

2. **The `/schedule` command** — Type `/schedule` in any chat. Same conversational setup, but you can trigger it mid-conversation without touching the dropdown.

3. **Scheduled Tasks page** — Click "Scheduled" in the left sidebar, then "+ New task." This gives you a form to fill in directly: task name, description, prompt, frequency (hourly, daily, weekly, weekdays, manual), model choice, and working folder. Best for creating tasks from scratch without a conversation.

Walk through creating a test task using whichever method feels most natural to the student (something harmless like a daily weather summary or a reminder). Then show them the Scheduled Tasks page where they can see all their tasks, review run history, pause/resume, or run on demand.

One related capability worth knowing: on Pro and Max plans, you can also assign Cowork tasks from the Claude mobile app — message Claude from your phone, and it does the work on your desktop using your local files and connectors, delivering results back to the same conversation. Same constraint as scheduled tasks: the desktop app has to be open and awake. Scheduling handles the recurring work; mobile assignment handles the "I just thought of something" work.

### Debrief

"Scheduled tasks turn manual workflows into background automation. The limitation is the app needs to be running. For your workflow, Exercise 3 will identify which step to automate."

### Quick Check

"Think about [your workflow]. Which step would be a good candidate for a scheduled task, and which step would be a bad candidate? Why?"

🛑 **CHECKPOINT** — Good answer distinguishes mechanical/repeatable steps (good candidates — data pulls, status checks, report generation) from judgment-heavy steps (bad candidates — decisions, creative work, ambiguous tasks). If they can't distinguish, ask: "Could this step run while you're asleep and still produce correct output?"

---

## Concept 4: Claude in Chrome — When Connectors Aren't Enough

### Frame

Connectors work great when they exist for the service you need. But many web tools don't have connectors — internal dashboards, niche SaaS apps, client portals, login-required sites. Claude in Chrome is the fallback: a browser extension that lets Claude see and interact with web pages directly.

Think of it as the manual gear when connectors are the automatic — more flexible, more effort, but it reaches everywhere.

### Show

Describe the capability: "Claude in Chrome can read page content, fill forms, click buttons, extract data, and navigate multi-step web workflows. If your workflow involves a web tool that doesn't have a connector, this is how Claude reaches it."

Ask the student: "Does your workflow touch any web tools that don't have connectors? Internal tools, niche apps, portals?"

### Debrief

"Connectors first — they're faster and more reliable. Chrome extension when connectors don't cover what you need. Between the two, Claude can reach almost any digital tool."

### Quick Check

"Your workflow needs data from a niche internal dashboard at work. There's no connector for it. What's your option, and why would you still prefer a connector if one existed?"

🛑 **CHECKPOINT** — Good answer identifies Claude in Chrome as the fallback, and explains that connectors are preferred because they're faster, more reliable, and purpose-built for the integration. Chrome extension is more flexible but requires more effort and is less predictable. If they don't mention reliability, highlight that connectors use structured APIs while Chrome extension navigates UI — which can break.

---

## Concept 5: Batch Processing Patterns

### Frame

Remember context budgeting from Session 3 — every element in the context window has a cost? Batch processing is where that discipline becomes critical. For high-volume operations (processing dozens of files, reformatting, analyzing), you can't load everything at once.

### Show

Walk through the batch design pattern:
1. **Define scope** — Which files, what operation
2. **Split into numbered batches** — Sized to fit the context window
3. **Script mechanical fixes, manual for judgment** — Not everything needs Claude
4. **Verify each batch** before proceeding

Use a concrete example: "If you had 50 client reports to reformat, loading all 50 would overwhelm the context window. Instead: batch 1 is reports 1-10, verify the output is correct, then batch 2 is 11-20. Mechanical formatting gets scripted. Judgment calls (like 'is this summary accurate?') get manual review."

### Debrief

"Batch processing is context budgeting at scale. Size batches to fit the window. Script what's mechanical. Review what needs judgment. You'll design a batch workflow in Exercise 4."

---

## Exercise 1: Connect a Tool to Your Workflow (Throughline)

### Frame

"Time to extend your workflow beyond local files. Where do your inputs come from or where do your outputs go?"

### Do

**Step 1:** Help the student identify an external service their workflow touches — email, Slack, a shared drive, a project management tool, etc.

🛑 **CHECKPOINT** — Confirm which service to connect.

**Step 2:** Guide them through connecting it via Customize > Connectors. Walk through authentication.

**Step 3:** Test the connection: have Claude pull real data from the service into their workflow, or push a deliverable out to it.

🛑 **CHECKPOINT** — Did it work? Is the data flowing correctly?

### Debrief

"Your workflow now reaches beyond your computer. Inputs can flow in from [service], and outputs can flow out. This is the integration layer of your system."

Update WORKFLOW.md: Session 6: Connected [service] — workflow now pulls/pushes data externally.

---

## Exercise 2: Install and Use a Plugin (Standalone)

### Frame

"Let's explore the plugin ecosystem. Find something useful for your work."

### Do

**Step 1:** Browse available plugins together. Help the student evaluate: is this relevant to their work? Does it do something they can't do with base Claude?

**Step 2:** Install one that looks useful.

**Step 3:** Use it in a Cowork session. Have the student run it on a real task.

🛑 **CHECKPOINT** — "Was it worth installing? Did it save time or effort? Did it do something you couldn't do otherwise?"

### Debrief

"Not every plugin is worth the cost. The evaluation criteria: does it save time, does it add capability you don't have, and is it reliable? Apply the same criteria when you build your own in Sessions 7-8."

---

## Exercise 3: Automate a Step of Your Workflow (Throughline)

### Frame

"Which step of your workflow runs on a schedule? Let's automate it."

### Do

**Step 1:** Identify a recurring step: a daily check, a weekly summary, a regular data pull. Help the student pick one that's mechanical enough to run unattended.

🛑 **CHECKPOINT** — Confirm which step and what schedule.

**Step 2:** Create the scheduled task using `/schedule`. Set up the schedule (daily, weekly, etc.) and the prompt that defines what Claude should do.

**Step 3:** Let it run. Tell the student to check results after the first automated run and evaluate: does the output match what they'd produce manually?

### Debrief

"Let this run for a few days before Session 7. When you come back, you'll have data on whether the automation works or needs adjusting. Automation that's 90% right is still a massive time saver — the last 10% might need a human touch."

Update WORKFLOW.md: Session 6: Automated [step] on [schedule].

---

## Exercise 4: Design a Batch Workflow (Standalone)

### Frame

"Let's practice batch design on a real set of files."

### Do

**Step 1:** Help the student identify a set of files that need the same operation — reformatting, renaming, analyzing, summarizing. Can be from their workflow or any work context.

**Step 2:** Design the batch together:
- Define scope (which files, what operation)
- Set batch size (how many per round, based on context limits)
- Decide: what's mechanical (scriptable) vs. what needs judgment (manual review)?

**Step 3:** Run the first batch with "Ask before acting" to verify quality.

🛑 **CHECKPOINT** — Is the batch output correct? Any adjustments needed before running the rest?

### Debrief

"Batch processing is a repeatable pattern: scope, split, script the mechanical parts, review the judgment calls, verify per batch. It's context budgeting applied to volume work."

---

## Session Completion

### What to Remember

1. Connectors extend Claude to your actual tools via MCP. The term helps with troubleshooting.
2. Plugins bundle capabilities. Evaluate before installing — not every plugin is worth the context cost.
3. Scheduled tasks automate recurring work but require the app to be open.
4. Claude in Chrome is the fallback when connectors don't exist.
5. Batch processing: size batches to the context window, script mechanical fixes, review judgment calls.
6. Start with one connector for a tool you use daily. Add more once you see the pattern.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 6: Connected Tools & Automation** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 6 status to "Complete"
- Set Exercises Done count
- Update WORKFLOW.md "What I've Built So Far" table
- Add instructor Notes

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 7

"You've built the complete operational layer: Cowork for local work (Session 5), connectors for external tools, scheduled tasks for automation, and batch processing for volume. The next step is a mental model shift: from consumer to creator. Session 7 teaches you to build skills — packaging your expertise into reusable specifications that anyone can run. You've been using skills this entire training. Now you learn to build your own."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-7`
- If they want to break → "When you're ready to continue: go to your training project, start a new chat, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
