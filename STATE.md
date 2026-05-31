# uxfx-tools — Marketplace State

Source of truth for what is published in this marketplace and where each plugin stands in the pipeline.

- **Public storefront:** this repo (`uxfx-tools/`). Only gate-passed plugins live in `plugins/`.
- **Authoring master:** `~/Documents/GitHub/uxfx-workshop/<plugin>/` — where plugins are created and updated.

## Publishing model

1. Author / update each plugin in its workshop folder: `uxfx-workshop/<name>/plugin/`.
2. Run `GATE.md`. On pass, promote (copy) `plugin/` → `uxfx-tools/plugins/<name>/`.
3. Add or update the plugin's entry in `.claude-plugin/marketplace.json`.
4. `version` lives in `plugin.json` only — never duplicated in `marketplace.json` (if set in both, `plugin.json` wins silently). Bump it on every release.
5. Validate before pushing: `claude plugin validate .`

## Pipeline

| Plugin | Workshop master | Published | Gate | Notes |
|--------|-----------------|-----------|------|-------|
| premise | v1.0.0 (draft) | — not yet | ☐ not run | retire old `premise-marketplace/` on migration |
| foundry | v1.4.0 | — not yet | ☐ not run | lift `src/` → `plugin/` |
| context-engineering-training | v0.1.0 | — not yet | ☐ not run | lift `plugin/src/` → `plugin/` |

## Notes

- Marketplace name `uxfx-tools` checked against Anthropic's reserved/blocked list (docs, 2026-05-31) — clear.
- `$schema` uses schemastore.org URL (resolves; drives editor validation). Claude Code ignores it at load.

## Changelog

- 2026-05-31 — Repo scaffolded. Empty marketplace; no plugins promoted yet.
