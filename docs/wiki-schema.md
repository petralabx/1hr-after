# Wiki schema — 1HR-After

Schema layer for the Karpathy LLM-wiki in this repo. [`CLAUDE.md`](../CLAUDE.md) and [`AGENTS.md`](../AGENTS.md) point here. The living pages are in [`knowledge/`](knowledge/).

This is the same three-layer pattern used by the Furgenics brand repo, adapted for 1HR-After and extended with a Meta ads lane. It is not a copy of Furgenics product knowledge.

## Three layers

1. **Raw sources** — [`sources/`](sources/). Immutable. Humans and imports drop files here. Agents read them and do not rewrite them.
2. **Wiki** — [`knowledge/`](knowledge/). Markdown the agent maintains: summaries, cross-links, catalogs. Substantive answers get filed back here.
3. **Schema** — this file, plus the short pointers in `CLAUDE.md` and `AGENTS.md`. Tells a fresh session how the wiki is organized and which operation to run.

## Three operations

1. **Ingest** — a new source lands in `sources/`. Read it, file a short summary if the takeaway is durable, update every relevant wiki page, append `knowledge/log.md`.
2. **Query** — read [`knowledge/index.md`](knowledge/index.md), then only the pages the question needs, then answer. If the answer synthesizes several pages or is an explicit write-up, file it under `knowledge/analyses/` and add a catalog line plus a log entry.
3. **Lint** — look for contradictions, stale TBD fields treated as facts, orphan pages missing from `index.md`, and claims that are not allowed by [`compliance/claims.md`](compliance/claims.md). There is no linter script yet; do the check in the session and record it in `log.md` as `lint`.

## Two special files

- [`knowledge/index.md`](knowledge/index.md) — catalog. Every wiki page has a row. Hand-maintain Core pages. Analyses go between the `AUTO-APPEND:analyses` markers, newest first.
- [`knowledge/log.md`](knowledge/log.md) — append-only, newest first. Greppable prefix:

```markdown
## [YYYY-MM-DDTHH:MM:SSZ] type | title
```

Types: `ingest` · `audit` · `citation-run` · `lint` · `query` · `fix` · `ship` · `infra`.

Recent events: `grep "^## \[" docs/knowledge/log.md | head -20`.

## Ownership classes

| Class | Who writes | Pages |
|---|---|---|
| **C** | Humans only. Agents may propose in a PR description; they do not silently rewrite the page body. | `brand-voice.md`, `icp.md`, `business-identity.md`, `content-style-guide.md`, `compliance/claims.md` |
| **B** | Agent proposes; a human approves semantic changes before they are treated as canonical. | `products.md`, `competitor-intel.md`, `keyword-universe.md`, `market-map.md`, `backlinks.md`, `channels/meta-ads.md` |
| **A** | Agent may append. | `log.md`, `optimization-log.md` auto blocks, `analyses/` filings, index analyses block |

Marker-bounded machine regions use:

```html
<!-- AUTO-APPEND:<key>:START -->
<!-- AUTO-APPEND:<key>:END -->
```

Do not edit between the markers by hand except to repair a broken marker.

## What does not belong in the wiki

- COGS, fees, margins, or other internal financials.
- API keys, pixels' access tokens, or Shopify client secrets. `data/config.json` may name env vars only.
- Furgenics, For & Against, or any other brand's products, prices, voice, or competitors pasted in as if they were 1HR-After.
- Invented SKUs, domains, ad accounts, or claims. Empty tables stay empty until a human supplies the fact.

## Meta ads

Paid social for this brand is Meta (Facebook and Instagram), not a generic "paid ads" dump.

- Playbook: [`channels/meta-ads.md`](channels/meta-ads.md) (Class B).
- Approved copy: `copy/ads/meta/`.
- Platform checklist: [`knowledge/best-practices/meta-ads.md`](knowledge/best-practices/meta-ads.md).
- A creative or campaign change is a `ship` or `query` log entry, and it updates the playbook only when the operating decision changed.

## Session close

Append a short entry to [`sessions.md`](sessions.md) in the same PR. File a deep write-up in `knowledge/analyses/` when the answer should compound.

## Reading order

1. [`sessions.md`](sessions.md) — latest handoff.
2. [`knowledge/index.md`](knowledge/index.md).
3. `grep "^## \[" docs/knowledge/log.md | head -20`.
4. The pages the task names. Usually three or four, not the whole wiki.
