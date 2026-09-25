# AGENTS.md — Brand repo

- Import MC task discipline: every agent PR carries the Hub-minted `MC-Checkout: dsp_…` line (see Mission Control handshake below).
- Colors come from brand tokens in `docs/design-system/tokens.css` only — no raw hex in components.
- Tokens activate inside the opt-in brand boundary declared in `plx-brand.json`.

## Mission Control handshake (Claude Code and every agent)

Before first edit or any PR_CREATE on `petralabx/1hr-after`:

1. **Search** projects, buckets and TASK-* first (`mc_search_tasks` / `mc_suggest_work`: branch, title, runId). Reuse a matching open TASK.
2. **Create only on a real miss**: `mc_create_task` in the registry default bucket (`BKT-INFRA`, from PLX_MC `config/tracked-repos-registry.json`; do not hardcode another prod bucket). Create a project/bucket only if it is truly missing. Never create a TASK to escape incomplete evidence on a live checkout.
3. **Checkout**: `mc_checkout_task { taskId, repo: "petralabx/1hr-after" }` on PLX-MC-Hub. Confirm `taskId` matches and `actor.repo` is `petralabx/1hr-after`. Copy `prBodyLine` exactly. HTTP fallback when Hub MCP tools are missing:
   `COMPLIANCE_CAPTURE=1 MC_REPO=petralabx/1hr-after MC_TASK_ID=TASK-N node scripts/compliance-checkout.mjs` (reads `MC_BASE_URL`, `MC_MCP_API_KEY`, `MC_OPERATOR_EMAIL`, `MC_ACCOUNTABLE` from the environment; never echo the key).
4. **Stamp at PR open**: put the `MC-Checkout: dsp_…` line in the body at `gh pr create` time (the compliance gate reads the body on opened/synchronize/reopened only, not on edits). Never invent a `dsp_*`, never write `MC-Checkout: pending`, never `--no-verify`, never an empty commit or push to re-trigger CI. If the body must change after open, ask CIP to close/reopen.
5. **Last commit → `mc_complete_task`** (summary + verificationCommands + rollback) **→ freeze**. CIP lands; agents never merge. Next slice = new branch from the integration branch.
6. If Hub MCP and the HTTP fallback both fail: stop; CoS/CIP paste `prBodyLine`.

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
