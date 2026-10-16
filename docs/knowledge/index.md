# 1HR-After — knowledge index

> Catalog of every page in this wiki.
> **Core pages** and **Outside this directory** are hand-maintained.
> **Analyses** is agent-maintained between the `AUTO-APPEND:analyses` markers.
>
> _Last hand-touched: 2026-10-06 (scaffold). Facts are not filled._

## Core pages

| Page | Summary | Owner |
|---|---|---|
| [backlinks.md](backlinks.md) | Incoming-link profile. Empty until a provider export is ingested. | Class B |
| [brand-voice.md](brand-voice.md) | Voice rules, forbidden terms, tone. Unfilled. | **Class C (human-only)** |
| [business-identity.md](business-identity.md) | Name, address, domain, email. Unfilled. Do not reuse another brand's identity. | **Class C (human-only)** |
| [competitor-intel.md](competitor-intel.md) | Tracked competitors. Canonical table empty; proposed Body Glide / SNB / Gold Bond / Chamois Butt’r rows 2026-10-07. | Class B |
| [content-style-guide.md](content-style-guide.md) | Draft and Meta ad writing rules. Structure only. | **Class C (human-only)** |
| [faq-corpus.md](faq-corpus.md) | Canonical Q&A. No questions yet. | Agent expands after voice exists |
| [icp.md](icp.md) | Ideal customer. Unfilled. | **Class C (human-only)** |
| [keyword-universe.md](keyword-universe.md) | Keyword table. Canonical empty; proposed Body Glide vs / best anti-chafe rows 2026-10-07. | Class B |
| [market-map.md](market-map.md) | Intent clusters and owning URLs. Canonical empty; proposed anti-chafe cluster 2026-10-07. | Class B |
| [optimization-log.md](optimization-log.md) | Ship and test log. Header only. | Mixed |
| [products.md](products.md) | Product roster. No SKUs until a human adds them. | Class B |
| [schema-state.md](schema-state.md) | Deployed structured data in the live Debut export (`#122661372077`). | Agent, once a theme exists |
| [target-queries.md](target-queries.md) | AEO prompts. Tracking off. | Strategy human; metrics agent |
| [best-practices/meta-ads.md](best-practices/meta-ads.md) | Meta placement and creative checklist. Confirm specs before launch. | Class B |
| [best-practices/README.md](best-practices/README.md) | How best-practice notes are filed. | Agent |

## Operational files

| Page | Purpose |
|---|---|
| [log.md](log.md) | Greppable timeline. `grep "^## \[" log.md \| head -20`. |
| [README.md](README.md) | Human navigation. |
| [index.md](index.md) | This file. |
| [analyses/README.md](analyses/README.md) | Filing rules for query answers. |

## Analyses

> _Filed query answers. Newest first._

<!-- AUTO-APPEND:analyses:START -->

