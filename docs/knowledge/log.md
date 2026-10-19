# 1HR-After — operations log

> Append-only. Newest first. Karpathy prefix: `## [ISO_DATETIME] type | title`.
>
> Parse: `grep "^## \[" log.md | head -20`
>
> Types: `ingest` · `audit` · `citation-run` · `lint` · `query` · `fix` · `ship` · `infra`

<!-- AUTO-APPEND:timeline:START -->

## [2026-10-19T18:10:00Z] ship | Product tile size and separation

- Race Day Kit was taller than the row, so its photo met the Marathon Pack. Both pack cards are now the same square as the other products, and the lists have an 8px gap.
- On the collection page all eight tiles are 475×475 at 1440px and 390×390 on a phone. No tile boxes overlap.
- Filed [`analyses/2026-10-19-tile-separation.md`](analyses/2026-10-19-tile-separation.md).

## [2026-10-19T17:40:00Z] ship | Marathon Pack tile size

- The Marathon Pack card is a square matching the other product tiles. The bottle-group photo scales into the space under the title.
- On the collection page the conditioner and the pack are both 480×480 at desktop and 390×390 on a phone.
- Filed [`analyses/2026-10-19-marathon-pack-tile.md`](analyses/2026-10-19-marathon-pack-tile.md).

## [2026-10-16T21:05:00Z] ship | Subscribe and Save on the product template

- The product form now has Shopify’s `subscriptions_app_embed_block` mount, plus a one-time or monthly choice that submits `selling_plan`.
- Cooling Menthol Body Wash shows “Deliver every month, 10% off — $27.00”. A throwaway cart add took that plan and was cleared.
- Filed [`analyses/2026-10-16-subscribe-embed.md`](analyses/2026-10-16-subscribe-embed.md).

## [2026-10-16T20:45:00Z] ship | Grey first paint and Subscribe & Save

- The blank flash is the `#C7C4C4` page color while `theme.css` and `onehour.css` block the first paint. An inline ring now covers that wait and leaves after both files apply.
- Subscribe & Save was not removed. The shop and Cooling Menthol Body Wash have no selling plans, so the existing BSS block stays hidden.
- Filed [`analyses/2026-10-16-first-paint-spinner.md`](analyses/2026-10-16-first-paint-spinner.md).

## [2026-10-16T19:55:00Z] ship | Tile and Add to Cart layout

- Add to Cart is in the product column again. Review counts and pack contents no longer sit across the photos.
- The grey strip above Race Day Essentials was section padding. The Marathon Pack tile uses the square featured image.
- Filed [`analyses/2026-10-16-tile-atc-layout.md`](analyses/2026-10-16-tile-atc-layout.md). Prices, names, and claims copy were not changed.

## [2026-10-16T19:24:00Z] ship | Leftover claim lines and Phase 4

- Cleared the shampoo dandruff bullet, the shampoo and Marathon Pack repair lines, the Marathon Pack healing jojoba line, and the vitamin B5 anti-inflammatory line.
- Rewrote the claim answers in the product FAQ snippets and five homepage sentences. News article titles were classified and left in place.
- Filed [`analyses/2026-10-16-claims-phase4.md`](analyses/2026-10-16-claims-phase4.md). `docs/compliance/claims.md` was not edited.

## [2026-10-16T19:02:00Z] ship | Phase 3 remaining product copy

- Replaced the approved lines on the lotion, body wash, shampoo, conditioner, and Marathon Pack. Lotion and wash SEO descriptions were set with their titles.
- The bones, heart, and blood-pressure sentence on the lotion is gone. The inflammation bullet was removed.
- Filed [`analyses/2026-10-16-claims-phase3.md`](analyses/2026-10-16-claims-phase3.md). Phase 4 has not started. `docs/compliance/claims.md` was not edited.

## [2026-10-16T18:29:00Z] ship | Phase 2 zinc copy and Phase 1 leftovers

- Replaced the zinc ingredient sentences on the lotion, wash, shampoo, conditioner, and Marathon Pack. The extra Marathon Pack zinc line uses the nearest approved skin sentence.
- Cleared the balm image alts, the vitamin E repair line, “PAINFUL” on the anti-chafe balm, and the balm FAQ treatment answers. SEO titles were not sent, so they stayed put.
- Filed [`analyses/2026-10-16-claims-phase2.md`](analyses/2026-10-16-claims-phase2.md). Phase 3 has not started. `docs/compliance/claims.md` was not edited.

## [2026-10-16T18:20:00Z] ship | Phase 1 claims copy on three products

- Archived all eight product descriptions and SEO fields, then replaced the approved lines on Muscle Recovery Balm, Race Day Kit, and Anti Chafe Glide Balm.
- Balm SEO description is the cooling-feel sentence. SEO title was restored to the endurance-athletes title. The other five products were not edited.
- Filed [`analyses/2026-10-16-claims-phase1.md`](analyses/2026-10-16-claims-phase1.md). Phases 2–5 have not started.

## [2026-10-16T12:20:00Z] ship | Staged storefront fixes from homepage and PDP feedback

- Homepage grid shows six products, including the lotion and the body wash. Cards show Judge.me counts. Race Day Kit and Marathon Pack cards name their contents.
- Product pages: three bullets, quantity, kit link on the balms, long copy inside Benefits, Key Active Ingredients open, mobile Add to Cart on the viewport. Empty “What Athletes Are Saying?” block removed.
- Race Day buttons sit under the photo on small screens. Footer says LASTS LONGER. Homepage meta replaced. Spelling on the lotion and seven articles is Refueling.
- Prices were not changed. No “Save $52”. No free-shipping bar. Filed [`analyses/2026-10-16-storefront-feedback.md`](analyses/2026-10-16-storefront-feedback.md). Agents do not merge.

## [2026-10-15T21:05:00Z] ship | Hide the Try Free Sample button

- The Athletic Sampler stays draft. The header “try free sample” button, the homepage mobile sample bar, and the scrolling sample line are Liquid comments in `sections/header.liquid`.
- Live theme `#122661372077` header asset updated `2026-10-15T17:00:00-04:00`. Homepage at 1440px and 390px has no sample button. Logo, cart, and the runner photo remain.
- Filed [`analyses/2026-10-15-hide-try-sample.md`](analyses/2026-10-15-hide-try-sample.md). Agents do not merge.

## [2026-10-14T21:00:00Z] ship | Homepage taglines, Race Day buttons, blog tiles

- Race Day shop buttons share a baseline and stay inside the photo from 1000px through 1440px. Taglines use MonoSpec. The Body Recovery em dash is a period.
- Shop Pay is still on paid product pages. The two October 7 posts use different existing shop images.
- Filed [`analyses/2026-10-14-tagline-buttons-blog.md`](analyses/2026-10-14-tagline-buttons-blog.md). Agents do not merge.

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
