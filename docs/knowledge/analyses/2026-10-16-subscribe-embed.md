# Subscribe and Save on the product template — 1HR-After

> Filed: 2026-10-16T21:05:00Z · Kind: ship
> Related: [`2026-10-16-first-paint-spinner.md`](2026-10-16-first-paint-spinner.md)

The shop now has a selling plan named Subscribe and Save: “Deliver every month, 10% off.” The vintage product template had no mount point for Shopify’s subscription widget. Shop `1hourafter.myshopify.com`. Theme `#122661372077`. TASK-3148. Live push used `--only sections/product-template.liquid` from `site/theme`.

## What was added

Inside the product form in [`site/theme/sections/product-template.liquid`](../../../site/theme/sections/product-template.liquid), after quantity and before Add to Cart:

- `<div class="subscriptions_app_embed_block"></div>`, the mount Shopify’s Subscription widget looks for on a vintage theme.
- A purchase-option group that lists one-time purchase and each selling plan on the product. The plan line uses the plan name and that variant’s selling-plan price. Choosing a plan sets the form’s `selling_plan` field. One-time purchase leaves that field off the add-to-cart request.
- If the Subscription widget app embed fills the mount point, the theme group is removed so the page does not show two selectors.

The cart template already prints `item.selling_plan_allocation.selling_plan.name`. The sample product template was left alone.

The theme’s App embeds list does not yet include the Subscription widget. Until that toggle is on, the theme group is what shoppers see. Theme editor → App embeds → Subscription widget turns on Shopify’s own widget, and the theme group steps aside.

## Live check

Cache off, 2026-10-16, after the section asset was pushed. Cooling Menthol Body Wash.

- The mount is inside the product form. The group is visible: “One-time purchase” and “Deliver every month, 10% off — $27.00”. One-time leaves `selling_plan` disabled. Choosing the monthly plan sets `selling_plan` to `8577613997`.
- Desktop 1440 and phone 390: the group sits between quantity and Add to Cart. The phone Add to Cart bar is still `position: fixed`.
- A throwaway cart add of the wash with that plan returned the line “Deliver every month, 10% off” at 2700 cents. That cart was cleared.

The same plan group is on the anti-chafe balm, muscle recovery balm, lotion, shampoo, Race Day Kit, and Marathon Pack product records, so those pages use the same product template block.

## Rollback

From `site/theme`, restore the previous `sections/product-template.liquid` and run:

```bash
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete --only sections/product-template.liquid
```
