---
name: session-2
description: >
  Session 2: How Claude Actually Works. Teaches the context window, personalization stack,
  memory, research, model selection, extended thinking, and conversation as unit of work.
  Four exercises including choosing the throughline workflow. Use when: STATE.md shows
  Session 2, or user says "session 2" or "how claude works".
user-invocable: true
---

# Session 2: How Claude Actually Works

The Big Idea: Claude is a reasoning partner with a finite context window. Everything — output quality, session length, what Claude "knows" — comes down to what's in that window and how well you manage it. This is context engineering.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position, student info |
| `WORKFLOW.md` | Student's workflow (from Session 1 or initially blank — gets filled in Exercise 1) |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position, exercises done, notes |
| `WORKFLOW.md` | Populate with student's workflow (Exercise 1) |
| `learning-journal.md` | Append Session 2 takeaway at session end |

---

## Concept 1: The Context Window — Your Finite Resource

### Frame

Set up the core mental model. Most people treat Claude like a search engine — type a question, get an answer. The real model: you're managing a context window. Everything Claude can "see" lives in that window: your messages, Claude's responses, files, project instructions, memory, tool outputs. There's a hard limit. When it fills up, earlier context drops out.

This single concept — the context window as a finite resource — is the foundation of everything in the training. Every technique from here forward is a strategy for managing this constraint.

### Show

Demonstrate the context window in action. Do this conversationally:

1. Point out what's currently loaded in this conversation: the plugin instructions, the student's state file, the agent persona, this skill file, and the conversation itself. All of that is context. All of it consumes tokens.

2. Explain what would happen if you kept adding — loading more files, having a longer conversation, asking Claude to hold more information. Eventually, the earliest parts of the conversation would start getting pushed out.

3. Make it concrete: "Right now, this training plugin is using context to teach you about context. The skill file I'm following, the instructor persona shaping how I talk to you, your state file tracking progress — all of that is in the window alongside our conversation. If we loaded a 50-page document on top of all that, something would have to give."

### Debrief

Check: "Does the context window concept make sense? Think of it as Claude's working memory — everything has to fit, and what doesn't fit gets forgotten. The rest of this session teaches you what goes into that window and how to control it."

### Quick Check

"Say you're working on [student's workflow] and you load a long reference document, detailed project instructions, AND start a complex conversation. What's the trade-off you're making?"

🛑 **CHECKPOINT** — Wait for the student's answer. They should identify that loading more context leaves less room for the conversation itself, or that earlier context may get pushed out. If they frame it as a resource management problem, they've got it.

---

## Concept 2: The Personalization Stack

### Frame

Claude's behavior is shaped by layers, from broadest to narrowest. Each layer adds context to the window. The more relevant that context, the better the output. The more irrelevant, the worse.

### Show

Walk through the five layers, demonstrating each one:

1. **Profile preferences** — "Remember the preferences you wrote in Session 0? Those are shaping how I'm talking to you right now. If you told me to be concise, I'd give shorter answers. If you told me you're a developer, I'd use different language. That's Layer 1 — account-wide, applies everywhere."

2. **Project instructions** — "Projects are persistent workspaces where context carries across conversations. You haven't created one yet — that's Session 3. When you do, the instructions you write will be loaded into every conversation in that Project. It's like onboarding a new team member once instead of re-explaining everything each time."

3. **Styles** — "Claude has four preset styles — Normal, Concise, Formal, Explanatory — plus custom styles. These control how I deliver information, not what I know. Useful for maintaining consistent voice."

4. **Memory** — "I have some memory of past conversations with you. It's useful for continuity — knowing your preferences, recurring context — but unreliable for precise facts. We'll test this in Exercise 3."

5. **The conversation itself** — "Everything we've said so far in this chat. This is the most immediate context, and it's growing with every message. Eventually it'll push out the earliest parts of our conversation."

Key point to land: each layer takes up space in the context window. Loading all five layers with dense content leaves less room for the actual conversation. This tradeoff — persistent context vs. conversation space — is the core tension of context engineering.

### Debrief

"Five layers, one window. The skill isn't knowing they exist — it's knowing how much to put in each one. Session 3 goes deep on that. For now, just hold the mental model: layers shape behavior, layers consume tokens, and you control what's in them."

