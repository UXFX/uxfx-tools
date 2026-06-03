---
name: session-0
description: >
  Session 0: Getting Set Up. Orients the student on what the training covers and
  what they'll build, then walks through Profile Preferences and key settings.
  Use when: STATE.md shows Session 0 in progress, or user says "session 0" or "getting set up".
user-invocable: true
---

# Session 0: Getting Set Up

Purpose: Orient the student on what this training is and what they'll build, then configure Claude so everything in Sessions 1–9 works.

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Current position |
| `agents/instructor.md` | Teaching persona |

## Writes

| File | Action |
|------|--------|
| `STATE.md` | Update position and completion |

---

## Concept 1: What You're Building Toward

### Frame

Before configuring anything, give the student the big picture. They should understand what they're signing up for and what they'll have at the end.

### Show

Walk through the three tiers and what each one produces:

**Tier 1: Foundation (Sessions 0–4)** — "I get consistently useful output."
You'll learn how to think about AI, how Claude actually works — the context window, personalization layers, and how to design Projects that make every conversation better. By the end, you'll have a purpose-built Project for your real workflow with instructions, knowledge, and handoff discipline that shape Claude's behavior.

**Tier 2: Builder (Sessions 5–7)** — "I work with Claude across sessions and tools."
You'll learn Cowork mode, connected tools, and how to build skills. Claude stops being a one-conversation tool and becomes something that produces real file output, connects to external services, and encodes your expertise. By the end, your workflow runs in Cowork with automation and a custom skill.

**Tier 3: Architect (Sessions 8–9)** — "I design reusable AI systems."
You'll learn to orchestrate multi-skill systems and package them as plugins. By the end, you'll have a fully productionized system — and the ability to design more.

### Debrief

Key point to land: "Every session applies to YOUR workflow. In Session 2, you'll choose a real workflow from your actual work. Everything after that builds on it. By Session 9, that workflow is a finished system."

One more thing: "The training portal you just received tracks all of this. Open it anytime to see where you are, review concepts, and check your progress."

---

## Concept 2: Profile Preferences

### Frame

Profile preferences shape every conversation across all of Claude. They're your standing relationship with Claude — set once, apply everywhere.

Explain briefly: these live in Settings > Profile. They affect every conversation, every project. Getting them right early saves repetition later. They don't need to be perfect now — Session 2 will refine them.

### Show

Show the student what profile preferences look like in action. Ask Claude (yourself) a question two ways:
- First, describe what you'd produce with NO preference context (generic, safe, middle-of-the-road)
- Then describe what you'd produce if someone had set preferences like: "I'm a marketing director. Be direct, skip explanations I didn't ask for, keep responses under 200 words unless I ask for more."

Point out the difference. That's what preferences do.

### Do

Walk the student through writing their initial preferences using four categories:

**WHO I AM**
Ask: "What's your role? What should Claude assume about your skills? What's your experience level with AI tools?"
Help them write 2-3 sentences that are specific and behavioral.

**COMMUNICATION STYLE**
Ask: "How do you want Claude to talk to you? Direct or gentle? Short or detailed? Should Claude ask you questions or just execute?"
Help them write preferences that describe behavior, not just adjectives.

**RESEARCH BEHAVIOR**
Ask: "Does your work involve anything that changes — market data, competitors, regulations, news? If so, should Claude research first by default?"
Help them decide whether to set a research-first default.

**FILE DISCIPLINE**
Ask: "Should Claude ask before creating files? What format do you prefer? Are there files Claude should never create without asking?"
Help them set boundaries that prevent Claude's worst habits (unsolicited documentation files, READMEs, etc.)

🛑 **CHECKPOINT** — Confirm the student has written their profile preferences in Settings > Profile.

Tell them: "These don't need to be perfect. You'll refine them in Session 2 after you've seen how they affect Claude's behavior. The point is to start with something rather than nothing."

### Debrief

Confirm they've saved their preferences. Tell them that in Session 2, Exercise 2 specifically tests whether these preferences are pulling their weight — so they'll get a chance to tighten them up.

---

## Concept 3: Settings That Matter

### Frame

Three settings affect the rest of the training. Quick configuration, no theory.

**Navigation note for the student:** Settings in Claude Desktop can feel scattered — some live in the Settings panel (gear icon), others live inside conversations. When walking through each setting below, give the student explicit step-by-step navigation: where to click, what to look for, and how to get back to this conversation afterward. Don't assume they know the UI layout yet.

### Show + Do (combined — these are just toggles)

Walk the student through:

1. **Memory** — Settings > Capabilities > Memory. Turn it on. Explain in one sentence: "This lets Claude learn about you across conversations. We'll explore how it works — and its limits — in Session 2."

2. **Approval mode for Cowork** — This isn't in Settings — it's inside each Cowork conversation. When you start a Cowork task, look for the approval mode control in the chat interface. Recommend "Ask before acting" for training. Explain: "This means Claude will show you what it wants to do before doing it. You'll switch to autonomous mode later when you trust your workflows." Walk the student through finding it so they're not hunting for it in the settings panel.

3. **Model selector** — Show them where it is. Don't explain models yet — Session 2 covers model selection. Just confirm they can see and switch models.

🛑 **CHECKPOINT** — Confirm all three settings are configured.

### Debrief

One sentence: "You're configured. These settings will make more sense as you use them — Session 2 explains why each one matters."

---

## Session Completion

Update STATE.md:
- Set Session 0 status to "Complete"
- Set Session 1 status to "Not Started"
- Clear Position concept/phase

Invoke `portal` skill to regenerate the progress portal.

**Surface progress in-chat:** Present the updated portal HTML and learning journal as clickable artifacts in the conversation. The student should be able to see their progress without leaving this chat.

Bridge to Session 1:
"Session 0 was orientation and setup. Session 1 is where the learning starts — you'll learn the mental model shift that makes everything else in this training click."

**Clear next steps:**
- If they want to continue now → "Ready to keep going?" → invoke `session-1`
- If they want to break → "When you're ready to continue: go to your training project, start a new chat, and say 'continue training.' Your progress is saved — you'll pick up right where you left off."
