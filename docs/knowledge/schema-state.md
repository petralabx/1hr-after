# Schema state

> **Owner:** Agent keeps this aligned with what is actually deployed.
> **Status:** Live Debut export in `site/theme/` (theme `#122661372077` on `1hourafter.myshopify.com`). Markup is Liquid JSON-LD, not a separate snippet app.
> **Last updated:** 2026-10-06 (catalog audit: FAQPage still product-id gated; several ACTIVE products have no FAQ JSON-LD)
> **Verified against:** theme pull + Admin product ids 2026-10-06. Raw HTML canonical/robots from this VM 429'd; WebFetch confirmed titles/H1s.

## Deployed

| Type | Where | Version | Last verified |
|---|---|---|---|
| Organization | `sections/header.liquid` JSON-LD | Debut 17.12; `sameAs` includes sample Shopify Instagram/Tumblr URLs from theme settings | 2026-10-06 |
| WebSite + SearchAction | `sections/header.liquid` (index only) | Debut 17.12 | 2026-10-06 |
| Product + Offer | `templates/product.liquid`, `product.preorder.liquid`, `product.sample-free.liquid`, `sections/featured-product.liquid` | schema.org Product | 2026-10-06 (code; homepage is not a product URL) |
| FAQPage | `snippets/faq-*.liquid` via `sections/faq-schema.liquid`, gated on hard-coded `product.id`s | schema.org FAQPage | 2026-10-06 (code). Wired for 9 ids; **not** wired for live `1hr-adaptogen-shampoo`, `post-workout-hair-care-kit`, `post-workout-body-care-set`, `lab-ss-001`, `recovery-body-gel`. Orphan snippet `faq-1hr-adaptogen-shampoo-stregthning.liquid` is unused. See [`analyses/2026-10-06-seo-aeo-catalog-audit.md`](analyses/2026-10-06-seo-aeo-catalog-audit.md) |
| Open Graph | `snippets/social-meta-tags.liquid` | Debut | 2026-10-06 |

## Not deployed

- BreadcrumbList (no snippet in this export; live homepage HTML has none)
- Organization with a real brand `sameAs` set (settings still point at `instagram.com/shopify`)

When Liquid JSON-LD here changes, update this table in the same PR. Do not paste a new JSON-LD example that could be mistaken for a second live copy.