### Quick Check

"If you wanted Claude to always use a specific tone in every conversation — not just this one — which layer of the personalization stack would you put that in, and why?"

🛑 **CHECKPOINT** — Wait for the student's answer. Profile preferences or styles are both valid — the key insight is that it should go in a persistent layer, not the conversation. If they say "project instructions," clarify that those are per-project, not account-wide.

---

## Concept 3: Memory — What Claude Remembers (and Doesn't)

### Frame

Memory is the most misunderstood feature. People either over-rely on it (expecting Claude to remember project details precisely) or ignore it entirely. The truth: memory generates summaries from your conversations that persist across chats. Useful for personal preferences and recurring context. Not reliable for specific facts, project state, or anything that needs to be exactly right.

Incognito chats exist for conversations you don't want affecting memory.

### Show

Demonstrate memory's boundaries:

1. Share something specific the student told you in this session (or earlier) and show whether memory captured it.
2. Explain what memory tends to retain well (preferences, broad patterns, recurring topics) versus what it drops (specific numbers, exact file paths, precise project state).
3. Mention incognito mode: "If you want to explore something without it affecting what Claude remembers about you, use an incognito chat."

### Debrief

"Memory is continuity, not storage. It helps Claude know who you are over time. It does NOT replace files for anything you need to be precise. In Session 4, you'll build a file-based system for project state that doesn't depend on memory at all."

### Quick Check

"You're tracking a list of 15 key decisions made across a multi-week project. Would you trust memory to keep that list accurate? What would you use instead?"

🛑 **CHECKPOINT** — Wait for the student's answer. They should say no to memory and suggest a file. If they're unsure, reinforce: memory retains patterns and preferences, not specific lists or facts.

---

## Exercise 1: Choose Your Workflow (Throughline)

This is the most important exercise in the entire training. The student picks the workflow they'll build across all 9 sessions.

### Frame

"Every session from here forward applies its concepts to YOUR workflow. You're not doing abstract exercises — you're building a working system, one layer at a time. So the choice matters: pick something real."

### Do

Guide the student through choosing their workflow:

**Step 1: Identify candidates**
Don't put the student on the spot with a blank page. Use what you already know — their role, their industry, what they mentioned in Sessions 0-1 — to offer 2-3 concrete workflow suggestions tailored to their situation. Frame it as: "Based on what you've told me about your work, here are some workflows that could work well for this training — or tell me something completely different."

Then ask: "Do any of these resonate, or do you have something else in mind?"

🛑 **CHECKPOINT** — Wait for their choice or alternative. If they're still stuck, ask about their typical week: "Walk me through a typical Monday. What takes the most time? What do you wish was already done when you sat down?" Help them find the workflow in their own routine.

**Step 2: Evaluate against criteria**
For each candidate, check:
- Is it genuinely part of your work? (Not a toy example)
- Do you do it at least weekly?
- Does it involve multiple steps or decisions?
- Would you be relieved to have it running well by Session 9?

Help them pick one. If they're torn, pick the one they do most often — frequency means more practice reps.

**Step 3: Describe the workflow**
Ask them to describe it in plain language:
- What triggers it?
- What steps do you take?
- What does the output look like?
- Where's the pain?

🛑 **CHECKPOINT** — Wait for their description.

**Step 4: Write it down**
Update `WORKFLOW.md` with their answers. This file travels with them through the entire training.

**Step 5: First context engineering test**
Now demonstrate context engineering on their workflow:

a. Ask Claude (yourself) to help with one step of their workflow using a bare, context-free framing. Produce output.

b. Then ask the same question but with full context: role framing ("You're helping a [role] who does [workflow] every [frequency]"), task specificity, constraints, and domain context from what they just told you. Produce output.

c. Compare the two outputs explicitly. Point out what changed and why. "The second version is better because it had context. The context window had more relevant information to work with. That difference — between a bare prompt and a contextual prompt — is context engineering."

### Debrief

"You've chosen your workflow and seen context engineering in action on your own work. From here forward, every session adds a layer to this workflow. By Session 9, it'll be a fully productionized system."

