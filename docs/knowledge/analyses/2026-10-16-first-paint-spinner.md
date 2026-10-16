# The grey first paint and Subscribe & Save — 1HR-After

> Filed: 2026-10-16T20:45:00Z · Kind: ship
> Related: [`2026-10-14-page-load-review.md`](2026-10-14-page-load-review.md)

The blank flash before the page appears is the theme’s grey page color while two large stylesheets block the first paint. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3140. Live push used `--only layout/theme.liquid` from `site/theme`.

## What the flash is

The inline critical CSS in [`site/theme/layout/theme.liquid`](../../../site/theme/layout/theme.liquid) sets `body, html { background-color: #C7C4C4 }`. `theme.css` and `onehour.css` were normal stylesheets in the head, so the browser painted that grey and waited for both files before it could paint the header and the hero. Other shops often use a white background that matches the page, so the same wait is easy to miss.

An earlier slice removed a rule that hid `.main-content` until CSS arrived. That stopped a white hold. It left the grey wait in place. See [`2026-10-14-atc-and-first-paint.md`](2026-10-14-atc-and-first-paint.md).

## What is live now

`html` starts with the class `booting`. An inline rule draws a grey cover and a 56px ring in the existing accent `#fa5a16`. The ring is in the head, so it can paint before the app scripts in `content_for_header` finish. `theme.css` and `onehour.css` are preloaded and then linked with `media="print"` so they do not block that paint. When each file loads, the link switches to `media="all"`. After both have switched, two frames later the `booting` class comes off and the ring leaves. A four-second timer does the same thing if a file never loads. `prefers-reduced-motion` stops the spin. With JavaScript off, a `noscript` block hides the ring and loads both files as normal stylesheets.

`onLoadStylesheet()` is unchanged, so Debut’s stylesheet promise still resolves.

## Live check

Cache off, 2026-10-16, after the layout asset was pushed.

- With `theme.css` and `onehour.css` held back: `html` class is `js booting`, the cover is `rgb(199, 196, 196)`, and the ring is 56px with border `rgb(250, 90, 22)` and animation `bootspin`.
- After both files apply: the class is `js`, the cover and ring are gone, and the “Loading” status is removed. Homepage hero, logo, and “View all products” are in place. Six product cards are in the grid.
- Cooling Menthol Body Wash at 390px: Add to Cart is present and `.pdp-mobile-atc` is `position: fixed`.

## Subscribe & Save

This slice did not remove it, and the earlier layout and claims slices did not either. The purchase-option markup is still in the theme.

- [`site/theme/sections/product-template.liquid`](../../../site/theme/sections/product-template.liquid) renders the BSS price and the “Purchase options” radios only when `content_for_header` contains `bss-sub-recurring-pay`.
- [`site/theme/snippets/bss-selling-group.liquid`](../../../site/theme/snippets/bss-selling-group.liquid) renders only when `product.selling_plan_groups.size > 0`.

On 2026-10-16 the live homepage HTML does not contain `bss-sub-recurring-pay`. Admin GraphQL `2024-10` returns an empty `sellingPlanGroups` list for the shop and for Cooling Menthol Body Wash (`gid://shopify/Product/6668255723693`). With no selling plans, Shopify has nothing for a Subscribe & Save control to select.

The footer newsletter form is still in [`site/theme/sections/footer.liquid`](../../../site/theme/sections/footer.liquid). That is email signup. [`site/theme/snippets/subscribe-it-helper.liquid`](../../../site/theme/snippets/subscribe-it-helper.liquid) is the back-in-stock notice, not a subscription plan.

Putting a discount widget in the theme without a selling plan would invent an offer the shop cannot bill. To show Subscribe & Save again, reconnect the subscription app in Shopify admin and attach selling plans to the products. The theme gate will render the existing Purchase options block when both of those are true.

## Rollback

From `site/theme`, restore the previous `layout/theme.liquid` (render-blocking `theme.css` and `onehour.css`, no `booting` class) and run:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only layout/theme.liquid
```