- [Subscribe and Save on the product template](analyses/2026-10-16-subscribe-embed.md) — filed 2026-10-16 as `ship` · Shopify’s subscription mount is in the product form, with a one-time or monthly choice that submits the selling plan
- [The grey first paint and Subscribe & Save](analyses/2026-10-16-first-paint-spinner.md) — filed 2026-10-16 as `ship` · Grey first paint is now an orange loading ring that leaves when the stylesheets apply; Subscribe & Save is still gated and the shop has no selling plans
- [Tile and Add to Cart layout](analyses/2026-10-16-tile-atc-layout.md) — filed 2026-10-16 as `ship` · Add to Cart back in the column; reviews and pack text off the photos; grey strip above Race Day Essentials closed; Marathon Pack uses the square image
- [Leftover claim lines and Phase 4](analyses/2026-10-16-claims-phase4.md) — filed 2026-10-16 as `ship` · Shampoo and Marathon Pack leftovers, product FAQs, and five homepage sentences; news articles left for a decision
- [Phase 3 remaining product copy](analyses/2026-10-16-claims-phase3.md) — filed 2026-10-16 as `ship` · Lotion, wash, shampoo, conditioner, and Marathon Pack use the approved lines; SEO titles unchanged
- [Phase 2 zinc copy and the Phase 1 leftovers](analyses/2026-10-16-claims-phase2.md) — filed 2026-10-16 as `ship` · Zinc ingredient sentences on five products, balm image alts, vitamin E, the anti-chafe painful line, and the balm FAQ
- [Phase 1 claims copy on the three ad-linked products](analyses/2026-10-16-claims-phase1.md) — filed 2026-10-16 as `ship` · Balm, Race Day Kit, and anti-chafe descriptions and the balm SEO description use the approved lines; the other five products are unchanged
- [Staged storefront fixes from homepage and PDP feedback](analyses/2026-10-16-storefront-feedback.md) — filed 2026-10-16 as `ship` · Six-up homepage grid with lotion and body wash; card reviews and pack contents; PDP bullets, open ingredients, mobile Add to Cart; prices, rename, and a free-shipping bar left unchanged
- [Hide the Try Free Sample button](analyses/2026-10-15-hide-try-sample.md) — filed 2026-10-15 as `ship` · Header sample button, homepage mobile bar, and scrolling sample line are commented in `header.liquid` while the Athletic Sampler stays draft
- [Homepage taglines, Race Day buttons, and blog tiles](analyses/2026-10-14-tagline-buttons-blog.md) — filed 2026-10-14 as `ship` · Shop buttons share a baseline; taglines use MonoSpec; Body Recovery drops the em dash; the two October posts use different existing photos; Shop Pay stays on paid products
- [Add to Cart alignment and the first paint](analyses/2026-10-14-atc-and-first-paint.md) — filed 2026-10-14 as `ship` · Title row grows with the kit price; body wash matches the balms; the page is no longer hidden until CSS arrives
- [Add to Cart alignment, CAD switcher, first paint](analyses/2026-10-14-atc-markets-first-paint.md) — filed 2026-10-14 as `query` · Button mismatch is a fixed title row plus a body-wash rule; CAD is Mlveda; US and Canada markets already exist
- [Page load and the Race Day Kit bundle](analyses/2026-10-14-page-load-review.md) — filed 2026-10-14 as `query` · Blank first paint, then Addly and CAD; keep the Race Day Kit as its own offer
- [Visual fixes after the phased re-ship](analyses/2026-10-14-visual-fixes.md) — filed 2026-10-14 as `ship` · Full-bleed Body Recovery photo, kit button on the divider, affiliate label, one dollar sign in the bundle, blog tile images
- [Phased Oct 8 re-ship](analyses/2026-10-14-phased-oct8-reship.md) — filed 2026-10-14 as `ship` · Copy, article links, menus, featured order, pack Add to Cart, sampler price; mobile Race Day CSS tried and rolled back; WebP skipped
- [Body Glide comparison + anti-chafe roundup](analyses/2026-10-07-body-glide-comparison.md) — filed 2026-10-07 as `ship` · Evergreen vs post + runners roundup; proposed competitor rows; News publish + chafing cross-link
- [SEO/AEO action-plan ship](analyses/2026-10-07-seo-aeo-action-plan.md) — filed 2026-10-07 as `ship` · Snippets matching live copy; hike structure; two 404→301s; Race Day Kit; collection H1 template; noindex featured/frontpage
- [SEO/AEO hygiene + Organization](analyses/2026-10-06-seo-aeo-hygiene-org.md) — filed 2026-10-06 as `ship` · Archived gel; kept News blog; affiliate-signup canonical; Organization 1Hour After + Instagram; catalog hygiene; FAQ claims not rewritten
- [SEO/AEO post-ship review](analyses/2026-10-06-seo-aeo-post-ship-review.md) — filed 2026-10-06 as `audit` · Re-ran the four-query benchmark after PR #12; leftover gel PDP, sitemap noindex URLs, Shopify sameAs, affiliate trio ranked next
- [SEO/AEO live fixes](analyses/2026-10-06-seo-aeo-live-fixes.md) — filed 2026-10-06 as `ship` · Duplicate PDPs drafted + redirected; collection SEO; theme canonicals/0562/FAQ heading; live theme `#122661372077`
- [SEO/AEO catalog audit](analyses/2026-10-06-seo-aeo-catalog-audit.md) — filed 2026-10-06 as `audit` · Read-only Admin + storefront sample; 14 ACTIVE products; duplicate PDPs and empty collection SEO ranked highest; no Shopify write
- [Live Shopify theme audit](analyses/2026-10-06-live-shopify-theme-audit.md) — filed 2026-10-06 as `audit` · Published Debut `#122661372077` on 1hourafter.myshopify.com; SANDBOX not pulled; no Shopify write
- [Karpathy wiki scaffold for 1HR-After](analyses/2026-10-06-karpathy-wiki-scaffold.md) — filed 2026-10-06 as `infra` · Three-layer wiki, Meta ads lane, and the facts this repo deliberately does not contain yet

<!-- AUTO-APPEND:analyses:END -->

## Outside this directory

| Path | What it is |
|---|---|
| [../wiki-schema.md](../wiki-schema.md) | Schema layer. Read before editing the wiki. |
| [../sessions.md](../sessions.md) | Session handoff. Newest first. |
| [../sources/](../sources/) | Immutable raw sources. |
| [../channels/meta-ads.md](../channels/meta-ads.md) | Meta ads playbook. |
| [../compliance/claims.md](../compliance/claims.md) | Allowed claims. Empty. Class C. |
| [../../copy/content-drafts/](../../copy/content-drafts/) | Organic page drafts. |
| [../../copy/ads/meta/](../../copy/ads/meta/) | Meta ad copy archive. |
| [../../data/config.json](../../data/config.json) | Shopify and Meta account snapshot. `shopify.shopDomain` is `1hourafter.myshopify.com`. |
| [../../site/](../../site/) | Pulled live Debut theme under `site/theme/` (`#122661372077`). |
| [../design-system/](../design-system/) | Brand tokens. Out of scope for brand-ops edits. |
