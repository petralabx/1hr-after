# SEO/AEO action-plan ship — 1HR-After

> Filed: 2026-10-07T16:30:00Z · Kind: ship
> Related: [`2026-10-06-seo-aeo-hygiene-org.md`](2026-10-06-seo-aeo-hygiene-org.md), [`../products.md`](../products.md)

Operator asked to implement the independently reviewed Oct 2026 SEO action plan. This slice is the **agreed** set: snippets that match live article numbers, hike structure, two 404→301s, race-pack rewrite, homepage kit CTA added (not replacing the two product buttons), collection H1 template, noindex featured/frontpage.

**Not done (review disagrees):** robots `Disallow` of `/pages/affiliate-signup` or `/apps/`; October slug 301s for Valentine's or the marathon checklist; magnesium merge into types-of-magnesium; Body Glide posts; `${t}` theme hunt; “Made in Canada”; invented “7 proven” / “9 fixes” / “treat in 24 hours”; FAQ claim rewrites.

Shop: `1hourafter.myshopify.com` only. Theme `#122661372077`. CIP lands; this agent cannot merge.

## What shipped live

### Snippets (Admin `global.title_tag` / `description_tag`, plus H1 where the article title was stale)

Numbers match the live bodies: hike does not promise recover-in-48-hours; half-marathon says **7–14 days**; Hyrox says beginners **12–16** / experienced **8–12**; wetsuit does not promise 24-hour cure; body wash says **Made clean in North America**.

Handles were not changed.

### Hike post

Product cards under the TOC came from `article-template.liquid` (tag match), not the article HTML. Moved those cards **below** the article and demoted product names from `h2` to `p`. Body now has a jump link `#how-to-treat-sore-calves-after-hiking`, a contextual recovery-balm card, a lotion sentence under Epsom, a sampler CTA, and a DOMS link in the intro.

### Redirects

| From | To | Before |
|---|---|---|
| `/blogs/news/post-hike-sore-calves-muscle-relief` | hike post | 404 |
| `/blogs/news/how-long-does-it-take-from-half-marathon` | half-marathon post | 404 |

### Race Day Kit

Handle stays `marathon-race-pack`. Display title **Race Day Kit: Anti-Chafe + Recovery Balm**. Sentence-case description. Compare-at `$32.98` (sum of the two live balm prices). Homepage Race Day section: “clothe sores” → “clothing”, plus a third button to the kit.

### Collections

`collection.liquid` now renders `collection-template` (this collection’s H1 + products). `collection3`/`collection2` were homepage featured grids, which is why every collection URL showed the same chrome. `/collections/all` title/H1/description set in the theme (`collectionByHandle("all")` is not a merchant collection). `featured-collection` and `frontpage` are `noindex` in `layout/theme.liquid`. Unique Admin descriptions on race-day and body-care.

## Live checks (2026-10-07)

| URL | Result |
|---|---|
| Hike post | Title `Sore Calves After Hiking: Causes and How to Treat Them`; jump line; no product H2s under TOC |
| Menthol post | Title `Menthol Crystals Benefits: Skin, Sore Muscles and Recovery` (no longer the balm product title) |
| Hyrox post | Title/H1 `How Long to Train for Hyrox: 8-16 Weeks by Fitness Level` (dropped Ultimate 2025) |
| Christmas athletes | Evergreen title; “Start here” sampler / balm / kit block |
| `/products/marathon-race-pack` | H1 Race Day Kit; sentence-case copy; `$29.55` / compare-at `$32.98` |
| `/collections/race-day-essentials` | H1 present; **2 products** (the two balms), not the old shared grid |
| `/collections/all` | Title/H1 `All Post-Workout Body Care`; 9 products including the kit |
| `/collections/featured-collection` | `noindex` |
| `/collections/frontpage` | `noindex` |
| Homepage | “skin friction and clothing”; kit href + “RACE DAY KIT”; ANTI CHEF still gone |
| Old hike slug | 301 → current hike URL |
| Old half-marathon slug | 301 → current half-marathon URL |
| `/pages/affiliate-signup` | Still 200 (not robots-blocked) |

## Deliberately left

- Gift-guide lists were **not** cut from 100 to 20 (editorial pick still needed). 1Hour After cards were prepended.
- Valentine’s and marathon-checklist **slugs kept** (year stays in the URL until after the season).
- Body Glide comparison posts not written.
- `robots.txt.liquid` unchanged.
- Class B [`../products.md`](../products.md) canonical tables still empty; proposed row notes the kit rename.

## Rollback (Shopify)

Delete the two new URL redirects. Revert article titles/bodies/metafields from Shopify versions. `productUpdate` race pack title/description/SEO back to “The Marathon Race Pack”; `productVariantsBulkUpdate` compare-at to null. Revert collection descriptions/SEO. `shopify theme push` `site/theme` from `main` (PR #14) onto theme `122661372077`. Git: revert this PR.
