# Staged storefront fixes from homepage and PDP feedback — 1HR-After

> Filed: 2026-10-16T12:20:00Z · Kind: ship
> Related: [`2026-10-15-hide-try-sample.md`](2026-10-15-hide-try-sample.md), [`2026-10-14-phased-oct8-reship.md`](2026-10-14-phased-oct8-reship.md)

Operator feedback on the live store, checked against the catalog before any price or claim change. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3065. CIP lands; this agent does not merge.

**Skipped on purpose:** Race Day Kit price, Marathon Pack rename, a “Save $52” line, and a free-shipping bar. Reasons are below. No new disease or treatment claims. Athletic Sampler stays draft. US Retail stays draft. `settings_data.json` was not pushed. No `format: 'webp'` on `img_url: '1x1'`.

## Prices the feedback did not match

Checked on the storefront in USD, cache off, 2026-10-16:

| Product | Handle | Live price |
|---|---|---|
| Race Day Kit | `marathon-race-pack` | $29.55, compare-at $32.98 |
| Anti Chafe Glide Balm | `anti-chafe-balm` | $14.99 |
| Muscle Recovery Balm | `muscle-recovery-balm` | $17.99 |
| The Marathon Pack | `marathon-pack` | $105.00, compare-at $120.00 |
| Lotion, body wash, shampoo | bottle handles | $30.00 each |

$14.99 + $17.99 = $32.98, which is the kit’s compare-at. The kit is already below $29.99. Moving it to $29.99 would raise the price. It was left at $29.55.

The Marathon Pack description lists four products: shampoo, conditioner, body wash, and magnesium lotion. It does not list two balms plus four bottles. $105 against a $120 compare-at is not a $52 discount. The name stays **The Marathon Pack**. The card line is “Shampoo, conditioner, body wash, and magnesium lotion.” The Race Day Kit card line is “Anti-chafe balm and muscle recovery balm.” Neither card prints a dollar saving.

## What shipped

### Homepage grid

`featured-collection` already contained the lotion and the body wash. The section only rendered four products, so the grid stopped at shampoo. [`site/theme/sections/collection.liquid`](../../../site/theme/sections/collection.liquid) now renders six handles when the section collection is `featured-collection`: Race Day Kit, Anti Chafe, Recovery Balm, Refueling Magnesium Body Lotion, Cooling Menthol Body Wash, Adaptogen Protein Strengthening Shampoo. Conditioner stays in the collection and is not one of these six. CSS in [`site/theme/assets/onehour.css`](../../../site/theme/assets/onehour.css) wraps the row at 33.33% (two rows of three at 1440px) and 50% under 749px.

Live check: all six images had `naturalWidth` 480 at 1440px and 195 at 390px. Current image URLs did not contain `{width}`.

### Review badges and pack contents

[`site/theme/snippets/product-card-grid.liquid`](../../../site/theme/snippets/product-card-grid.liquid) prints the Judge.me preview badge and the two contents lines above. Theme CSS had been hiding `.jdgm-prev-badge__text`; the card rule shows it. Homepage cards: kit “No reviews” (the bundle has none), balms and lotion and wash “10 REVIEWS”, shampoo “9 REVIEWS”. On `/collections/all`, The Marathon Pack card shows the four-product line, “7 REVIEWS”, sale $105, regular $120.

### Product page

