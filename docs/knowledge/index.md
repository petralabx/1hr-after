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
| [competitor-intel.md](competitor-intel.md) | Tracked competitors. Empty table. | Class B |
| [content-style-guide.md](content-style-guide.md) | Draft and Meta ad writing rules. Structure only. | **Class C (human-only)** |
| [faq-corpus.md](faq-corpus.md) | Canonical Q&A. No questions yet. | Agent expands after voice exists |
| [icp.md](icp.md) | Ideal customer. Unfilled. | **Class C (human-only)** |
| [keyword-universe.md](keyword-universe.md) | Keyword table. Empty. | Class B |
| [market-map.md](market-map.md) | Intent clusters and owning URLs. Empty. | Class B |
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
