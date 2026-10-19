# Product tile size and separation — 1HR-After

> Filed: 2026-10-19T18:10:00Z · Kind: ship
> Related: [`2026-10-19-marathon-pack-tile.md`](2026-10-19-marathon-pack-tile.md), [`2026-10-16-tile-atc-layout.md`](2026-10-16-tile-atc-layout.md)

The Race Day Kit card was taller than the other product tiles, so its photo ran into the Marathon Pack card on the next row. The Marathon Pack photo was squeezed under a text band, so only the pump tops showed. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3368. Live push used `--only assets/onehour.css` from `site/theme`.

## What changed

In [`site/theme/assets/onehour.css`](../../../site/theme/assets/onehour.css), both pack cards (any product card that has a contents line) are the same square as the single products. The photo fills that square with `object-fit: cover`. The title, reviews, and contents sit on the photo. Every product list uses an 8px gap, and each desktop column is `calc((100% - 16px) / 3)` so the gap does not wrap a tile.

Prices, names, and the contents lines are unchanged. This replaces the taller Race Day stack and the Marathon Pack “photo under the text band” treatment from [`2026-10-19-marathon-pack-tile.md`](2026-10-19-marathon-pack-tile.md).

## Live check

Cache off, 2026-10-19, after the stylesheet was pushed. Each card was scrolled into view so the lazy photos had loaded.

- Collection, 1440px: all eight tiles are 475×475. Columns start at 0, 483, and 965. No tile boxes overlap. Race Day Kit and The Marathon Pack use `aspect-ratio: 1` and `object-fit: cover`, and the photo is the full tile.
- Collection, 390px: all eight tiles are 390×390, stacked, with the same gap.
- Homepage, 1440px: all six featured tiles are 475×475 once their photos have loaded. Below-the-fold cards stay short until the lazy image loads; that is the existing loader, and the pack cards stay square while they wait.

## Rollback

From `site/theme`, restore the previous `assets/onehour.css` and run:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only assets/onehour.css
```
