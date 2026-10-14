# 1HR-After — operations log

> Append-only. Newest first. Karpathy prefix: `## [ISO_DATETIME] type | title`.
>
> Parse: `grep "^## \[" log.md | head -20`
>
> Types: `ingest` · `audit` · `citation-run` · `lint` · `query` · `fix` · `ship` · `infra`

<!-- AUTO-APPEND:timeline:START -->

## [2026-10-14T20:30:00Z] ship | ATC alignment and first paint

- Title row height is auto. Body-wash button override under 1025px is removed. Race Day Kit price clears Shop Pay. Body wash matches the balms at 1000px.
- `theme.liquid` no longer hides `.main-content` until CSS arrives. Homepage hero and product photos still load. No `{width}` in image URLs.
- Filed [`analyses/2026-10-14-atc-and-first-paint.md`](analyses/2026-10-14-atc-and-first-paint.md). Agents do not merge.

## [2026-10-14T18:45:00Z] query | ATC alignment, CAD switcher, first paint

- Add to Cart differs because the title row is 70px tall and the body wash has its own rule under 1025px. Race Day Kit’s compare-at price overlaps Shop Pay.
- Header CAD is Mlveda. Shopify presents USD only. Primary market `uni` is the United States. Canada is already an active market. US Retail stays draft.
- Filed [`analyses/2026-10-14-atc-markets-first-paint.md`](analyses/2026-10-14-atc-markets-first-paint.md). No Shopify write.

## [2026-10-14T17:40:00Z] query | Page load and Race Day Kit bundle

- Cold loads: first paint ~0.3–0.4 s on a white page, product visible by 0.9 s, Addly bundle and CAD text by ~1.8 s. Server time to first byte was 18–46 ms on three of four pages.
- Race Day Kit stays its own offer. The pre-checked Addly pair with the Marathon Pack should come off. No Shopify write in this slice.
- Filed [`analyses/2026-10-14-page-load-review.md`](analyses/2026-10-14-page-load-review.md). Agents do not merge.

## [2026-10-14T16:55:00Z] ship | Visual fixes: banner, kit button, affiliate label, bundle dollar, blog images

- Body Recovery photo fills wide windows. Race Day Kit Add to Cart sits on the divider. Affiliate “SIGN UP NOW” is visible. Addly’s extra `$` is hidden. Two News posts have the existing anti-chafe stick as the featured image.
- Marathon Pack SKU `OH700-KIT` and Race Day Kit (no SKU) are different products. The bundle widget offers both.
- Filed [`analyses/2026-10-14-visual-fixes.md`](analyses/2026-10-14-visual-fixes.md). Agents do not merge.

## [2026-10-14T15:10:00Z] ship | Phased Oct 8 re-ship; mobile CSS rolled back

- Admin copy, 12 article links, Labs off three menus, featured order kit → anti-chafe → recovery. Theme: native Add to Cart on both packs; sampler reads `Free — $1.99 shipping`; Shop Pay hidden at $0.
- Mobile Race Day CSS shipped, covered the hero, and was rolled back with `--only assets/onehour.css`. WebP lazy-load filters stayed skipped.
- Filed [`analyses/2026-10-14-phased-oct8-reship.md`](analyses/2026-10-14-phased-oct8-reship.md). Agents do not merge.

## [2026-10-07T19:15:00Z] ship | Body Glide vs 1HR-A comparison + runners roundup

- Two evergreen News posts live: `/blogs/news/body-glide-vs-1hr-a-anti-chafe-balm` and `/blogs/news/best-anti-chafe-balm-for-runners`. Chafing guide now links both. No prices, no year titles, honest Body Glide-wins section.
- Class B proposed competitor-intel rows (Body Glide human-named). Filed [`analyses/2026-10-07-body-glide-comparison.md`](analyses/2026-10-07-body-glide-comparison.md). Agents do not merge.

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
