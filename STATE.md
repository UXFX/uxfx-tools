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
| premise | v1.0.0 | **v1.0.0** | ✅ PASS (2026-05-31) | promoted; cleanest run — 0 leaks, 0 junk; shipped at 1.0.0 per owner |
| foundry | v1.4.0 | → moved to `uxfx-pro` | ✅ PASS (2026-05-31) | split out to private marketplace 2026-05-31 (release decision pending) |
| context-engineering-training | v0.1.0 | **v0.1.0** | ✅ PASS (2026-05-31) | promoted; added missing frontmatter to instructor agent |

## Notes

- Marketplace name `uxfx-tools` checked against Anthropic's reserved/blocked list (docs, 2026-05-31) — clear.
- `$schema` uses schemastore.org URL (resolves; drives editor validation). Claude Code ignores it at load.

## Changelog

- 2026-05-31 — Repo scaffolded. Empty marketplace; no plugins promoted yet.
- 2026-05-31 — foundry v1.4.0 promoted (first plugin). Gate first-pass blocked on internal codename "REDACTED" in twin-retype skill; scrubbed; re-passed.
- 2026-05-31 — context-engineering-training v0.1.0 promoted (2nd plugin). Gate: added missing YAML frontmatter to instructor agent; denylist clean.
- 2026-05-31 — premise v1.0.0 promoted (3rd plugin). Gate clean (0 denylist hits, 0 junk). Shipped at 1.0.0 per owner; workshop STATE.md draft note treated as stale.
- 2026-05-31 — Split: foundry moved to private marketplace `uxfx-pro`. `uxfx-tools` is now PUBLIC, holding premise + context-engineering-training only.
