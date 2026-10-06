# Meta ads — creative checklist

> **Owner:** Class B
> **Status:** Platform hygiene, not a media plan. Re-check sizes in Ads Manager before the first flight. Meta changes placement specs.
> **Last updated:** 2026-10-06
> **Playbook:** [`../../channels/meta-ads.md`](../../channels/meta-ads.md)

## Confirm before export

| Placement | Aspect | Starting size | Notes |
|---|---|---|---|
| Feed | 4:5 | 1080 × 1350 | Preferred feed crop |
| Feed | 1:1 | 1080 × 1080 | Safe square fallback |
| Stories and Reels | 9:16 | 1080 × 1920 | Keep text out of the top and bottom UI bands |

## Copy length

- Primary text: lead with the point in the first line. Assume truncation.
- Headline: short enough to read at a glance. Write the full line in the copy file even if a placement cuts it.
- Description: optional. Do not hide the only claim here.

## File hygiene

- One aspect ratio per exported file. Do not rely on Meta to crop a 16:9 master into 9:16.
- Name files `<campaign-slug>_<creative-slug>_<aspect>.<ext>` and match the slug in `copy/ads/meta/`.
- No raw customer footage that lacks a release, and no other brand's packaging.
- Color callouts in a built component use `--1hr-` tokens. The exported image itself is a binary asset, not a token file.

## Do not treat as approved

- A size in this table is a starting size, not permission to run the ad.
- Claims, offers, and prices still go through [`../../compliance/claims.md`](../../compliance/claims.md) and [`../products.md`](../products.md).
