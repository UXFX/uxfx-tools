# uxfx-tools — Marketplace State

Source of truth for what is published in this marketplace and where each plugin stands in the pipeline.

- **Public storefront:** this repo (`uxfx-tools/`). Only gate-passed plugins live in `plugins/`.
- **Authoring master:** `~/Documents/GitHub/uxfx-workshop/<plugin>/` — where plugins are created and updated.

## Publishing model

1. Author / update each plugin in its workshop folder: `uxfx-workshop/<name>/plugin/`.
2. Run the gate (`uxfx-workshop/_gate/GATE.md`). On pass, promote (copy) `plugin/` → `uxfx-tools/plugins/<name>/`.
3. Add or update the plugin's entry in `.claude-plugin/marketplace.json`.
4. `version` lives in `plugin.json` only — never duplicated in `marketplace.json` (if set in both, `plugin.json` wins silently). Bump it on every release.
5. Validate before pushing: `claude plugin validate .`

## Pipeline

| Plugin | Workshop master | Published | Gate | Notes |
|--------|-----------------|-----------|------|-------|
| premise | v1.1.0 | **v1.1.0** | ✅ PASS (2026-06-07) | run-3 patches: 4 SKILL.md ambiguity fixes |
| foundry | — | → moved to `uxfx-pro` | ✅ PASS (2026-05-31) | split out to private marketplace 2026-05-31; tracked in `uxfx-pro/STATE.md` |
| context-engineering-training | v0.4.0 | **v0.4.0** | ✅ PASS (2026-06-15) | two-dials teaching unit: reliability vs judgment stops (S5 seed + S9 principle) |

## Notes

- Marketplace name `uxfx-tools` checked against Anthropic's reserved/blocked list (docs, 2026-05-31) — clear.
- `$schema` uses schemastore.org URL (resolves; drives editor validation). Claude Code ignores it at load.

## Changelog

- 2026-05-31 — Repo scaffolded. Empty marketplace; no plugins promoted yet.
- 2026-05-31 — foundry v1.4.0 promoted (first plugin). Gate first-pass blocked on a denylist hit in the twin-retype skill; scrubbed; re-passed.
- 2026-05-31 — context-engineering-training v0.1.0 promoted (2nd plugin). Gate: added missing YAML frontmatter to instructor agent; denylist clean.
- 2026-05-31 — premise v1.0.0 promoted (3rd plugin). Gate clean (0 denylist hits, 0 junk). Shipped at 1.0.0 per owner; workshop STATE.md draft note treated as stale.
- 2026-05-31 — Split: foundry moved to private marketplace `uxfx-pro`. `uxfx-tools` is now PUBLIC, holding premise + context-engineering-training only.
- 2026-06-07 — Added `GETTING-STARTED.md` (repo root): end-user onboarding — Claude Desktop install (macOS/Windows), add marketplace, install plugins, first-run walkthroughs, updating to new versions. Steps verified against support.claude.com articles 10065433 and 13837440, then corrected against the live Desktop UI (owner screenshots). Denylist scan clean.
- 2026-06-07 — Hygiene: reworded a 2026-05-31 changelog line that named an internal codename (denylist term in public repo); refreshed stale pipeline-table versions; gitignored `.gate-cache`.
- 2026-06-09 — context-engineering-training v0.3.0 promoted (capability-currency release: styles retirement, thinking modes, compaction). Gate all-PASS — see GATE.md. (Backfilled 2026-06-15; the pipeline table had lagged at v0.2.0.)
- 2026-06-15 — context-engineering-training v0.4.0 promoted. New teaching unit: autonomy as two dials (reliability + judgment) — S5 Approval Modes seed + S9 design principle "Decide where you stay in the loop." Gate all-PASS; denylist 0 hits in `plugin/` + 0 across full uxfx-tools history. Marketplace manifest bumped 1.1.0→1.2.0 (cache refresh).