- Three short bullets under Add to Cart, from [`site/theme/snippets/pdp-benefit-bullets.liquid`](../../../site/theme/snippets/pdp-benefit-bullets.liquid). Wording stays inside what the page already says.
- The four all-caps intro paragraphs move into the existing Benefits block, which stays closed.
- Key Active Ingredients starts open. Directions, the full ingredient list, and FAQ stay closed. The first attempt wrapped each heading in a second `<details>` element; the ingredient text stayed `display: none` because of `.cont-hide`. That wrapper was removed. The page uses the existing `.set-prod` blocks.
- Quantity input always renders.
- Anti-chafe and recovery balm link to the Race Day Kit: “Both balms are in the Race Day Kit.”
- Mobile Add to Cart is a second button on `document.body` (`.pdp-mobile-atc`). `position: fixed` on the original button does not stick, because `.page-container` has a transform. After scroll on a 390px window the bar sat on the viewport bottom (`top` 770, `bottom` 844).
- The empty “What Athletes Are Saying?” block is gone. Its script called `dev.maxdigi.co` and embedded a Judge.me token. That script is not in the current template. Reviews stay in the Judge.me widget (anti-chafe shows 4.90 from 10 reviews). Rotate that token in Judge.me; it was on the live page and remains in git history. Do not copy it into docs.

### Alt text

Made-clean icons use the metafield titles (VEGAN, ORGANIC, and the rest). Related-product images now print `featured_image.alt`, or the product title when that alt is blank. Blog tiles in the same section use the article title. On the anti-chafe page the rendered `<img>` set had no empty alt. Six `iconN_small` tags with `alt=""` sit inside an HTML comment and are not in the DOM. They were left there.

### Mobile layout

Under 749px, `#shopify-section-custom_content_Bq8YWE` stacks the photo, then the three shop buttons on a `#1c1c1c` bar. Measured overlap between the photo and the button block was 0. The buttons read “SHOP ANTI CHAFE BALM”, “SHOP RECOVERY BALM”, and “SHOP THE RACE DAY KIT”. The hero is unchanged. This is not the earlier `position: static` plus `height: auto` rule; that one covered the hero and must not come back.

Under 420px the logo is capped at 52% width and 26px, and the icon row sits above it. At 400px the account icon is visible between the logo and the cart.

### Copy

- Footer “LAST LONGER” is “LASTS LONGER” in [`site/theme/sections/footer.liquid`](../../../site/theme/sections/footer.liquid). Homepage text has the new line and not the old one.
- Homepage meta, in [`site/theme/layout/theme.liquid`](../../../site/theme/layout/theme.liquid): “Post-workout body care for daily athletes. Anti-chafe balm, menthol muscle recovery balm, magnesium lotion, and cooling body wash from 1HR-A.”
- Made-clean sentence: “to make the most of that hour.”
- Spelling is **Refueling**. The lotion SEO title is “Refueling Magnesium Body Lotion for Muscle Recovery | 1HR-A”. The directions sentence in that product’s description, and seven News articles that used Refuelling or refuelling, were updated in Admin. A commented-out footer list and the Globo preorder profile name still say Refuelling. Neither is the visible product title.

## Free shipping

No “Add $X for free shipping” bar. The theme has no free-shipping threshold, and the earlier delivery-profile read was denied. The “orders over $35.00” line on the product page is Shop Pay installments, not shipping. Do not invent a $50 bar.

## Live check

Cache off, 2026-10-16, after the product-template asset `updated_at` `2026-10-16T08:07:08-04:00` and a later accordion push.

- Homepage 1440px and 390px: six products, lotion and body wash present, images loaded, review counts and the kit contents line visible.
- Race Day at 390px: photo, then the three buttons, then Body Recovery. Hero still shows the runner.
- Header at 400px: menu, logo, account, cart all visible.
- Anti-chafe at 390px: bullets, quantity, kit link, Benefits closed with the long copy inside it, Key Active Ingredients open, sticky Add to Cart after scroll, no “What Athletes Are Saying?”.

## Rollback

From `site/theme`, push the parent copies of the changed theme files:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only assets/onehour.css --only layout/theme.liquid --only sections/collection.liquid --only sections/footer.liquid --only sections/header.liquid --only sections/product-template.liquid --only snippets/product-card-grid.liquid --only snippets/pdp-benefit-bullets.liquid
```

A theme push does not undo the Admin spelling edits (lotion description, seven articles), the lotion SEO title, the renamed tag, or the media alts set on the conditioner and the Marathon Pack.
