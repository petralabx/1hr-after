# Schema state

> **Owner:** Agent keeps this aligned with what is actually deployed.
> **Status:** Live Debut export in `site/theme/` (theme `#122661372077` on `1hourafter.myshopify.com`). Markup is Liquid JSON-LD, not a separate snippet app.
> **Last updated:** 2026-10-06 (Organization name 1Hour After; sameAs Instagram only)
> **Verified against:** Live homepage JSON-LD after TASK-2459 theme push.

## Deployed

| Type | Where | Version | Last verified |
|---|---|---|---|
| Organization | `sections/header.liquid` JSON-LD | Debut 17.12; `name` is `1Hour After`; `sameAs` is Instagram `https://www.instagram.com/1hourafter/` only | 2026-10-06 |
| WebSite + SearchAction | `sections/header.liquid` (index only) | Debut 17.12 | 2026-10-06 |
| Product + Offer | `templates/product.liquid`, `product.preorder.liquid`, `product.sample-free.liquid`, `sections/featured-product.liquid` | schema.org Product | 2026-10-06 (code; homepage is not a product URL) |
| FAQPage | `snippets/faq-*.liquid` via `sections/faq-schema.liquid`, gated on hard-coded `product.id`s | schema.org FAQPage | 2026-10-06. Gel archived so it no longer needs FAQ. Claims not rewritten. Orphan snippet `faq-1hr-adaptogen-shampoo-stregthning.liquid` unused. |
| Open Graph | `snippets/social-meta-tags.liquid` | Debut | 2026-10-06 |

## Not deployed

- BreadcrumbList (no snippet in this export; live homepage HTML has none)
- Organization Facebook/YouTube `sameAs` (not invented; add when a human supplies the URLs)

When Liquid JSON-LD here changes, update this table in the same PR. Do not paste a new JSON-LD example that could be mistaken for a second live copy.
