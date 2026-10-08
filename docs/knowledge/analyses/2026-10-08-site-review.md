# Oct 8 site review — aligned ship (no Markets)

> Filed: 2026-10-08T16:00:00Z · Kind: ship
> Related: [`2026-10-07-seo-aeo-action-plan.md`](2026-10-07-seo-aeo-action-plan.md), [`../products.md`](../products.md)

Operator uploaded a 1hourafter.com site review (Oct 8, 2026) and asked to implement **only what this session independently verified and agreed with**. Shop: `1hourafter.myshopify.com` only. Theme `#122661372077`. CIP lands; this agent cannot merge.

Hard rule from the review (kept): **no edits to product or ingredient claims.** Sampler stays as-is (no balm trial sizes). Marathon Pack ≠ Race Day Kit; both kept.

## Independent verification (2026-10-08)

| Review claim | Live check | Call |
|---|---|---|
| Store currency USD; Mlveda picker does not convert prices | Admin `shop.currencyCode` USD; `Shopify.currency.active` USD | Agree; **defer Markets** |
| Native ATC missing on Race Day Kit and Marathon Pack | Theme `product-template.liquid` hid the submit button for ids `8140422578349` and `7162482262189`; Addly embed still in `settings_data.json` | Agree; restore native ATC in theme. No Addly admin in this app. Hide Addly on those two handles via CSS |
| Sampler $0 shows Shop Pay terms and a blank price | Sampler variant price `0.00`; `payment_terms` was un-gated | Agree |
| Labs empty + leaked `-->` | `/pages/lab-1hr` in main/mobile/footern; `page.lab.liquid` HTML comment still ran Liquid | Agree: remove from live menus; convert leak to `{% comment %}` |
| Featured grid is hair/body first | `featured-collection` order was shampoo → conditioner → wash → lotion, balms last; kit was **not in** the collection | Agree: add kit, reorder kit / anti-chafe / recovery first |
| “View all” → featured-collection | `collection.liquid` used `collection.url` | Agree → `/collections/all` |
| Affiliate nav hits a redirect | Main/mobile/footern pointed at `/pages/athletic-affiliate-program-in-usa-and-canada` | Agree → `/pages/affiliate-signup` |
| `FREECRUELTY` | Anti-chafe `custom.product_icon6_title` was `freecruelty ` | Agree → `Cruelty Free` |
| “more better” | Anti-chafe Directions: `FOR EVEN MORE BETTER RESULTS` | Agree → `FOR BEST RESULTS`. Recovery balm has the same string; **not named** in the fix list, left |
| FOR MULATED / PREPAR | Marathon Pack description | Agree |
| FAQ still says Marathon Race Pack | Theme FAQ JSON-LD question name | Agree: question title only; answers untouched |
| Four blog links still hit redirects | 18 article bodies contained the old URLs | Agree: `articleUpdate` replacements |
| Sampler CTA on hike / half-marathon recovery claimed balm trial sizes | False: sampler is wash/lotion/shampoo/conditioner sachets | Agree: route those CTAs to the Race Day Kit |
| jquery-1.10.2 on PDPs | `product-template.liquid` loaded it | Agree: drop; keep jquery-ui 1.13.2 |
| Markets / CAD base / USD .99 list | Needs Shopify Support + Stephen sign-off | **Defer** |
| Invent contact email / “1 business day” | [`../business-identity.md`](../business-identity.md) is Class C empty | **Defer** |
| Uninstall Mlveda / Addly / Ordersify | No app-admin in this credential; Markets not on | **Defer** |
| Rename Glide Balm vs Balm | Title/H1 already match `Anti Chafe Glide Balm` | **Defer** |
| Webkul `12pxpx` | App CSS, not theme source | **Defer** |
| Fill Labs page | Empty on purpose until copy exists | **Defer** (removed from nav instead) |
| Two GSC properties | Same domain; not needed | Agree, no action |

## What shipped live

### Theme `#122661372077`

- Native `button[name="add"]` renders on both pack PDPs (product-id hide removed). Pack handles force-show `.product-form__cart-submit` and hide `[class*="addly"]`.
- `payment_terms` only when `product.price > 0`. Sampler price label `Free — $1.99 shipping`.
- Header try-sample URLs → `/products/free-1hour-after-athletic-sampler-pack`.
- Featured/frontpage “View all” → `/collections/all`.
- FAQ question name “WHAT IS THE RACE DAY KIT DESIGNED FOR?” (answers unchanged).
- Cart USD disclaimer visible until Markets.
- Lab template: HTML-comment leak converted to `{% comment %}`; loop closers explicit.
- Mobile: try-wrap visible; Race Day overlay `position: static`; logo TM max-width 58%.
- Why 1Hour After / Made clean `p` `text-transform: none`. Badge `h3` `overflow-wrap`. Icon alts from title metafields.
- jquery-1.10.2 dropped from `product-template.liquid` and `sample-product-template.liquid`. `custom-content` images request `format: 'webp'`.

### Admin (2024-10, client_credentials, `1hourafter.myshopify.com`)

- Menus `main-menu`, `mobile-menu`, `footern`: Labs/Lab removed; Affiliate → `/pages/affiliate-signup`. Footer menu already had no Labs.
- `featured-collection`: added Race Day Kit; reorder job put kit / anti-chafe / recovery in positions 0–2.
- Anti-chafe `product_icon6_title` = `Cruelty Free`.
- Marathon Pack compare-at `$120.00` (4 × `$30`). Typos FORMULATED / PREPARE.
- Anti-chafe Directions: `FOR BEST RESULTS`.
- Race Day Kit description: copied both balms’ Directions + Full ingredient list accordions (existing copy, no new claims).
- 18 News articles: four redirect URLs replaced at source. Hike + half-marathon recovery sampler CTAs retargeted to the Race Day Kit. Chafing, Hyrox, triathlon, marathon-checklist, wetsuit posts got a kit sentence where they had no kit URL.

## Deliberately not done

- Shopify Markets, CAD base-currency Support request, USD `.99` price list, Mlveda uninstall, cart-disclaimer deletion.
- Addly dashboard (exclude packs / recommend kit on balms). Theme CSS hides the widget on pack handles so native ATC can sell. Single-balm Addly left in place.
- Claim copy. Contact SLA/email. Glide Balm rename. Webkul FAQ pixel bug. Filling Labs. Homepage section-setting alts (those live in the theme editor JSON; not all are in git-exported settings).

## Rollback (Shopify)

Revert menus (re-add Lab pages; Affiliate resource `gid://shopify/Page/97379975341`). Remove kit from `featured-collection` or reorder shampoo first. `productUpdate` anti-chafe / marathon-pack / kit descriptions from Shopify versions. `productVariantsBulkUpdate` marathon-pack `compareAtPrice` to null. `metafieldsSet` icon6 to `freecruelty `. Revert the 18 `articleUpdate` bodies. `shopify theme push` `site/theme` from `main` / PR #15 onto theme `122661372077`. Git: revert this PR.
