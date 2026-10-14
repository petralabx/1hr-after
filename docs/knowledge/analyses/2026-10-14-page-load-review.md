# Page load and the Race Day Kit bundle — 1HR-After

> Filed: 2026-10-14T17:40:00Z · Kind: query
> Related: [`2026-10-14-visual-fixes.md`](2026-10-14-visual-fixes.md)

Operator asked why `1hourafter.com` takes a second and does not finish in one paint, whether the Race Day Kit should stay bundled with the Marathon Pack, and what to do next. Measured live on 2026-10-14 with cache disabled, viewport 1440×900. Shop `1hourafter.myshopify.com` only. Theme `#122661372077`. No Shopify write in this slice. TASK-2921.

## How the pages load

The store answers quickly. The stagger is in the browser.

| Page | Time to first byte | First paint | Load event | Requests | When “CAD” first appears in the page |
|---|---:|---:|---:|---:|---:|
| Homepage | 46 ms | 428 ms | 1.3 s | 293 | 1.5 s |
| Race Day Kit | 377 ms | 436 ms | 1.5 s | 357 | 1.8 s |
| Marathon Pack | 18 ms | (largest image 820 ms) | 1.3 s | 365 | 1.8 s |
| News | 21 ms | 280 ms | 0.7 s | 284 | 1.3 s |

HTML is about 170 KB on the wire and 500–650 KB decoded. Homepage transferred about 2.6 MB across those 293 requests. About 200 of the requests are scripts.

Screenshots from the same run:

- 350 ms: white. Header and product are not on screen yet.
- 900 ms: the page is painted. On the Race Day Kit the photo, price, and Add to Cart are there. The bundle is not.
- 1.8 s: the Addly block has been inserted above Add to Cart, the description has moved down, and the header shows `CAD`.

### Why it paints in stages

1. **The theme hides the page until CSS arrives.** `layout/theme.liquid` inlines `.main-content{opacity:0}` and `.main-content .shopify-section{display:none}`, then loads `theme.css` (200 KB) and `onehour.css` (101 KB) with `media="print"` and flips them on later. The `onehour.css` preload is commented out. `theme.css` is what sets `.main-content{opacity:1}`. That is the blank first third of a second. Debut does this so the unstyled HTML never flashes. On this shop it reads as a pause, then the whole orange page appears.

2. **Addly inserts the bundle after the product is already visible.** On both pack pages the widget is absent at 900 ms and present by 1.8 s. Both “ADD THIS” boxes are checked. The block pushes Add to Cart and the description down. That is the jump in the Race Day Kit screenshot.

3. **Mlveda rewrites prices after load.** Shop currency is USD. Mlveda’s default is CAD (`mlvedaACS_defaultCurrency: CAD`, format `money_with_currency_format`). The theme price stays `$29.55` / `$105.00`. The bundle amounts and the header switcher become CAD about 1.5–1.8 s after navigation. Markets stay deferred.

4. **The rest of the “simple” page is apps.** Enabled embeds: Klaviyo, Judge.me, a spin-wheel popup, EcomSend, Addly, Minmaxify. The layout also loads Globo preorder, Smile, Swym, a back-in-stock helper, Buy with Prime on the product template, Google Tag Manager, a Meta pixel, and `booster-page-speed-optimizer.js` from Shopify files shop `0194/1736/6592` (this shop is `0561/0618/8973`). Shop Pay then pulls a long list of checkout stylesheets. Homepage also calls `/cart/update.js` three times (Affiliatery).

5. **Marathon Pack testimonials wait on a dev proxy.** `sections/product-template.liquid` loads reviews through `https://dev.maxdigi.co/proxy/1hra.php/` and puts a Judge.me token in the page script. On the Marathon Pack that products call took 3.6 s and the reviews call 1.9 s. The token is already in the public theme. It is not copied here. A later slice should delete that script and use the Judge.me embed that is already on.

Lazy images are a separate, smaller effect. Below-fold photos stay as placeholders until scroll. The homepage hero was up by 900 ms.

## Race Day Kit and the Marathon Pack

They should stay two products. The Race Day Kit should be its own offer. The pre-checked Addly pair should come off.

| | Race Day Kit | Marathon Pack |
|---|---|---|
| Handle | `marathon-race-pack` | `marathon-pack` |
| What it is | 1× Anti Chafe Glide Balm and 1× Muscle Recovery Balm. Before the start, after the finish. | Shampoo, conditioner, cooling body wash, magnesium body lotion. Post-workout hair and body. |
| Price on the page | $29.55, compare-at $32.98 | $105.00, compare-at $120.00 |
| SKU | blank in Admin. Do not invent one. | `OH700-KIT` |

There is no separate “marathon starter pack” in the catalog. The four-bottle set is the Marathon Pack. The free sampler is sachets, not this pair.

Addly shows the same offer on both pages: Marathon Pack + Race Day Kit, both boxes checked, “ALL, FOR ONLY: $191.80 CAD”. That total is the CAD conversion of $105 + $29.55. On the $29.55 kit page the $105 pack is already selected, and the kit is listed as a second item inside its own page. That is why the two products keep looking like one SKU.

Leave both products published. Turn this offer off in Addly. If an add-on is still useful, put it only on the Marathon Pack, unchecked, so a runner can add the two balms. Do not pre-check the wash kit on the balm kit page.

## What is next

Do these one at a time. Each one can be rolled back alone.

1. **Addly offer.** Operator turns off the Marathon Pack + Race Day Kit pair in Addly. If that is the only Addly offer, the fallback is disabling the Addly embed in `config/settings_data.json` and pushing that one file. Re-check both pack pages: no bundle block, Add to Cart stays put, homepage images still load.
2. **Blank first paint.** `layout/theme.liquid` only. Load `theme.css` and `onehour.css` as normal stylesheets and remove the opacity / section hide. Screenshot at 1440 before and after. Do not touch image tags. Do not add `format: 'webp'` on `img_url: '1x1'`.
3. **Leave currency alone** until the Markets decision. Mlveda’s CAD default is the price rewrite at ~1.5 s.
4. **Later, still one file at a time:** remove the `dev.maxdigi.co` review script from `product-template.liquid` (and rotate that Judge.me token); then decide whether `booster-page-speed-optimizer.js` from the other shop’s files is still wanted; then a new attempt at the homepage Race Day buttons on a phone. Do not reuse `position: static` plus `height: auto` on `#shopify-section-custom_content_Bq8YWE`.

CIP still lands draft PRs [#21](https://github.com/petralabx/1hr-after/pull/21) and [#22](https://github.com/petralabx/1hr-after/pull/22). This review does not change the live theme.
