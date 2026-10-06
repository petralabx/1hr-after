# 1HR-After — operations log

> Append-only. Newest first. Karpathy prefix: `## [ISO_DATETIME] type | title`.
>
> Parse: `grep "^## \[" log.md | head -20`
>
> Types: `ingest` · `audit` · `citation-run` · `lint` · `query` · `fix` · `ship` · `infra`

<!-- AUTO-APPEND:timeline:START -->

## [2026-10-06T20:45:00Z] audit | Post-ship SEO/AEO website review (no Shopify write)

- Re-ran the same four-query benchmark + Admin GraphQL after PR #12. 301s still hold on the storefront; Google still lists `/products/post-workout-body-care-set`. Ranked leftovers: `recovery-body-gel` ($0 / OutOfStock / leftover vendor), sitemap `sample-pack` and `/blogs/test`, three affiliate pages, Organization `sameAs` = Shopify Instagram.
- Filed [`analyses/2026-10-06-seo-aeo-post-ship-review.md`](analyses/2026-10-06-seo-aeo-post-ship-review.md). Class C untouched. No live writes.

## [2026-10-06T20:25:00Z] ship | Live SEO/AEO gap fixes on 1hourafter.myshopify.com

- Drafted four duplicate/thin ACTIVE products and 301'd their handles. Collection SEO filled; `frontpage` retitled. Missing sampler/page meta filled. Theme `#122661372077` pushed (canonical overrides, 0562 CDN, FAQ heading gate, ANTI CHAFE links).
- `write_publications` denied — `sample-pack` noindexed in Liquid instead of unpublished. MLVeda/Repair Remedy drafts not deleted.
- Filed [`analyses/2026-10-06-seo-aeo-live-fixes.md`](analyses/2026-10-06-seo-aeo-live-fixes.md). Class C untouched. Agents do not merge.

## [2026-10-06T19:55:00Z] audit | Read-only SEO/AEO catalog audit (no Shopify write)

- Admin GraphQL on `1hourafter.myshopify.com` (client-credentials; token prefix only). 35 products (14 ACTIVE), 6 collections, 10 pages, 51 articles, 39 redirects. `1hours.myshopify.com` was not called.
- Filed [`analyses/2026-10-06-seo-aeo-catalog-audit.md`](analyses/2026-10-06-seo-aeo-catalog-audit.md). Proposed roster labeled in [`products.md`](products.md); Class B not approved. Class C pages not rewritten.
- Highest-leverage gaps: duplicate live PDPs, collection SEO/canonicals, missing meta, FAQ id mismatches, crawl clutter (lab SKU, test blog, 0562 CDN). No live Shopify fixes.

## [2026-10-06T18:25:00Z] audit | Live Shopify theme pull (published Debut only)

- Pulled published theme `#122661372077` (`Theme export  1hours-myshopify-com-debut  03may…`) into `site/theme/`. SANDBOX `#143449981101` not pulled. No Shopify write.
- Theme Access authenticates on `1hourafter.myshopify.com`. Env `SHOPIFY_FLAG_STORE=1hours.myshopify.com` 401s.
- Filed [`analyses/2026-10-06-live-shopify-theme-audit.md`](analyses/2026-10-06-live-shopify-theme-audit.md). Recorded shop domain and observed GTM Meta pixel id in `data/config.json`.
- `--1hr-` tokens are unused in the theme. GTM `GTM-M4LGTWV` loads Meta pixel `1035858581719070`. No Furgenics or For & Against files.

## [2026-10-06T17:45:00Z] infra | Karpathy wiki and Meta ads lane scaffolded

- Added `docs/knowledge/` (index, log, Class B/C stubs, analyses), `docs/sources/`, `docs/wiki-schema.md`, `copy/content-drafts/`, `copy/ads/meta/`, `data/config.json`, and `site/` placeholder.
- Meta ads playbook is `docs/channels/meta-ads.md`. Account, pixel, and campaigns are unconfigured.
- No product roster, voice, claims, or Shopify domain. Do not backfill them from Furgenics or For & Against.

<!-- AUTO-APPEND:timeline:END -->
