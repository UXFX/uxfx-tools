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

Update date and meta-teaching note (appears automatically after Session 5 and expands after Session 8 — handled by template logic).

---

## Everything Else Is the Template's Job

The concept lists, session content, stack layers, full design system (fonts, colors, dark/light themes, breakpoints, interactions), and the meta-teaching footer notes all live hardcoded in `templates/portal.html`. The skill never writes markup, styles, or static data — it only patches the dynamic fields listed above. If session content changes in a future plugin version, update the template directly.
