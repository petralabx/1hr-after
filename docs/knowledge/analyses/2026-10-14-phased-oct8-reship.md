# Phased Oct 8 re-ship — 1HR-After

> Filed: 2026-10-14T15:10:00Z · Kind: ship
> Related: [`2026-10-07-seo-aeo-action-plan.md`](2026-10-07-seo-aeo-action-plan.md)

Operator asked to re-apply the agreed Oct 8 storefront fixes one phase at a time, with a homepage image check before the next phase, after the bundled Oct 8 theme push removed images. Shop: `1hourafter.myshopify.com` only. Theme `#122661372077`. TASK-2893. CIP lands; this agent does not merge.

**Skipped:** WebP `img_url` filters. Adding `format: 'webp'` drops `_1x1.` from Debut lazy URLs, so `replace: '_1x1.'` never runs and homepage images vanish. No product or ingredient claim edits. No Markets / currency change.

## What stayed live

### 1. Admin copy (no theme)

| Surface | Change |
|---|---|
| Anti-chafe description | `FOR EVEN MORE BETTER RESULTS` → `FOR BEST RESULTS` |
| Anti-chafe `custom.product_icon6_title` | `freecruelty ` → `Cruelty Free` |
| Marathon Pack description | `FOR MULATED` → `FORMULATED`; `PREPAR FOR` → `PREPARE FOR` |
| Marathon Pack compare-at | `$120.00` |
| Race Day Kit description | Four direction accordions copied from the existing balm lists |

Recovery balm still says `FOR EVEN MORE BETTER RESULTS`. That string was copied into the kit directions as-is.

### 2. Article bodies (12 posts)

Old redirect targets inside article HTML were replaced at the source:

| Old path | New path |
|---|---|
| `muscle-recovery-body-lotion` | `muscle-recovery-magnesium-body-lotion` |
| `the-complete-active-recovery-system` | `marathon-pack` |
| `recovery-body-gel` | `muscle-recovery-balm` |
| `christmas-gifts-for-athletes-and-runners` | `christmas-gifts-for-athletes-and-track-runners` |

Handles updated: `what-is-exercise-recovery`, `why-magnesium-is-important-for-exercise-recovery`, `the-importance-of-post-workout-skincare-routine`, `the-science-behind-skin-care-products-for-athletes`, `the-magical-power-of-magnesium-for-muscle-recovery`, `magnesium-the-ultimate-secret-weapon-for-athletes-rest-recovery-and-pain-relief`, `sweat-skincare-navigating-the-challenges-of-post-workout-skin-care-routine-for-athletes`, `upgrade-your-body-care-shower-routine-with-these-tips-tricks`, `christmas-gifts-for-athletes-and-track-runners`, `christmas-gifts-for-triathletes-runners-swimmers-cyclists`, `recovery-products-for-athletes-and-overtraining-myths`, `post-hike-recovery-sore-calves-muscle-relief`.

### 3. Menus

Labs removed from `main-menu`, `mobile-menu`, and `footern`. Affiliate on those menus points at `/pages/affiliate-signup` (page `93708288173`). The `footer` menu was not changed.

### 4. Featured collection

`featured-collection` (`284554952877`) order on the homepage grid: Race Day Kit, Anti Chafe, Muscle Recovery Balm, then shampoo. The kit was added; it was not in the collection before this slice.

### 5. Add to Cart (theme)

`sections/product-template.liquid` only. Removed the product-id gate that hid `name="add"` on Race Day Kit `8140422578349` and Marathon Pack `7162482262189`. No image tags. No Addly CSS.

### 6. Sampler price and Shop Pay (theme)

`snippets/product-price.liquid` prints `Free — $1.99 shipping` when `price == 0`. Paid products still use `money_price`. `product-template.liquid` and `sample-product-template.liquid` render `payment_terms` only when `product.price > 0`. jQuery was not changed.

## Phase 7 — tried, then rolled back

Mobile rules inside `@media (max-width: 749px)` in `assets/onehour.css`: show `.try-wrap-mob-only`, set `#shopify-section-custom_content_Bq8YWE` to `height: auto`, and set `.custom__item--html_Hma93k` to `position: static`.

At 390px the shop buttons landed on the hero headline (“1HOUR AFTER IS POST-WORKOUT…”) and the two balm photos left the Race Day section. Homepage image bytes were still HTTP 200. The file was restored from the pre-phase-7 commit and pushed with `--only assets/onehour.css`.

After that push, a 390px screenshot matches the pre-change page: runner photo, readable hero, both balm sticks visible. The pre-existing overlap remains: “SHOP ANTI CHAFE BALM” and “SHOP RECOVERY BALM” still sit on the product labels. Do not retry `position: static` / `height: auto` on that block.

Live CSS after the rollback again has `.try-wrap-mob-only {display:none !important;}` and `.custom__item.custom__item--html_Hma93k` absolutely positioned.

## Live checks (2026-10-14)

| Check | Result |
|---|---|
| Homepage hero image `_720x.png` | HTTP 200 `image/png` |
| Homepage HTML | no `format=webp`; `/pages/lab-1hr` count 0; `/pages/affiliate-signup` count 3 |
| Featured grid order | `marathon-race-pack`, `anti-chafe-balm`, `muscle-recovery-balm`, then shampoo |
| Anti-chafe | `FOR BEST RESULTS`; `Cruelty Free`; `name="add"` 1 |
| Marathon Pack | `FORMULATED` present; `FOR MULATED` absent; `PREPARE FOR`; `$120`; `name="add"` 1 |
| Race Day Kit | directions include `FOR BEST RESULTS`; `name="add"` 1; Shop Pay terms present |
| Sampler | `Free — $1.99 shipping`; Shop Pay terms absent; `name="add"` 1 |
| `what-is-exercise-recovery` | old lotion URL 0; new lotion URL 5; gel product URL 0 |
| 390px after CSS rollback | hero photo and both balm sticks visible; no horizontal overflow |

Storefront HTML can stay stale for a few minutes after Admin writes. Re-fetch with a query string.

## Rollback (one phase at a time)

- **Phase 7:** already rolled back. `onehour.css` matches `main`.
- **Phase 6:** restore `product-price.liquid` and the `payment_terms` lines in `product-template.liquid` and `sample-product-template.liquid` from `main`, then `shopify theme push --only` those files onto `#122661372077`.
- **Phase 5:** restore the product-id `if` around the Add to Cart button from `main` and push `--only sections/product-template.liquid`. Do not push image sections.
- **Phase 4:** remove kit `gid://shopify/Product/8140422578349` from `featured-collection`, then reorder to shampoo, conditioner, wash, lotion, recovery balm, anti-chafe, recovery-body-gel, adaptogen shampoo.
- **Phase 3:** add Labs page `81435885741` back to main, mobile, and footern. Point Affiliate items `459967496365`, `475707932845`, and `554266493101` at page `97379975341`.
- **Phase 2:** restore the 12 article bodies from the pre-change HTML.
- **Phase 1:** restore the three product descriptions, set `product_icon6_title` back to `freecruelty `, and clear Marathon Pack compare-at.

Git revert of this PR does not undo Admin phases 1–4.
