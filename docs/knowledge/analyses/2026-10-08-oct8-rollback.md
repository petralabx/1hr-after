# Oct 8 theme rollback — restore images and mobile

> Filed: 2026-10-08T17:30:00Z · Kind: ship
> Related: live Debut `#122661372077` on `1hourafter.myshopify.com`

Operator reported the TASK-2546 / PR #17 live theme ship removed homepage images and broke mobile layout. Those were not acceptable to leave live. This session restored the last known-good theme (`origin/main` / PR #15, `9d28210`) onto the published theme and reverted the Admin mutations from that slice.

CIP lands; this agent does not merge. Draft PR #17 must not land — it still contains the broken theme files.

## What broke

Two theme edits in the Oct 8 slice were enough to damage the storefront:

1. **`custom-content.liquid` `format: 'webp'`** on the lazy-load `img_url: '1x1'` + `replace: '_1x1.'` pattern. Shopify’s WebP URL no longer contains `_1x1.`, so the width swap failed and homepage section images vanished.
2. **Mobile CSS in `onehour.css`** (`try-wrap-mob-only {display:block}`, Race Day overlay `position: static`, logo `max-width: 58%`). That overrode the existing mobile layout.

## What was restored live

Theme `#122661372077` files pushed from `9d28210`:

`assets/onehour.css`, `assets/theme.css`, `sections/collection.liquid`, `sections/custom-content.liquid`, `sections/header.liquid`, `sections/header-hulkapps-backup.liquid`, `sections/product-template.liquid`, `sections/sample-product-template.liquid`, `snippets/faq-marathon-race-pack.liquid`, `snippets/product-price.liquid`, `templates/cart.liquid`, `templates/page.lab.liquid`.

Live checks after the push: homepage `format=webp` gone; a `{width}` lazy URL at `720x` returns `200 image/png`; `onehour.css` again has `.try-wrap-mob-only {display:none !important}` in the mobile block.

Admin reverted from pre-change backups: menus (Labs back; Affiliate on the old page URL), `featured-collection` order and kit removed from that collection, anti-chafe / marathon-pack / kit descriptions, marathon-pack compare-at cleared, `product_icon6_title` back to `freecruelty `, 18 article bodies restored.

## Not re-applied

Pack native Add to Cart, sampler Shop Pay gate, homepage hero-first grid, nav cleanup, and copy typos stay **out** until a later slice can ship without touching image URL filters or mobile overlay CSS.

## Rollback of this rollback

`shopify theme push` the TASK-2546 theme files from `cursor/seo-aeo-oct8-review-f8cc` onto `#122661372077`. Re-run the TASK-2546 Admin mutations. Do not do that unless the image URL filter and mobile CSS are rewritten and verified first.
