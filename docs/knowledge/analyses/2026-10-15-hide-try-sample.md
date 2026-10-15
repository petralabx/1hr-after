# Hide the Try Free Sample button — 1HR-After

> Filed: 2026-10-15T21:05:00Z · Kind: ship
> Related: [`2026-10-14-tagline-buttons-blog.md`](2026-10-14-tagline-buttons-blog.md)

The Athletic Sampler is a draft because sample packs are short. The homepage “try free sample” button, the homepage mobile sample bar, and the scrolling “TRY OUR FREE SAMPLE PACK” line are parked in the live header. The markup is still in the repo. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3041.

## What was showing

`sections/header.liquid` had three sample promotions:

- A scrolling bar, on every template wider than 749px: “TRY OUR FREE SAMPLE PACK! JUST PAY SHIPPING!”
- A header button on every template: `try free sample`, linking to `/products/free-1hour-after-athletic-sampler-pack`
- A homepage-only mobile bar: “try a free sample now!”, linking to `/products/free-1hour-after-sample-pack`. CSS already hid that bar at 749px and below with `display: none !important`, and hid the header button at the same width.

The product was not unpublished from this slice. The operator set the Athletic Sampler to draft.

## Where the code lives

All three blocks are `{% comment %}` wrappers in [`site/theme/sections/header.liquid`](../../../site/theme/sections/header.liquid), each starting with `RESTORE:`. The jQuery line `$(".try-samples-wrap").toggle()` is still in the header script. It does nothing while the button markup is commented.

To put them back: publish the sampler, delete the three comment wrappers (leave the markup they contain), then from `site/theme` run:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only sections/header.liquid
```

`sections/header-hulkapps-backup.liquid` still has the old button. That file is not the live header.

## Live check

Cache off, 2026-10-15, after the header asset `updated_at` `2026-10-15T17:00:00-04:00`.

- Homepage at 1440px and 390px: no “try free sample”, no sample-pack bar, no `.try-samples-wrap` or `.try-wrap-mob-only`. Logo, cart, and the runner photo are still there. Hero `naturalWidth` 1241 at 1440px.
- Anti-chafe page at 1440px: the header button is gone there too. The button was not homepage-only.

The sampler FAQ snippet and the $0 “Free — $1.99 shipping” price label are unchanged. They are not linked from the header.

## Rollback

From `site/theme`, push the parent copy of `sections/header.liquid` with `shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only sections/header.liquid`. That puts the button, the mobile bar, and the scrolling line back on the live theme.
