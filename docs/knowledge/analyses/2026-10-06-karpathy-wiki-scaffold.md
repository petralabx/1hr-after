# Karpathy wiki scaffold for 1HR-After

> Filed: 2026-10-06T17:45:00Z · Kind: infra
> Related: [../../wiki-schema.md](../../wiki-schema.md), [../index.md](../index.md), [../../channels/meta-ads.md](../../channels/meta-ads.md)

## Why this page exists

The next session should not have to reconstruct why `petralabx/1hr-after` is shaped this way. This is the filed answer.

## What the pattern is

Andrej Karpathy's LLM-wiki pattern has three layers and three operations.

Layers:

1. Raw sources the model reads and does not rewrite.
2. A wiki the model maintains: cross-linked markdown that compounds.
3. A schema file that tells a fresh session how the wiki is organized.

Operations: ingest a source, answer a query and file the answer back, and lint for drift.

Two files make that workable: a content catalog (`index.md`) and an append-only log with a greppable `## [date] type | title` prefix.

The point is accumulation. A later session reads the wiki instead of rediscovering the same synthesis from chat.

## What this repo adopted

Matched to the Furgenics brand repo, not to the multi-brand steward tree:

| Karpathy layer | Path here |
|---|---|
| Schema | [`docs/wiki-schema.md`](../../wiki-schema.md), pointed at from `CLAUDE.md` and `AGENTS.md` |
| Wiki | [`docs/knowledge/`](../) |
| Raw sources | [`docs/sources/`](../../sources/) |
| Catalog | [`index.md`](../index.md) |
| Log | [`log.md`](../log.md) |
| Filed answers | [`analyses/`](./) |

Also matched from Furgenics, because that is the brand-repo shape we were asked to follow:

- `copy/content-drafts/` for organic page drafts (markdown canonical, HTML paste-ready).
- `data/config.json` for the steward snapshot (domains and channel ids, no secrets).
- `site/` reserved for a future theme. No other brand's Liquid was copied.
- `docs/sessions.md` as the human handoff, separate from `log.md`.
- Class C pages stay human-owned: voice, ICP, business identity, content style, claims.

## What was added

Furgenics does not have a dedicated Meta ads lane in the brand repo. 1HR-After does:

- Playbook: [`docs/channels/meta-ads.md`](../../channels/meta-ads.md)
- Copy archive: `copy/ads/meta/`
- Placement checklist: [`best-practices/meta-ads.md`](../best-practices/meta-ads.md)
- `data/config.json` key `channels.metaAds.enabled = true`

Google, TikTok, and Amazon paid are not scaffolded.

## What was deliberately left empty

No Shopify domain, pixel, ad account, SKU, price, competitor, claim, or tagline is recorded, because none was supplied. Empty tables are the honest state. Filling them from Furgenics or For & Against would corrupt the wiki on day one.

`plx-aeo-steward` is the operational upstream for Furgenics. It is not wired for 1HR-After. Until that exists, this repo is the wiki of record.

## What was skipped

- Obsidian, Dataview, and a search index. The wiki is small enough to grep.
- YAML frontmatter on every page.
- A theme push, a pixel, or a campaign.
- Copying Furgenics analyses, product pages, or `site/theme` Liquid.

## How a later session should behave

Read `docs/sessions.md`, then `index.md`, then the pages the task names. If the answer is worth keeping, file it here, add the index bullet, and append `log.md`. Do not rewrite Class C pages inside that filing.
