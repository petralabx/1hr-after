# Add to Cart alignment, the CAD switcher, and the first paint — 1HR-After

> Filed: 2026-10-14T18:45:00Z · Kind: query
> Related: [`2026-10-14-page-load-review.md`](2026-10-14-page-load-review.md)

Operator turned the Addly pair off, then sent four product screenshots from one window. The Add to Cart row is not the same on each page. They also asked what the CAD switcher is, and said Canada and the USA should use Markets. No Shopify write in this slice. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-2927.

## Why Add to Cart sits in a different place

The button is `position: absolute` on desktop (`.prod-template-new-nav .product-form__item--submit.product-form__item--no-variants` in `assets/onehour.css`). The description is pushed down with a fixed margin (`theme.css` uses 30px; `onehour.css` uses 85px, 55px, or 40px depending on width). The title row is locked to `height: 70px`.

Measured live on 2026-10-14, cache off:

| Width | Anti-chafe | Recovery balm | Body wash | Race Day Kit |
|---|---|---|---|---|
| 1440px | Stars and button share the line | Same | Same | `$32.98` overlaps Shop Pay. No stars. Description pulled up to the button |
| 1024px and under | Button just above the star row | Same | Button drops, about 66px of empty orange above the stars | Same overlap as the wide window |

Two separate causes:

1. **Race Day Kit, every width.** The kit has a sale price and a compare-at (`$29.55` / `$32.98`) and a 0.00 Judge.me rating, so the stars are hidden. The second price is taller than the 70px title row, so it paints on top of “Pay over time”. `alignAtc` in `sections/product-template.liquid` runs only when the rating is `0.00`, so this page’s description margin is different from the balms.
2. **Cooling Menthol Body Wash, 1025px and under.** That product alone gets the class `cooling-menthol-pro` (`product.id == 6668255723693`). Inside `@media (max-width: 1025px)` the button is set back to `position: static` and the description margin becomes 40px. Anti-chafe and the recovery balm do not have that rule, so the same window looks different.

Addly’s bundle block is gone from these screenshots. The embed can still be in the theme; the offer itself is off.

## The CAD switcher

The “CAD” in the header is **Mlveda**, the currency app in the theme. It is on. Default currency is CAD. Format is `money_with_currency_format`. The shop currency is USD, and Shopify presentment currencies are USD only (`enabledPresentmentCurrencies: ["USD"]`). Mlveda rewrites the displayed price in the browser after load. Checkout is still USD. That rewrite is the price jump at about 1.5 seconds.

## Markets for Canada and the USA

The countries are already markets. Do not add another one.

| Market | Status | Country | Role |
|---|---|---|---|
| uni | Active, **primary** | United States | This is the US market. The name is `uni`. |
| Canada (`ca`) | Active | Canada | Country market. Checkout currency is still USD. |
| International | Active | Rest of world | Leave local currencies off here. |
| US Retail | **Draft** | United States | A second US market. Leave it draft. |

Canada in CAD and the US in USD means: on the Canada market, turn on CAD as the local currency (that adds CAD to presentment currencies). Leave the primary market in USD. In the same step, turn Mlveda off. If Mlveda stays on, it will convert a Markets price again and US visitors will still see CAD in the header.

Admin: [Settings → Markets](https://admin.shopify.com/store/1hourafter/settings/markets). This slice did not change markets or Mlveda.

## The one first-paint edit

`layout/theme.liquid` only. The inline CSS sets `.main-content{opacity:0}` and hides every section except the first. `theme.css` and `onehour.css` load with `media="print"` and switch to `all` on load. `theme.css` is what sets `.main-content{opacity:1}`. Until that file arrives the screen is white (measured at 350 ms). The `onehour.css` preload is commented out.

The edit: load both stylesheets as normal stylesheets, and remove the opacity and section-hide rules. Do not change image tags. Do not add `format: 'webp'` on `img_url: '1x1'`. Screenshot the homepage and one product page after the push.

## What is next

1. One CSS change so Add to Cart matches on these four products: let the title row grow past 70px, and remove the body-wash-only rule under 1025px. Screenshot all four at a wide window and at about 1000px.
2. The `theme.liquid` first-paint edit, alone.
3. Markets currency: CAD on the Canada market, USD on `uni`, Mlveda off in that same step. Do not activate US Retail.
