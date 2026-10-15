# Add to Cart alignment and the first paint — 1HR-After

> Filed: 2026-10-14T20:30:00Z · Kind: ship
> Related: [`2026-10-14-atc-markets-first-paint.md`](2026-10-14-atc-markets-first-paint.md)

Operator removed Mlveda, set Canada to CAD, and left the primary market `uni` on USD. Then asked for the button CSS and the `theme.liquid` first-paint edit. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-2937. Live pushes used `--only` from `site/theme`.

## What was already true before this slice

Shopify presentment currencies are `CAD` and `USD`. The Mlveda snippets render as “app was uninstalled.” A US load of the homepage no longer shows CAD in the header.

## Add to Cart

`assets/onehour.css` only.

- `.prod-template-new-nav .product-single__meta` height is `auto`, so the Race Day Kit’s `$29.55` / `$32.98` stays inside the title row. Shop Pay starts 16px below the price.
- Removed the body-wash-only rules under 1025px that set the button to `position: static` and the description margin to 40px. The column spacing on `.cooling-menthol-pro .product_flex_box` is unchanged.

Live check, cache off, 2026-10-14:

| Width | Anti-chafe, body wash, recovery balm | Race Day Kit |
|---|---|---|
| 1440px | Same row. Button overlaps the star line by 40px. | Price clears Shop Pay. Button bottom meets the description (gap 0). |
| 1000px | Body wash matches the two balms (gap 15px). | Price clears Shop Pay. Gap 0. |

Homepage hero images still load (`naturalWidth` 1241 and 1440). No `{width}` left in image URLs.

## First paint

`layout/theme.liquid` only.

Removed `.main-content{opacity:0}` and the rule that hid every section except the first. `theme.css` and `onehour.css` now load as normal stylesheets. `theme.css` still calls `onLoadStylesheet()` so Debut’s stylesheet promise can resolve. `sections/header.liquid` still has a second `onehour.css` link with `media="print"`. It does not hide the page.

Live check: homepage opacity is 1, 8 sections present, 0 broken image URLs. Phone width 390px shows the runner photo and the hero headline at 400ms. Desktop first paint is about 460ms and is the styled hero, not a white hold. Product photos on the Race Day Kit are present (`naturalWidth` 720 and 1024).

## Rollback

Push the parent copies of these two files with `shopify theme push --only` onto theme `122661372077`:

- `assets/onehour.css`
- `layout/theme.liquid`

Do not touch markets or reinstall Mlveda in that rollback.
