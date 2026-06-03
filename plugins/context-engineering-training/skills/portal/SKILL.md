---
name: portal
description: >
  Generate an interactive HTML progress portal from STATE.md and WORKFLOW.md.
  Session-centric design: hero card (what's next), vertical timeline with expandable
  session details (concepts, exercises, workflow), searchable quick reference, and
  collapsible Claude Stack. Updates at each session completion. Use when: a session
  completes, or user says "show portal", "update portal", "my progress", or "generate portal".
user-invocable: true
---

# Progress Portal

Generate a single-file, offline-capable HTML page that visualizes the student's training progress. This is both a practical reference tool and a meta-teaching device — it demonstrates artifacts, skills, and orchestration patterns the student is learning about.

## When to Generate

- After each session completion (called by session skills at their completion step)
- On student request ("show portal", "my progress")
- After the `start` skill completes initial setup

## Reads

| File | What You Need |
|------|---------------|
| `STATE.md` | Session progress, exercises done, tier status, student info, notes |
| `WORKFLOW.md` | Workflow description and "What I've Built So Far" table |
| `templates/portal.html` | HTML template with `%%DATA_PLACEHOLDER%%` marker |

## Writes

| File | Action |
|------|--------|
| `training-portal.html` | Inject data into template and write to student's workspace root |

---

## How It Works: Targeted Field Injection

The portal is a self-contained HTML template (`templates/portal.html`) with an embedded JavaScript data object containing default values for ALL fields — sessions, exercises, concepts, sessionContent, stackLayers, etc. Most of this data is static and lives in the template permanently. The skill's job is to inject ONLY the dynamic student data by patching specific fields. Never replace the entire data object.

### Steps

1. **Read STATE.md and WORKFLOW.md** — Extract student progress data
2. **Read templates/portal.html** — Load the HTML template as a string
3. **Patch dynamic fields** — Use targeted string replacements on specific fields (see below)
4. **Write the completed HTML** — Save to `training-portal.html` in the student's workspace root

### What to Patch (and What to Leave Alone)

**PATCH these fields** (they change per student):

| Source | Target in template | How to patch |
|---|---|---|
| Student name from STATE.md | `student: { name: "", started: "" }` | Replace with actual name and start date |
| Today's date | `lastUpdated: ""` | Replace with current date |
| Session statuses from STATE.md progress table | Each session's `status: "not-started"` | Change to `"completed"` or `"in-progress"` per STATE.md. Map: "Complete" → "completed", "In Progress" → "in-progress" |
| Exercise counts from STATE.md | Each session's `exercisesDone: 0` | Replace with actual count from STATE.md |
| Exercise statuses | Each exercise's `status: "not-done"` in the `exercises` object | Mark exercises as `"done"` based on exercisesDone count per session. Mark in order. If notes mention skipped exercises, mark those as `"skipped"` |
| Workflow description from WORKFLOW.md | `workflow: { description: "", builtSoFar: [] }` | Replace with actual description and built-so-far entries |

**DO NOT TOUCH these fields** (they are hardcoded in the template and must stay):
- `concepts` — All concept names and descriptions per session
- `sessionContent` — Big ideas, what-to-remember, exercise descriptions
- `stackLayers` — Claude Stack visualization data
- Session `title`, `tier`, `exercisesTotal` — Static session metadata
- Exercise `name` and `type` — Static exercise metadata
- Everything outside the `TRAINING_DATA` object (HTML, CSS, JS functions)

### How to Do the Replacements

Use simple string find-and-replace on the template text. Examples:

**Student info:**
Find: `student: { name: "", started: "" }`
Replace with: `student: { name: "Dale", started: "2026-05-20" }`

**Last updated:**
Find: `lastUpdated: ""`
Replace with: `lastUpdated: "2026-05-23"`

**Session status** (do for each completed/in-progress session):
For session 0, find the line containing `id: 0` and on that same line change `status: "not-started"` to `status: "completed"` and `exercisesDone: 0` to `exercisesDone: N`.

**Workflow:**
Find: `workflow: { description: "", builtSoFar: [] }`
Replace with the populated version including description and array of `{ session: N, description: "..." }` entries.

**Exercise statuses:**
For each session with completed exercises, find the exercise entries in the `exercises` object and change `status: "not-done"` to `status: "done"` for the appropriate number of exercises (in order).

### Why Targeted Patching

The template contains ~250 lines of static data (concepts, sessionContent, stackLayers) that the skill doesn't need to regenerate. Replacing the entire data object risks:
- Dropping fields the skill doesn't know about
- Breaking if the template adds new fields in a future version
- Producing invalid JS from JSON serialization edge cases (curly quotes in strings, etc.)

Targeted patching means the template is always the source of truth for static content. The skill only touches what actually changes per student.

This preserves the placeholder comment (for future updates) while injecting the real data.

---

## Portal Sections (Session-Centric Design)

The portal organizes around the student's journey through sessions, not around data types. This means concepts, exercises, and workflow contributions are nested inside each session — not scattered across separate sections.

### 1. Header

- Title: "Context Engineering Training"
- Student name, session count ("Session N of 10"), current tier badge
- Theme toggle (dark/light)

### 2. Hero Card (What's Next)

A prominent card showing the current or next session. Adapts to three states: welcome (no sessions started), continue (session in progress with exercise count), or up next (next not-started session). Shows session title, tier, and encouraging microcopy. If all sessions complete, shows congratulations.

### 3. Session Journey (Vertical Timeline)

The heart of the portal. A vertical path with all 10 sessions as nodes.

**Completed/in-progress sessions** are expandable (click to toggle). When expanded, they show:
- **Concepts** — as compact pills with tooltips showing descriptions
- **Exercises** — with status icons (✓ done, ⏭ skipped, ○ not done) and type badges (throughline/standalone)
- **Workflow contribution** — one line from the `builtSoFar` data for that session

**Not-started sessions** are clickable and open the detail modal (same as completed/in-progress), so students can preview what's coming. Text is slightly muted to distinguish from active sessions.
**Tier labels** appear inline as section headers before each tier group: "Tier 1: Foundation", "Tier 2: Builder", "Tier 3: Architect".

### 4. Quick Reference

A searchable concept glossary below the timeline. Shows concepts from ALL completed/in-progress sessions. Each entry shows: concept name (pill), one-line description, session number. Real-time text filtering via search input. This is the study companion — what students return to between sessions.

### 5. Claude Stack (Collapsible)

Appears only after at least one session is complete. Collapsible section (collapsed by default). Shows the incremental layer diagram — learned layers styled normally, future layers muted with session badges showing when they'll be introduced.

### 6. Footer

Update date and meta-teaching note (appears after Session 5 or Session 8 per the spec).

**Concept list by session:**

Session 1:
- Mental model shift — Stop asking questions, start giving context. Thinking partner, not search engine.
- What AI is good and bad at — Evaluate before you trust. Claude can be confidently wrong.
- Prompt anatomy — Role, Task, Context, Constraints. Diagnostic checklist when output disappoints.
- Thinking vs execution — Think first, produce second. Catch bad assumptions before they compound.

Session 2:
- Context window — Your finite resource. Everything loaded has a cost.
- Personalization stack — Five layers shape behavior: preferences, instructions, styles, memory, conversation.
- Memory — Useful for continuity, unreliable for precision. Use files for project state.
- Research — Claude's training data is frozen. Anything current needs research first.
- Model selection — Match reasoning power to task complexity. Start default, switch up or down.
- Extended thinking — Encourages Claude to reason before responding. Pair with stronger models for hard problems.
- Conversation as unit — Quality comes from the conversation, not the prompt.

Session 3:
- One Project per workstream — Don't overload a single Project with everything.
- Project instructions — Your standing brief. Set context once.
- Project knowledge — Two approaches: UI uploads (stable content) or file system (evolving content).
- Styles — Voice and tone control. Format, not substance.
- Context budgeting — Load only what this conversation needs. High-signal beats high-volume.

Session 4:
- Session endings — Context full, topic drifting, or natural breakpoint. Recognize which.
- Handoff file — The connective tissue between sessions. No file, no continuity.
- Transition prompts — Bootstrap fresh conversations: CONTEXT, WHAT JUST HAPPENED, TASK, GUARDRAILS.
- Two-layer system — Lean master checklist + focused session kickoffs. Prevents context overload.
- Guardrails — Explicit scope boundaries prevent Claude from going off-script.

Session 5:
- Cowork mode — File access + code execution + sub-agents + document creation. Claude as operator.
- Approval modes — "Ask before acting" for learning, "Act without asking" for trusted workflows.
- Artifacts — Standalone content in a dedicated panel. Deliverables that live outside the conversation.
- Sub-agents — Parallel work with isolated context. A context management technique.
- Research in Cowork — Research first, save to file, review, then produce. Explicit step, not assumption.
- Error recovery — Three failure modes: context exhaustion, tool failures, scope drift.

Session 6:
- Connectors — Extend Claude to external services via MCP. Knowing the term helps with troubleshooting.
- Plugins — Bundled capabilities. Evaluate before installing.
- Scheduled tasks — Recurring automation. Requires app open.
- Claude in Chrome — Browser extension fallback when connectors don't exist.
- Batch processing — Size batches to context window. Script mechanical fixes, manual for judgment.

Session 7:
- Skills — Encode expertise, not just instructions. Define HOW to think.
- Decision framework — Chat → Project → Skill → Plugin. Cost increases, so does return.
- Creating skills through conversation — Turn into skill: Claude builds your SKILL.md through conversation. 80% path.
- SKILL.md anatomy — Role, process stages, quality gates, behavioral constraints, triggers. The deeper 20%.
- CLAUDE.md — Project-level configuration in the file system. Travels with the project.

Session 8:
- One skill per phase — Split workflows into skills that each handle one type of thinking.
- State file — Shared clipboard between skills. Plain markdown, read at start, updated at end.
- Gates — Preconditions preventing shortcuts. Without them, Claude skips steps.
- Orchestrator — Reference map, not a program. Describes the flow so Claude knows where it is.
- Plugins (building) — Package multi-skill systems for distribution.
- Review pipelines — Separate creation from critique using sub-agents and different skills.

Session 9:
- The Claude Stack — All layers, all levels. Right information at the right level.
- Design for others — Clear instructions, well-named skills, intuitive structure. Members vs. Editors.
- Start with one workflow — Full stack for one, then expand.
- Maintain your system — Stale instructions and outdated skills degrade quality.

---

## HTML Generation Guidelines

### Design System: Foundry Portal

Use the same design system as the Foundry plugin portal. This ensures visual consistency if the student uses both plugins, and inherits a proven, polished design.

**Required resources:**
- Google Fonts: Inter (weights 400, 500, 600, 700)
- Material Symbols Rounded icon font

### Core Design Tokens

Use Foundry's CSS custom properties verbatim:

**Gray scale:** `--color-primitive-gray-950: #0a0a0b` through `--color-primitive-gray-50: #fafafa`, plus `--color-primitive-white: #ffffff`

**Brand:** `--color-primary-default: #6366f1`, `--color-primary-gradient: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%)`

**Status:** success `#22c55e`, warning `#f59e0b`, error `#ef4444`, info `#0ea5e9` — each with a muted variant at 0.15 opacity

**Typography:**
- `--font-family-base: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`
- `--font-family-mono: 'SF Mono', 'Fira Code', 'Consolas', monospace`
- Sizes: display 36px, h1 28px, h2 24px, h3 20px, body-lg 18px, body 16px, body-sm 14px, caption 12px, overline 11px
- Weights: regular 400, medium 500, semibold 600, bold 700

**Spacing (8px base):** `--space-1: 4px` through `--space-16: 64px`

**Shape:** `--radius-sm: 4px`, `--radius-md: 8px`, `--radius-lg: 12px`, `--radius-xl: 16px`, `--radius-full: 9999px`

**Motion:** `--transition-fast: 150ms ease`, `--transition-normal: 200ms ease`, `--transition-slow: 300ms ease`

### Dark Theme (Default)

- Background: `--color-bg: #121214`, elevated surfaces: `#18181b`, `#1f1f23`, `#27272a`
- Text: primary `#ffffff`, secondary `#e4e4e7`, tertiary `#a1a1aa`, muted `#71717a`
- Borders: subtle `rgba(255,255,255,0.06)`, default `rgba(255,255,255,0.1)`, hover `rgba(255,255,255,0.2)`
- Shadows: sm `0 2px 8px rgba(0,0,0,0.3)`, md `0 8px 24px rgba(0,0,0,0.4)`, lg `0 16px 48px rgba(0,0,0,0.5)`

### Light Theme (data-theme="light")

- Background: `#f8f8fa`, elevated: `#ffffff`, `#f0f0f3`, `#e4e4e7`
- Text: primary `#0a0a0b`, secondary `#27272a`, tertiary `#52525b`, muted `#71717a`
- Borders: subtle `rgba(0,0,0,0.06)`, default `rgba(0,0,0,0.12)`, hover `rgba(0,0,0,0.2)`
- Shadows: sm `0 2px 8px rgba(0,0,0,0.06)`, md `0 8px 24px rgba(0,0,0,0.08)`, lg `0 16px 48px rgba(0,0,0,0.12)`

### Training-Specific Spectrum Colors

Map Foundry's spectrum to training entity types:

| Entity | Spectrum | Color | Use |
|--------|----------|-------|-----|
| Tier 1: Foundation | spectrum-2 | `#6366f1` (indigo) | Session nodes, badges |
| Tier 2: Builder | spectrum-4 | `#10b981` (emerald) | Session nodes, badges |
| Tier 3: Architect | spectrum-1 | `#8b5cf6` (violet) | Session nodes, badges |
| Exercise (throughline) | spectrum-5 | `#84cc16` (lime) | Exercise markers |
| Exercise (standalone) | spectrum-3 | `#06b6d4` (cyan) | Exercise markers |
| Concept | spectrum-7 | `#0ea5e9` (sky) | Concept reference items |

### Component Patterns to Reuse from Foundry

**Portal layout:** `.portal`, `.portal-header`, `.portal-section`, `.portal-footer` — same structure, padding, borders.

**Cards:** `.entity-card` pattern for session cards in the progress map — background, border, radius, hover lift.

**Status badges:** `.status-badge` with `.dot` indicator — reuse for session status (Complete, In Progress, Not Started).

**Phase timeline:** `.phase-timeline` with `.phase-badge` — adapt for tier navigation (Foundation / Builder / Architect tabs).

**Stat rows:** `.stat-row` pattern for the header stats (sessions complete, exercises done, current tier).

**Theme toggle:** `.theme-toggle` with `.theme-toggle-btn` — same light/dark switch.

**Collapsible sections:** Use Foundry's expand/collapse pattern for the exercise log per session.

**Confidence bars:** `.confidence-row` with `.confidence-track` and `.confidence-fill` — repurpose for session completion progress bars.

### Responsive Breakpoints

Match Foundry: 1024px (tablet) and 768px (mobile). Session cards switch to single column on mobile. Portal header stacks vertically.

### Interactions

- Theme toggle (dark/light)
- Collapsible exercise log sections per session
- Hover states on session nodes showing exercise details
- Claude Stack layers highlight on hover showing which session introduced them
- Tier tab filtering in the progress map
- Vanilla JS only — no framework dependencies

### Meta-Teaching Note

After Session 5 (which teaches artifacts), add a subtle note to the portal footer:
"This portal is an artifact generated by a skill inside an orchestrated plugin — concepts from Sessions 5, 7, and 8 in action."

After Session 8 (which teaches orchestration), expand the note:
"This portal is generated by the `portal` skill, triggered by the orchestrator at session completion, reading from STATE.md and WORKFLOW.md. You now know how to build systems like this yourself."
