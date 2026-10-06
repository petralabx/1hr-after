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

## What this repo is

Versioned brand home for **1HR-After**. The directory layout follows the Furgenics brand repo. Meta ads are an extra lane Furgenics does not have. The knowledge base follows Karpathy's LLM-wiki pattern (sources, wiki, schema) — see [`docs/wiki-schema.md`](docs/wiki-schema.md).

- `docs/knowledge/` is the brand wiki (voice, ICP, products, competitors, FAQ, keywords, filed analyses).
- `docs/sources/` is the immutable raw layer. Agents read it; they do not rewrite committed sources.
- `docs/channels/meta-ads.md` is the Meta (Facebook and Instagram) playbook. Copy lives in `copy/ads/meta/`.
- `copy/content-drafts/` is the organic page archive (markdown canonical, HTML paste-ready).
- `site/` is reserved for the storefront theme. It is empty on purpose.
- `data/config.json` is the steward snapshot (Shopify and Meta ids). Env var names only — never secret values.

`docs/design-system/` is **out of scope for brand-ops work** — leave it alone unless a dedicated design-system task says otherwise.

There is no `plx-aeo-steward` brand folder for 1HR-After. Until one exists, this repo is the wiki of record. Do not treat the Furgenics steward tree as upstream content.

## Source-of-truth rules

- `docs/knowledge/products.md` is the canonical roster. It is empty until a human adds SKUs. Do not invent rows from another brand.
- `docs/knowledge/business-identity.md` is canonical for name, address, domain, and email.
- **Class C pages are human-only:** `brand-voice.md`, `icp.md`, `business-identity.md`, `content-style-guide.md`, `docs/compliance/claims.md`.
- Class B pages (products, competitors, keywords, market map, backlinks, Meta playbook) need human approval for semantic changes.
- Meta ad copy stays `Draft` until `docs/compliance/claims.md` names the claim the ad makes.

## Hard guardrails

1. **Never put COGS, fees, margins, or other internal financials in this repo.**
2. **No drug, disease, or treatment claims.** No proof claims ("clinically proven" and the like) until `docs/compliance/claims.md` allows that wording and cites evidence in `docs/sources/`.
3. **Do not paste Furgenics or For & Against products, prices, voice, competitors, or theme files into this repo.**
4. **API keys and secrets never enter this repo.** `data/config.json` may name env vars. Values stay in the secret store.
5. Do not invent a Shopify domain, pixel id, or ad account id.
6. Colors in components come from `docs/design-system/tokens.css` (`--1hr-` tokens). No raw hex in components.
7. Every agent PR carries the Hub-minted `MC-Checkout: dsp_…` line (see the handshake above).

## Workflow discipline

- **Start of session:** read the latest entry in `docs/sessions.md`, then `docs/knowledge/index.md` if the task touches the brand.
- New approved organic copy lands in `copy/content-drafts/`. Meta variants land in `copy/ads/meta/`.
- Substantive answers get filed in `docs/knowledge/analyses/` with an index bullet and a `docs/knowledge/log.md` line. See `docs/wiki-schema.md`.
- **End of session:** append a short entry to `docs/sessions.md` in the same PR.

## Repo map

| Path | What lives there |
|---|---|
| `docs/sessions.md` | Append-only session handoff |
| `docs/wiki-schema.md` | Karpathy wiki schema (layers, operations, ownership) |
| `docs/knowledge/` | Brand wiki. Start at `index.md` |
| `docs/knowledge/analyses/` | Filed answers |
| `docs/sources/` | Immutable raw sources |
| `docs/channels/meta-ads.md` | Meta ads playbook |
| `docs/compliance/claims.md` | Allowed claims (Class C, currently empty) |
| `docs/design-system/` | Tokens. Do not modify for brand-ops tasks |
| `copy/content-drafts/` | Organic page drafts |
| `copy/ads/meta/` | Meta ad copy archive |
| `site/` | Future theme. Placeholder only |
| `data/config.json` | Shopify and Meta account snapshot |

## Cursor Cloud specific instructions

### Operator preferences (durable)

- **Always hyperlink `.md` files in answers.** Whenever a response references a
  Markdown file, present it as an openable link so the operator can open it from
  the agent window: a `<TextReference>` for uploaded artifacts under
  `/opt/cursor/artifacts/`, or a Markdown link to the tracked file / PR on GitHub
  for in-repo docs. Never mention a `.md` file by bare name without a link.

### Repo notes

This is a `marketing-brand` repo (`plx-brand.json` → `repoKind: marketing-brand`):
a Karpathy brand wiki, Meta ads lane, design-system docs, and one governance validator.
There is **no** web app, build step, package manager, or dependency file — nothing to
`npm install` / `pip install`. The only runnable check is the stdlib-only Python validator.

- **Toolchain:** system `python3` (3.12) only. The validator uses `dict | None` unions, so it
  needs Python ≥ 3.10; no third-party packages.
- **Run / validate the repo:**
  `python3 scripts/check-brand-repo-structure.py` (add `--repo-root <path>` to check another repo).
  Exit `0` = clean or no `plx-brand.json` (skip); exit `1` = structure violations printed to stdout.
  For `brand.slug` `1hr-after` it also requires the wiki, Meta ads playbook, and copy archive.
- **Token prefix:** `--1hr-` is valid. The prefix regex allows a leading digit.
- **Lint/test/build:** the structure script is the check (see `CONTRIBUTING.md` §5). CI is
  governance-only: `.github/workflows/plx-mc-compliance.yml` (skips unless the
  `PLX_MC_BASE_URL` secret is set) and `compliance-gate-drift.yml` (needs network to fetch the
  pinned PLX_MC generator).