Update WORKFLOW.md with what was built in this exercise.

---

## Concept 4: Research — When Training Data Isn't Enough

### Frame

Claude's training data has a cutoff date. Everything it "knows" is frozen at that point. Anything current — market data, events, competitors, regulations, pricing — needs to be researched, not recalled.

This matters more than people realize. Claude will produce confident, well-structured output based on stale data without warning you. The habit to build: any time your work touches information that changes, tell Claude to research first, then produce.

### Show

Demonstrate with a real example connected to the student's workflow:

1. Ask yourself a question about the student's domain that involves current information (e.g., current pricing, recent industry trends, latest tools). Answer from training data first — note the uncertainty and potential staleness.

2. Then research the same question using web search. Compare what you find to what training data said.

3. Point out: "I gave you a confident answer from training data. It might have been wrong. The researched answer is verifiable. The habit is: research first when the information changes."

### Debrief

"Research is a context engineering decision. When you tell Claude to research first, you're choosing to fill the context window with current, verified information instead of stale training data. We'll make this operational in Session 5 when you start using Cowork for research workflows."

### Quick Check

"Think about your workflow — [reference their specific workflow]. Is there a step where Claude might confidently produce an answer using stale training data instead of current information? Which step, and how would you catch it?"

🛑 **CHECKPOINT** — Wait for the student's answer. Any step that touches current data (pricing, competitors, regulations, recent events, tool versions) is valid. The key insight is recognizing where staleness hides.

---

## Concept 5: Choosing the Right Model

### Frame

Claude comes in multiple models. The core tradeoff: reasoning depth versus speed. Stronger models (Opus) think harder — use for nuanced analysis, complex decisions, anything where getting it wrong is expensive. Faster models (Sonnet, Haiku) are better for straightforward tasks and high volume.

Model selection is a context engineering decision: you're choosing how much reasoning power to apply.

### Show

Describe the practical difference:
- "If I asked Haiku to analyze a complex contract, it would miss nuances that Opus would catch. But if I asked Opus to rename 50 files, it would be slower for no quality gain."
- Relate to the student's workflow: identify which steps need deep reasoning vs. which are mechanical.

### Debrief

"The heuristic: start with the default model. If output feels shallow, switch up. If you're doing repetitive work where quality is good enough, switch down. Session 2 Exercise 4 lets you feel this difference on your own workflow."

---

## Concept 6: Extended Thinking

### Frame

Extended thinking lets Claude work through complex problems before responding. It activates automatically for hard problems but can be encouraged. Think of it as asking Claude to think before speaking — useful for multi-step analysis, complex decisions, or anything where a human would need to think first.

### Show

Briefly explain how extended thinking pairs with model selection: "A stronger model with extended thinking is the highest-quality configuration. Reserve it for work that justifies the time."

### Debrief

"You now know the three quality levers: what context you provide (context engineering), which model you use (model selection), and whether Claude thinks before responding (extended thinking). Exercise 4 tests all three."

### Quick Check

"In your workflow, which step would you throw the most reasoning power at — stronger model, extended thinking, the works — and which step would you deliberately use a faster model for?"

🛑 **CHECKPOINT** — Wait for the student's answer. They should match high-judgment steps to stronger models and mechanical/repetitive steps to faster ones. If they say "strongest model for everything," push back on the speed trade-off.

---

## Concept 7: The Conversation Is the Unit of Work

### Frame

A single prompt rarely produces great output. A conversation — where you provide context, evaluate output, give feedback, and refine — is where real value happens.

### Show

Point to this session itself: "We've been having a conversation for a while now. You've given me context about your workflow, I've demonstrated concepts, you've asked questions. The quality of what I'm producing right now is shaped by everything that came before in this conversation. A single prompt couldn't have gotten us here."

### Debrief

"Think of each Claude session as a working session with a smart colleague, not a search query. The conversation builds context. The context improves output. That's the loop."

---

## Exercise 2: The Personalization Stack in Action (Standalone)

### Frame

"In Session 0, you wrote profile preferences. Let's test whether they're actually working."

### Do

**Step 1:** Ask the student to give you a task prompt — something simple from their work domain.

