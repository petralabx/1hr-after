# AGENTS.md — Brand repo

- Import MC task discipline: every agent PR carries the Hub-minted `MC-Checkout: dsp_…` line (see Mission Control handshake below).
- Colors come from brand tokens in `docs/design-system/tokens.css` only — no raw hex in components.
- Tokens activate inside the opt-in brand boundary declared in `plx-brand.json`.

## Mission Control handshake (Claude Code and every agent)

<!-- plx-mc:handshake:start -->
Generated from PLX_MC [`config/governance-contract.yaml`](https://github.com/petralabx/PLX_MC/blob/main/config/governance-contract.yaml) by `scripts/generate-governance-surfaces.py --fleet`. Do not edit this block: change the contract and regenerate.

Before the first edit or any PR on `petralabx/1hr-after`:

1. Search projects, buckets and TASK-* first (mc_search_tasks: branch, title, runId). Create a task only on a real miss, with mc_create_task in BKT-INFRA. Never create a task to escape incomplete evidence on a live checkout.
2. Check out with mc_checkout_task, passing repo `petralabx/1hr-after`, your own `runtime/lane` as agent, and your branch. Confirm the returned taskId and that actor.repo is `petralabx/1hr-after`. Copy prBodyLine exactly.
3. Never invent a dsp_* id, never write `MC-Checkout: pending`, and never push with --no-verify. Without the MC tools, check out over HTTP: `COMPLIANCE_CAPTURE=1 MC_REPO=petralabx/1hr-after MC_TASK_ID=TASK-N node scripts/compliance-checkout.mjs`. If that fails too, stop and ask CoS or CIP to paste the prBodyLine.
4. End every commit with Agent, On-Behalf-Of and MC-Checkout as its last three lines. Name the TASK id in the PR title or branch.
5. Save evidence with mc_save_evidence before you open the PR, and put the MC-Checkout line in the PR body when you open it.
6. After you fix a PR body, re-run the failed compliance job. Never push an empty commit, and never close and reopen a PR, to restart a check.
7. After the last commit, call mc_complete_task with verificationCommands, rollback and the PR link. Then move the task's stage, or say why you cannot.
8. Mark a green PR ready and stop: only CIP's merge-queue session arms auto-merge or merges, with a merge commit into `main`. A PR that touches money, migrations or workflows, or reverts merged work, needs a signed MC merge approval of its exact head (mc_request_approval, merge scope).

- A plan that adds a project, or two or more buckets, goes through a draft: mc_save_draft, then mc_submit_draft. Its author accepts it in Mission Control.
<!-- plx-mc:handshake:end -->

## Workstream protocol

Sessions are disposable. What the next session or a teammate needs lives in
[`docs/workstreams/`](docs/workstreams/README.md) and travels with the code (Vince, 2026-10-26, TASK-3953).

- One workstream per branch and worktree. Flag any edit outside your workstream's scope before you make it. A one-PR change needs no workstream.
- At session start, read your workstream's note, `docs/workstreams/<slug>.md`. The index in `docs/workstreams/README.md` maps branches to slugs.
- Before you end a session, and after any significant decision, update that note in the same branch (`/handoff` in Claude Code and Cursor; `/resume-workstream` picks it up).
- Change the index row (owner, branch, status, dependencies) only when a workstream opens, closes or changes status.
- SharePoint `Agent Handoffs/` stays the system of record for durable handoffs. The note is the agents' working copy; when they disagree, SharePoint wins.

## What this repo is

Versioned brand home for **1HR-After**. The directory layout follows the Furgenics brand repo. Meta ads are an extra lane Furgenics does not have. The knowledge base follows Karpathy's LLM-wiki pattern (sources, wiki, schema) — see [`docs/wiki-schema.md`](docs/wiki-schema.md).

- `docs/knowledge/` is the brand wiki (voice, ICP, products, competitors, FAQ, keywords, filed analyses).
- `docs/sources/` is the immutable raw layer. Agents read it; they do not rewrite committed sources.
- `docs/channels/meta-ads.md` is the Meta (Facebook and Instagram) playbook. Copy lives in `copy/ads/meta/`.
- `copy/content-drafts/` is the organic page archive (markdown canonical, HTML paste-ready).
- `site/theme/` is the published Shopify theme, pulled read-only. Do not push it back unless a later task says so.
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
- **Workstreams:** work that spans more than one PR or session also keeps a note in `docs/workstreams/` (see Workstream protocol). `docs/sessions.md` stays the short per-session log.
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
  governance-only: `.github/workflows/ci.yml` parses every workflow file and reports the `ci`
  roll-up, `ai-review-verdict.yml` posts `ai-review/verdict`, and the org-required PLX_MC gate
  reports `compliance`.
