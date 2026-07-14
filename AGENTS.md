# AGENTS.md — Brand repo

- Import MC task discipline: every agent PR stamps `MC-Checkout: <task-id>`.
- Colors come from brand tokens in `docs/design-system/tokens.css` only — no raw hex in components.
- Tokens activate inside the opt-in brand boundary declared in `plx-brand.json`.

## Cursor Cloud specific instructions

### Operator preferences (durable)

- **Always hyperlink `.md` files in answers.** Whenever a response references a
  Markdown file, present it as an openable link so the operator can open it from
  the agent window: a `<TextReference>` for uploaded artifacts under
  `/opt/cursor/artifacts/`, or a Markdown link to the tracked file / PR on GitHub
  for in-repo docs. Never mention a `.md` file by bare name without a link.

### Repo notes

This is a `marketing-brand` scaffold repo (`plx-brand.json` → `repoKind: marketing-brand`):
design-system docs plus one governance validator. There is **no** web app, build step,
package manager, or dependency file — nothing to `npm install` / `pip install`. The only
runnable "application" is the stdlib-only Python validator.

- **Toolchain:** system `python3` (3.12) only. The validator uses `dict | None` unions, so it
  needs Python ≥ 3.10; no third-party packages.
- **Run / validate the repo** (this is the core functionality):
  `python3 scripts/check-brand-repo-structure.py` (add `--repo-root <path>` to check another repo).
  Exit `0` = clean or no `plx-brand.json` (skip); exit `1` = structure violations printed to stdout.
- **Pre-existing caveat:** on the committed `main`, this validator exits `1` with
  `designSystem.tokenPrefix must look like --brand- (got '--1hr-')` — its regex `^--[a-z]...`
  rejects the digit-leading `--1hr-` prefix declared in `plx-brand.json`/`tokens.css`. This is a
  scaffold inconsistency, not an environment problem; leave it unless a task is explicitly to fix it.
- **Lint/test/build:** none configured yet (see `CONTRIBUTING.md` §5 — "add when project has a
  test suite"). CI is governance-only: `.github/workflows/plx-mc-compliance.yml` (skips unless the
  `PLX_MC_BASE_URL` secret is set) and `compliance-gate-drift.yml` (needs network to fetch the
  pinned PLX_MC generator).
