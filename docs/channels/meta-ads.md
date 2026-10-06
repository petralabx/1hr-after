# Channel: Meta ads

> **Owner:** Class B (agent proposes, human approves operating decisions)
> **Status:** Scaffold. No ad account, pixel, catalog, or campaign is on file.
> **Last updated:** 2026-10-06
> **Links:** [claims](../compliance/claims.md) · [brand voice](../knowledge/brand-voice.md) · [creative checklist](../knowledge/best-practices/meta-ads.md) · [copy archive](../../copy/ads/meta/README.md)

1HR-After paid social runs on Meta (Facebook and Instagram). Google, TikTok, and Amazon Attribution are out of scope until a later task adds them. This file is the operating playbook. It is the addition on top of the Furgenics repo shape.

## Account

Fill from Business Manager. Do not paste tokens.

| Field | Value |
|---|---|
| Business Manager | TBD |
| Ad account id | TBD |
| Facebook page id | TBD |
| Instagram account id | TBD |
| Pixel / dataset id | TBD |
| Conversions API | TBD |
| Catalog | TBD |
| Primary domain | TBD |
| Currency | TBD |
| Daily budget owner | TBD |

Mirror the ids (never the secrets) into [`../../data/config.json`](../../data/config.json) `channels.metaAds` when they are known.

## Campaign shapes

No campaign is approved. When work starts, file each live campaign under one of these shapes and link the copy file.

| Shape | Job | Status |
|---|---|---|
| Sales / catalog | Convert on the primary domain or a named landing URL | Not started |
| Prospecting | Cold and broad, after voice and claims exist | Not started |
| Retargeting | Site and engagers, after the pixel is verified | Not started |

Name campaigns so the ad account, this page, and `copy/ads/meta/` use the same slug. That slug is the join key.

## Measurement

UTM convention for every ad URL:

`utm_source=meta&utm_medium=paid&utm_campaign=<slug>&utm_content=<creative-slug>`

Events to confirm once a pixel exists: `PageView`, `ViewContent`, `AddToCart`, `Purchase`. Do not treat an unverified pixel as a working account.

Weekly note, once spend exists: spend, impressions, link clicks, CTR, CPC, landing-page views, purchases, and purchase value, by campaign slug. File the export under `docs/sources/meta-ads/` and append a line to [`../knowledge/optimization-log.md`](../knowledge/optimization-log.md). Do not commit raw exports that include customer data.

## Creative and copy

- Specs and placement checklist: [`../knowledge/best-practices/meta-ads.md`](../knowledge/best-practices/meta-ads.md).
- Drafts and approved variants: `copy/ads/meta/`. Start from [`../../copy/ads/meta/_template.md`](../../copy/ads/meta/_template.md).
- Color in any component built from an ad uses [`../design-system/tokens.css`](../design-system/tokens.css) (`--1hr-` tokens). No raw hex in components.
- Voice and claims are blocked until the Class C pages are filled.

## Rules

- No COGS, fees, or margins in this file or in ad copy.
- No access tokens, system-user secrets, or session cookies.
- Competitor names stay out of ad copy until [`../compliance/claims.md`](../compliance/claims.md) allows a specific comparison.
- A status change from `Draft` to `Approved` on a copy file requires the claims table to name the claim the ad makes.

## Open decisions

- Shopify (or other) domain the ads will land on.
- Whether checkout is on-site, Amazon, or another retailer.
- Who can approve Class B changes to this playbook.
- Whether a catalog/Advantage+ sales campaign is in the first flight.
