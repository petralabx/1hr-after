# Homepage taglines, Race Day buttons, and blog tiles — 1HR-After

> Filed: 2026-10-14T21:00:00Z · Kind: ship
> Related: [`2026-10-14-atc-and-first-paint.md`](2026-10-14-atc-and-first-paint.md)

Operator screenshots on desktop: the two Race Day shop buttons sat on different baselines when the paragraphs wrapped, both homepage taglines were a serif, and the Body Recovery line used an em dash. The two October 7 News tiles were the same white stick. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-2939.

## Buttons

`.prod-info` is a row of two columns. Each column is now a flex column, and `.link-btn` uses `margin-top: auto`, so the two shop buttons share a bottom edge when the paragraphs wrap to different heights.

Under 1280px the banner was shorter than the copy, so the buttons slipped under the next section. The type in that range is smaller (headline 28px, tagline 16px, supporting lines 14px) and the buttons size to their labels, so they stay on the rock and clear of the sticks. From 1281px to 1400px only the paragraph’s bottom margin is reduced, which keeps the Race Day Kit button inside the photo. Wider than 1400px the original type size stays. The overlay is still `position: absolute`. This slice does not use `position: static` or `height: auto` on `#shopify-section-custom_content_Bq8YWE`.

Live check, cache off, 2026-10-14. Both shop buttons share a top edge. The kit button’s bottom sits inside the section. Homepage heroes still load. No `{width}` in image URLs.

| Width | Section height | Shop buttons aligned | Kit button inside |
|---|---|---|---|
| 1000px | 442px | yes | yes (16px to spare) |
| 1100px | 483px | yes | yes |
| 1200px | 525px | yes | yes |
| 1366px | 594px | yes | yes (13px to spare) |
| 1440px | 625px | yes | yes |

At 390px the two shop buttons still sit across the stick labels. That phone overlap was already there. The new rules start at 750px, so this slice does not move them.

## Taglines

`assets/style.css` sets `.designed-for-txt-wrap h2.designed-for-daily` to EB Garamond with `!important`, and that file loads after `onehour.css`. A `body` selector in `onehour.css` now sets MonoSpec, which matches the headlines. The supporting sentences under Race Day stay EB Garamond so they remain readable body copy.

The Body Recovery line in the live theme settings is now `Support your body's natural recovery. Morning, noon, and night.` The curly apostrophe and em dash are gone, so MonoSpec does not fall back on those glyphs. The live `config/settings_data.json` was patched as a string and pushed with `--only`. The repo copy of that file only changes the same sentence. The rest of the repo settings file was not uploaded.

## Shop Pay

Shop Pay was not removed from paid products. `sections/product-template.liquid` still prints `{{ form | payment_terms }}` when `product.price > 0`. The anti-chafe page shows “PAY OVER TIME FOR ORDERS OVER $35.00 WITH shop” under the $14.99 price. It stays. The $0 sampler is the page where installments are suppressed.

## Blog tiles

Both October 7 posts used `antichef.png`. They now use two different files already in the shop:

- `best-anti-chafe-balm-for-runners` — `salve_vs_balm_-_1hour_after_anti_chafe_balm_versus_salve_cream.png` (stick next to an open salve tin)
- `body-glide-vs-1hr-a-anti-chafe-balm` — `1hour_after_anti_chafe_balm_product_showcase_image_2.png` (stick beside a runner in a park)

## Rollback

From `site/theme`, push the parent copies of `assets/onehour.css` and `config/settings_data.json` with `shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only`. Restoring settings that way puts the em dash sentence back and does not restore the previous blog images. Those two article images are Admin content, not theme files.
