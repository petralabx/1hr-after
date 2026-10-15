# Visual fixes after the phased re-ship — 1HR-After

> Filed: 2026-10-14T16:55:00Z · Kind: ship
> Related: [`2026-10-14-phased-oct8-reship.md`](2026-10-14-phased-oct8-reship.md)

Operator screenshots of `1hourafter.com` after TASK-2893. Shop `1hourafter.myshopify.com` only. Theme `#122661372077`. TASK-2899. CIP lands.

## What was wrong

| What you saw | Cause |
|---|---|
| Body Recovery photo sitting on top of another image at the sides | On windows wider than 1600px the photo stayed 1600px and the hero showed through the gaps |
| Race Day Kit Add to Cart crossing the white line | That product has no review stars. The button is absolutely positioned, so the divider ran through it. Anti-chafe and the Marathon Pack still have stars, so their buttons already sat on the line |
| Blog tiles and a gray block on the new posts | `best-anti-chafe-balm-for-runners` and `body-glide-vs-1hr-a-anti-chafe-balm` had no featured image. The article template still reserved a 600px image box |
| White block on the affiliate page | The “SIGN UP NOW” button. `.lab-series-ttl a` paints links white, so the label disappeared on the white button |
| Marathon Pack looking like the same SKUs as the Race Day Kit | They are not the same product. Marathon Pack variant `41510517801133` is SKU `OH700-KIT` at $105. Race Day Kit variant `44351525978285` has no SKU and is $29.55. The Addly “pairs well with” widget offers both products on both pages |
| Two dollar signs | The theme price is one `$` (`$105.00`, `$29.55`). Addly also prints a `$` and then Mlveda writes `$171.06 CAD` into the amount, so the bundle read `$$171.06 CAD`. The crossed-out number above a sale price is the compare-at ($120 on the Marathon Pack, $32.98 on the Race Day Kit) |

## What shipped

- `onehour.css`: Body Recovery image fills the section (`object-fit: cover`). Affiliate label is orange on white at desktop widths. Addly’s extra `$` span is hidden.
- `product-template.liquid`: if Judge.me rating is `0.00`, nudge the description so Add to Cart sits on the divider.
- `article-template.liquid`: no empty 600px hero when the article has no image.
- Featured image on the two October 7 posts, using the existing anti-chafe stick photo already on the shop.

No claim edits. No Markets change. No WebP on the `1x1` lazy pattern. Race Day Kit SKU was not invented.

## Live checks (2026-10-14)

| Check | Result |
|---|---|
| Body Recovery at 2200px | Photo 2200px wide, natural width 1718, no second image at the sides |
| Race Day Kit | Add to Cart bottom lines up with the description (gap 0). Bundle text has one `$` |
| Anti-chafe | Button still sits on the divider. Price `$14.99` |
| Affiliate signup | “SIGN UP NOW” is orange on white |
| News index | Both new posts show the stick photo |
| Article hero | Image present, no empty gray slab |
| Homepage `_720x.png` | HTTP 200 `image/png` |

## Rollback

`shopify theme push --only` these three files from the parent commit onto theme `122661372077`: `assets/onehour.css`, `sections/product-template.liquid`, `sections/article-template.liquid`. Clear the two article images in Admin if the stick photo should come off the posts. Do not revert compare-at prices in this rollback; they were set in an earlier task.
