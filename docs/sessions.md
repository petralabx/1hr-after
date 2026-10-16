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

## 2026-10-15 — Hide the Try Free Sample button

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#27](https://github.com/petralabx/1hr-after/pull/27) (TASK-3041). CIP lands; agent cannot merge.
- **Done:** Live on theme `#122661372077`. The header “try free sample” button, the homepage mobile sample bar, and the scrolling “TRY OUR FREE SAMPLE PACK” line are commented in [`site/theme/sections/header.liquid`](../site/theme/sections/header.liquid). Restore by removing the three `RESTORE:` comment wrappers and pushing that file. The Athletic Sampler stays draft.
- **Next:** CIP merge. At 390px the Race Day shop buttons still cross the stick labels. Do not fix that with `position: static` and `height: auto` on the Race Day block.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. Do not push the repo `settings_data.json` as a whole. Do not activate the draft US Retail market. Do not undraft the Athletic Sampler from this slice.

## 2026-10-14 — Homepage taglines, Race Day buttons, blog tiles

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#26](https://github.com/petralabx/1hr-after/pull/26) (TASK-2939). CIP lands; agent cannot merge.
- **Done:** Live on theme `#122661372077`. Race Day shop buttons share a baseline and stay on the photo from 1000px to 1440px. Both homepage taglines use MonoSpec. The Body Recovery line no longer uses an em dash. The two October 7 posts use different existing shop images. Shop Pay stays on paid products.
- **Next:** CIP merge. At 390px the Race Day shop buttons still cross the stick labels. Do not fix that with `position: static` and `height: auto` on the Race Day block.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. Do not push the repo `settings_data.json` as a whole. Do not activate the draft US Retail market.

## 2026-10-14 — ATC alignment and first paint

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#25](https://github.com/petralabx/1hr-after/pull/25) (TASK-2937). CIP lands; agent cannot merge.
- **Done:** Live on theme `#122661372077`. Title row grows so the Race Day Kit compare-at price clears Shop Pay. Body wash uses the same button rules as the balms under 1025px. `theme.liquid` loads the two stylesheets normally and no longer hides the page. Homepage hero and kit photos still load. Mlveda stays uninstalled. Markets were not changed.
- **Next:** CIP merge. `sections/header.liquid` still has a print copy of `onehour.css`. The kit button still nudges onto the line after load because that product has no stars.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. Do not activate the draft US Retail market. Do not reinstall Mlveda while Canada presents CAD.

## 2026-10-14 — ATC alignment, CAD switcher, first paint

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#24](https://github.com/petralabx/1hr-after/pull/24) (TASK-2927). CIP lands; agent cannot merge.
- **Done:** Explained the four-product Add to Cart mismatch, identified header CAD as Mlveda, and confirmed US (`uni`, primary) and Canada markets already exist with USD-only presentment. No Shopify write.
- **Next:** One CSS change so the kit price no longer covers Shop Pay and the body wash matches the balms under 1025px. Then the `theme.liquid` first-paint edit. Then CAD on the Canada market and Mlveda off together. Do not activate US Retail.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. Do not create a second US market.

## 2026-10-14 — Page load review and Race Day Kit bundle

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#23](https://github.com/petralabx/1hr-after/pull/23) (TASK-2921). CIP lands; agent cannot merge.
- **Done:** Measured homepage, both packs, and News with cache off. The blank first paint is the theme hiding `.main-content` until CSS loads. The second jump is Addly inserting the pre-checked Marathon Pack + Race Day Kit pair, then Mlveda writing CAD. Recommendation: keep the Race Day Kit as its own offer and turn that Addly pair off. No Shopify write.
- **Next:** Operator confirms the Addly pair comes off. Then one `theme.liquid` change for the blank first paint, with a screenshot before the next slice. Leave Mlveda CAD until the Markets decision.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. `product-template.liquid` still calls `dev.maxdigi.co` with a Judge.me token in the page. Do not copy that token into docs.

## 2026-10-14 — Visual fixes from operator screenshots

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#22](https://github.com/petralabx/1hr-after/pull/22) (TASK-2899). CIP lands; agent cannot merge.
- **Done:** Body Recovery photo is full-bleed on wide windows. Race Day Kit Add to Cart sits on the divider. Affiliate “SIGN UP NOW” is visible. Bundle prices show one dollar sign. The two October 7 posts have the existing anti-chafe stick as the featured image.
- **Next:** CIP merge. Race Day Kit still has no SKU; do not invent one. Compare-at prices ($120 Marathon Pack, $32.98 Race Day Kit) are still the crossed-out numbers.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'`. Do not call `1hours.myshopify.com`. Addly still offers Marathon Pack and Race Day Kit together on both pages.

## 2026-10-14 — Phased Oct 8 re-ship (mobile CSS rolled back)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#21](https://github.com/petralabx/1hr-after/pull/21) (TASK-2893). CIP lands; agent cannot merge.
- **Done:** Live on `1hourafter.myshopify.com`: copy fixes, 12 article link replacements, Labs off three menus, featured order kit / anti-chafe / recovery, native Add to Cart on both packs, sampler `Free — $1.99 shipping`, Shop Pay hidden at $0. Phase 7 mobile CSS was pushed, failed the 390px check (buttons covered the hero), and was rolled back with `--only assets/onehour.css`. WebP skipped.
- **Next:** CIP merge. A later single-file attempt can move the Race Day shop buttons off the balm labels. Do not reuse `position: static` plus `height: auto` on `#shopify-section-custom_content_Bq8YWE`.
- **Watch:** Do not add `format: 'webp'` on `img_url: '1x1'` lazy images. Do not call `1hours.myshopify.com`. Do not edit product or ingredient claims. Recovery balm still says “FOR EVEN MORE BETTER RESULTS”.

## 2026-10-07 — Body Glide comparison + anti-chafe roundup

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#16](https://github.com/petralabx/1hr-after/pull/16) (TASK-2518). CIP lands; agent cannot merge.
- **Done:** Published `/blogs/news/body-glide-vs-1hr-a-anti-chafe-balm` and `/blogs/news/best-anti-chafe-balm-for-runners` on `1hourafter.myshopify.com`. Cross-linked the chafing guide. Proposed Class B competitor-intel / query / market-map rows.
- **Next:** CIP merge. Optional later: GSC URL inspection on the two new posts; human Class B on the proposed tables.
- **Watch:** Do not name these competitors in Meta ads (`claims.md` still empty). Do not add prices. Do not robots-block affiliate-signup. Do not call `1hours.myshopify.com`.

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

## 2026-10-06 — Post-ship SEO/AEO website review (read-only)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** [#13](https://github.com/petralabx/1hr-after/pull/13) (TASK-2389). CIP lands; agent cannot merge.
- **Done:** Re-sampled live Admin + storefront + the same four WebSearch queries after [#12](https://github.com/petralabx/1hr-after/pull/12). Filed [`knowledge/analyses/2026-10-06-seo-aeo-post-ship-review.md`](knowledge/analyses/2026-10-06-seo-aeo-post-ship-review.md). No Shopify write.
- **Next:** Human picks one: DRAFT leftover gel, or theme `sameAs` Instagram, or unpublish sample-pack/test blog. GSC recrawl of 301'd URLs. Class B on `products.md`.
- **Watch:** App still lacks `write_publications`. Do not call `1hours.myshopify.com`. Do not invent SKUs or rewrite claims.

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
