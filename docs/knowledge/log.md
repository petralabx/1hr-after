# 1HR-After — operations log

> Append-only. Newest first. Karpathy prefix: `## [ISO_DATETIME] type | title`.
>
> Parse: `grep "^## \[" log.md | head -20`
>
> Types: `ingest` · `audit` · `citation-run` · `lint` · `query` · `fix` · `ship` · `infra`

<!-- AUTO-APPEND:timeline:START -->

## [2026-10-08T16:00:00Z] ship | Oct 8 review: pack ATC, nav, homepage grid, typos (no Markets)

- Restored native Add to Cart on Race Day Kit and Marathon Pack (theme had hidden those two product ids). Labs out of live menus. Featured collection reordered kit / anti-chafe / recovery first. Sampler $0 Shop Pay gated. Redirect URLs replaced in 18 articles. No claim edits. Markets/CAD deferred for Stephen + Support.
- Filed [`analyses/2026-10-08-site-review.md`](analyses/2026-10-08-site-review.md). Agents do not merge.

## [2026-10-07T16:30:00Z] ship | SEO action-plan snippets, hike structure, Race Day Kit, collection H1

- Answer-first titles/metas whose numbers match the live articles. Hike product cards moved below the fold. Two old-slug 301s. Race pack renamed in title (handle unchanged). Collection pages render this collection. Featured/frontpage noindex. Affiliate-signup and `/apps/` not robots-blocked.
- Filed [`analyses/2026-10-07-seo-aeo-action-plan.md`](analyses/2026-10-07-seo-aeo-action-plan.md). Agents do not merge.

## [2026-10-06T21:30:00Z] ship | Archive gel, Organization schema, affiliate canonical, catalog hygiene

- Archived Recovery Body Gel (DRAFT + 301 to recovery balm). Deleted leftover `/blogs/test`; kept News. Canonical affiliate is `/pages/affiliate-signup`. Organization JSON-LD is `1Hour After` + Instagram. Published aligned Shop facts only. Vendor/type/title hygiene. FAQ claims not rewritten.
- Filed [`analyses/2026-10-06-seo-aeo-hygiene-org.md`](analyses/2026-10-06-seo-aeo-hygiene-org.md). Agents do not merge.

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
