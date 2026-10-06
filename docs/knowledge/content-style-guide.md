# Content style guide

> **Owner:** Class C (human-only)
> **Status:** Structural rules only. Tone lives in [`brand-voice.md`](brand-voice.md). Claims live in [`../compliance/claims.md`](../compliance/claims.md).
> **Last updated:** 2026-10-06

## Organic pages

Drafts live in `copy/content-drafts/`. Markdown is canonical. HTML is the paste-ready twin. Start from `_template.md`.

- The first paragraph answers the query. No preamble.
- Prices, SKUs, and competitor names come from [`products.md`](products.md) and [`competitor-intel.md`](competitor-intel.md). If the row is missing, leave a `TBD` marker. Do not invent the number.
- Do not hardcode a price that is not in `products.md`.
- Internal links use the live path once a site exists. Until then, link the draft slug.

## Meta ads

Drafts live in `copy/ads/meta/`. One file per variant. Start from `copy/ads/meta/_template.md`.

- One idea per primary text. Headline stands alone when the primary text is truncated.
- No competitor name, no proof claim, and no price unless [`../compliance/claims.md`](../compliance/claims.md) and `products.md` both allow that exact line.
- Landing URL uses the UTM pattern in [`../channels/meta-ads.md`](../channels/meta-ads.md).
- Status stays `Draft` until a human marks it `Approved`.

## Both surfaces

- No COGS, fees, or margins.
- No raw hex when the sentence is implemented as a component. Use `--1hr-` tokens from `docs/design-system/tokens.css`.
- Log a publish in [`log.md`](log.md) as `ship` and, for tests, in [`optimization-log.md`](optimization-log.md).