🛑 **CHECKPOINT** — Wait for their prompt.

**Step 2:** Run the prompt and show how the output reflects (or doesn't reflect) their profile preferences. Point to specific choices in the output: "I used this tone because your preferences say X." Or: "Notice I didn't adjust for your domain expertise — your preferences don't mention it."

**Step 3:** Have them test with a Style applied (Concise, Formal, etc.) and see the difference.

**Step 4:** Now have them go back to their profile preferences and refine based on what they've seen. Ask: "Are your preferences specific enough to change my behavior, or are they vague labels I'm ignoring?"

🛑 **CHECKPOINT** — Confirm they've updated their preferences.

### Debrief

"Profile preferences are your first layer of context engineering. Specific, behavioral preferences shape every conversation. Vague ones get ignored. This is a pattern you'll see at every level — specificity wins."

---

## Exercise 3: Memory Observation (Standalone)

### Frame

"Let's map memory's actual boundaries."

### Do

**Step 1:** Ask the student to tell you three specific things about their work:
- One fact (a number, a name, a date)
- One preference (how they like something done)
- One piece of context (what they're working on right now)

🛑 **CHECKPOINT** — Wait for their three things.

**Step 2:** Acknowledge what they said. Then explain: "If you ended this conversation and started a new one, memory might retain the preference and the context. The specific fact is less likely to survive intact. And if you used an incognito chat, none of it would be stored."

**Step 3:** Encourage them to test this after the session — start a new conversation and see what Claude remembers. Then try incognito.

### Debrief

"Memory is useful for continuity, not precision. Don't depend on it for project state, specific numbers, or anything that needs to be exactly right. In Session 4, you'll build a file-based system that handles precision — memory handles vibes."

---

## Exercise 4: Model Selection & Extended Thinking (Throughline)

### Frame

"Let's feel the difference between models on your actual workflow."

### Do

**Step 1:** Identify the most complex step of their workflow — the one that requires the most judgment.

🛑 **CHECKPOINT** — Confirm which step.

**Step 2:** Guide them through running that step three ways:
a. With a faster model (Sonnet or Haiku)
b. With a stronger model (Opus)
c. With the stronger model and a prompt that encourages extended thinking ("Think through this step by step before responding")

Have them compare reasoning depth across the three outputs.

**Step 3:** Now run a mechanical step from their workflow the same three ways. Notice where the difference stops mattering.

### Debrief

"For your complex step, the stronger model probably produced noticeably better output. For the mechanical step, the difference was minimal or irrelevant. That's your heuristic: invest reasoning power where it matters, save it where it doesn't. This is a context engineering decision you'll make constantly."

---

## Session Completion

### What to Remember

Present these as a summary, not a lecture:

1. The context window is finite. Everything loaded into it has a cost.
2. Five layers shape Claude's behavior: profile preferences, project instructions, styles, memory, conversation. Each consumes tokens.
3. Claude's training data is frozen. Anything current needs research.
4. Model selection matches reasoning power to task complexity.
5. Memory is continuity, not storage. Use files for precision.
6. The conversation — not the prompt — is where quality happens.

### Append to Learning Journal

Append to `learning-journal.md` in the student's workspace. Include:

1. **Session 2: How Claude Actually Works** — date
2. **Key moments** — What the student tried, what clicked, what surprised them. Reference their specific work from the session's exercises.
3. **What worked** — Which concepts the student applied effectively (name the specific technique).
4. **What to practice** — Areas that need more work. Be specific.
5. **Principles demonstrated** — Connect their hands-on work back to the session's concepts.

Keep it concise — under 30 lines.

### Update State

Update STATE.md:
- Set Session 2 status to "Complete"
- Set Exercises Done: count of completed exercises
- Update WORKFLOW.md "What I've Built So Far" table
- Add any instructor Notes about what clicked vs. what was hard

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should see their progress without leaving this chat.

### Bridge to Session 3

"Session 2 gave you the mental model. Session 3 teaches you to architect it — you'll build a real Project for your workflow with instructions, knowledge, and styles that make Claude consistently good at your specific work."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-3`
- If they want to break → "When you're ready to continue: go to your training project, start a new chat, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
