# Schema state

> **Owner:** Agent keeps this aligned with what is actually deployed.
> **Status:** Live Debut export in `site/theme/` (theme `#122661372077` on `1hourafter.myshopify.com`). Markup is Liquid JSON-LD, not a separate snippet app.
> **Last updated:** 2026-10-06
> **Verified against:** this pull + `https://1hourafter.com/` HTML the same day.

## Deployed

| Type | Where | Version | Last verified |
|---|---|---|---|
| Organization | `sections/header.liquid` JSON-LD | Debut 17.12; `sameAs` includes sample Shopify Instagram/Tumblr URLs from theme settings | 2026-10-06 |
| WebSite + SearchAction | `sections/header.liquid` (index only) | Debut 17.12 | 2026-10-06 |
| Product + Offer | `templates/product.liquid`, `product.preorder.liquid`, `product.sample-free.liquid`, `sections/featured-product.liquid` | schema.org Product | 2026-10-06 (code; homepage is not a product URL) |
| FAQPage | `snippets/faq-*.liquid` via `sections/faq-schema.liquid`, gated on hard-coded `product.id`s | schema.org FAQPage | 2026-10-06 (code) |
| Open Graph | `snippets/social-meta-tags.liquid` | Debut | 2026-10-06 |

## Not deployed

- BreadcrumbList (no snippet in this export; live homepage HTML has none)
- Organization with a real brand `sameAs` set (settings still point at `instagram.com/shopify`)

When Liquid JSON-LD here changes, update this table in the same PR. Do not paste a new JSON-LD example that could be mistaken for a second live copy.
