# Session log

Append-only handoff for humans and agents. **Newest entry at the top.**

Read the latest one to three entries at the start of a working session. Append a short entry in the same PR that lands the work.

This is separate from:

- [`knowledge/log.md`](knowledge/log.md) — operational timeline
- [`knowledge/optimization-log.md`](knowledge/optimization-log.md) — SEO, AEO, and Meta optimization history
- [`knowledge/analyses/`](knowledge/analyses/) — deep write-ups

## Entry format

```markdown
## YYYY-MM-DD — short title

- **Who:** name / agent runtime
- **PR:** #N or n/a
- **Done:** 1–3 bullets
- **Next:** open follow-ups
- **Watch:** risks or fragile files
```

---

## 2026-10-08 — Oct 8 site review (aligned slice only)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#17](https://github.com/petralabx/1hr-after/pull/17) (TASK-2546). CIP lands; agent cannot merge.
- **Done:** Independently verified the Oct 8 review. Restored native ATC on Race Day Kit and Marathon Pack. Labs out of nav. Homepage featured grid starts with kit / anti-chafe / recovery. Sampler $0 / Shop Pay. Typos, FAQ question rename, blog redirect URLs, kit Directions copied from both balms. No claim edits.
- **Next:** CIP merge. Stephen + Shopify Support for CAD base currency and USD `.99` market list before Markets. Optional later: Addly dashboard (recommend kit on single balms) once native ATC is confirmed live.
- **Watch:** Do not change store base currency or enter USD prices without Stephen sign-off. Do not edit product/ingredient claims. Do not call `1hours.myshopify.com`. Do not invent SKUs. App still lacks `write_publications`.

## 2026-10-07 — SEO action-plan live updates

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#15](https://github.com/petralabx/1hr-after/pull/15) (TASK-2514). CIP lands; agent cannot merge.
- **Done:** Agreed action-plan slice live on `1hourafter.myshopify.com`: snippets matching article numbers, hike structure, two old-slug 301s, Race Day Kit rewrite, homepage kit CTA added, collection H1 template, noindex featured/frontpage.
- **Next:** CIP merge. Optional later: evergreen Valentine/marathon-checklist slugs after the season; Body Glide comparison after sourced claims; gift-list trim if a human picks the keepers.
- **Watch:** Do not robots-block `/pages/affiliate-signup` or `/apps/`. App still lacks `write_publications`. Do not call `1hours.myshopify.com`. Do not invent SKUs.

## 2026-10-06 — Archive gel, Organization, affiliate canonical, catalog hygiene

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#14](https://github.com/petralabx/1hr-after/pull/14) (TASK-2459). CIP lands; agent cannot merge.
- **Done:** Archived Recovery Body Gel (not deleted). Kept `/blogs/news`, deleted leftover `/blogs/test`. Kept `/pages/affiliate-signup` and 301'd the other two affiliate URLs. Theme Organization name `1Hour After` + Instagram `sameAs`. Published only brand-aligned Shop facts. Catalog vendor/type/title hygiene. FAQ JSON-LD not rewritten.
- **Next:** Operator GSC recrawl of the 301 list. Class B on `products.md`. Gift-card / founding-year facts stay unpublished until confirmed.
- **Watch:** App still lacks `write_publications` (`sample-pack` noindex only). Do not call `1hours.myshopify.com`. Do not invent SKUs.

## 2026-10-06 — Live SEO/AEO gap fixes (Shopify write)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#12](https://github.com/petralabx/1hr-after/pull/12) (TASK-2388). Includes the TASK-2387 audit commits. CIP lands; agent cannot merge. Draft [#11](https://github.com/petralabx/1hr-after/pull/11) is the audit-only slice on the parent branch.
- **Done:** Drafted four duplicate/thin products and 301'd them. Collection SEO + theme canonicals. Sampler/page meta. Live theme push `#122661372077` (0562 CDN, ANTI CHAFE, FAQ heading gate).
- **Next:** CIP merge. Human Class B on `products.md`. `write_publications` if `sample-pack` should leave the sitemap. Do not invent SKUs.
- **Watch:** App lacks `write_publications`. Theme Access REST Asset API 401s; CLI password works on `1hourafter.myshopify.com`. Do not call `1hours.myshopify.com`.

## 2026-10-06 — Read-only SEO/AEO catalog audit (no Shopify write)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#11](https://github.com/petralabx/1hr-after/pull/11) (TASK-2387)
- **Done:** Queried live Admin (client-credentials, `1hourafter.myshopify.com` only). Sampled sitemaps/robots/`agents.md` plus WebFetch storefront. Filed [`knowledge/analyses/2026-10-06-seo-aeo-catalog-audit.md`](knowledge/analyses/2026-10-06-seo-aeo-catalog-audit.md). Proposed product table labeled in `products.md`; canonical Active table still empty.
- **Next:** Human approves Class B roster. Later TASK: one Shopify write for the highest-leverage duplicate-PDP gap, then re-run the same benchmark. Do not merge this PR from the agent. Do not `theme push`.
- **Watch:** This VM 429s HTML on `1hourafter.com` (robots/sitemaps succeeded). Never call Admin on `1hours.myshopify.com`. Do not invent SKUs. Class C still empty.

## 2026-10-06 — Pull live Shopify theme and audit (no Shopify write)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#10](https://github.com/petralabx/1hr-after/pull/10) (TASK-2384)
- **Done:** Pulled published Debut `#122661372077` into `site/theme/`. Recorded `1hourafter.myshopify.com` in `data/config.json`. Filed the audit under `docs/knowledge/analyses/`. SANDBOX not pulled.
- **Next:** Human fills Class C pages. Confirm Meta pixel `1035858581719070` in Events Manager before ads. Map `--1hr-` tokens onto the theme in a later task. Do not `theme push`.
- **Watch:** Theme Access 401s on `1hours.myshopify.com`; use `1hourafter.myshopify.com`. Stale `shopifypreview.com` preview_key and 0562 CDN URLs live in `settings_data.json`. Do not copy Furgenics or For & Against.

## 2026-10-06 — Brand repo scaffold (Furgenics shape, Meta ads, Karpathy wiki)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** open with this commit
- **Done:** Added the Karpathy wiki under `docs/knowledge/`, raw `docs/sources/`, content-draft templates, a site placeholder, `data/config.json`, and the Meta ads lane (`docs/channels/meta-ads.md`, `copy/ads/meta/`). Product facts, Shopify domain, and the Meta ad account are left blank.
- **Next:** A human fills Class C pages (`brand-voice.md`, `icp.md`, `business-identity.md`, `content-style-guide.md`, `compliance/claims.md`) and the Shopify plus Meta account rows in `data/config.json`. Then file real products in `docs/knowledge/products.md`.
- **Watch:** Do not paste Furgenics or For & Against copy, prices, or theme files into this repo. Do not invent SKUs or claims to make the empty tables look finished.
