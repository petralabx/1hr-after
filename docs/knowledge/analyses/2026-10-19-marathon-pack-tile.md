# Marathon Pack tile size — 1HR-After

> Filed: 2026-10-19T17:40:00Z · Kind: ship
> Related: [`2026-10-16-tile-atc-layout.md`](2026-10-16-tile-atc-layout.md)

The Marathon Pack card was taller than the other product tiles. The title, reviews, and contents sat in a band above a full-size photo, so the card grew past the square used by the single products. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3358. Live push used `--only assets/onehour.css` from `site/theme`.

## What changed

In [`site/theme/assets/onehour.css`](../../../site/theme/assets/onehour.css), a card with `.card-img--fit` (the Marathon Pack) is locked to a square, the same proportion as the other product tiles. The bottle-group photo scales with `object-fit: contain` into the space under the title. The Race Day Kit still uses the taller text-above layout.

Prices, names, and the contents line are unchanged.

## Live check

Cache off, 2026-10-19, collection page, after the stylesheet was pushed.

- Desktop 1440: Strengthening Protein Conditioner and The Marathon Pack are both 480×480. The pack photo is 304px tall under the contents, with a 10px gap. `object-fit` is `contain`.
- Phone 390: both cards are 390×390. The pack photo starts below the contents.

## Rollback

From `site/theme`, restore the previous `assets/onehour.css` and run:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only assets/onehour.css
```
