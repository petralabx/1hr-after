# Optimization log

> Ship log for organic pages and Meta tests. Newest first.
> Auto-generated metric blocks, if a steward is pointed here later, stay inside the markers.
>
> **Last updated:** 2026-10-19 (QA theme published)

<!-- AUTO-APPEND:ships:START -->

## 2026-10-19 — storefront — QA theme published and affiliate form

- **Hypothesis:** The QA fixes were still on a preview theme, the balm still said "roll on", and the affiliate SIGN UP button had no form.
- **Change:** Theme `#189469851821` is live. The approved balm lines are on the product HTML. The affiliate page posts a contact form to the shop. See [`analyses/2026-10-19-publish-affiliate.md`](analyses/2026-10-19-publish-affiliate.md).
- **Result:** Chrome and Firefox show the form, a side-by-side desktop intro, and four steps in a row. Rankings not promised.
- **Source:** TASK-3394

## 2026-10-19 — storefront — Site QA preview

- **Hypothesis:** White FAQ answers, a footer Instagram link that stays on-site, broken star glyphs, uneven card type, and two empty signup bars were theme issues.
- **Change:** Those six items are fixed on unpublished theme `#189469851821`. See [`analyses/2026-10-19-site-qa-fixes.md`](analyses/2026-10-19-site-qa-fixes.md).
- **Result:** Chrome and Firefox on the preview show a readable FAQ answer, dark stars, one signup bar on the homepage and on `/collections/all`, and an Instagram link with `target="_blank"`. The published theme was not changed. Rankings not promised.
- **Source:** TASK-3392

## 2026-10-19 — storefront — Product tile size and separation

- **Hypothesis:** The Race Day Kit tile was taller than the row, so its grey photo ran into the Marathon Pack, and the pack photo was cropped to the pump tops.
- **Change:** Both pack cards are the same square as the other products. The photo fills the tile. Product lists have an 8px gap. See [`analyses/2026-10-19-tile-separation.md`](analyses/2026-10-19-tile-separation.md).
- **Result:** Collection tiles are 475×475 at desktop and 390×390 on a phone, with no overlapping boxes. Homepage featured tiles match once the photos load. Rankings not promised.
- **Source:** TASK-3368

## 2026-10-19 — storefront — Marathon Pack tile size

- **Hypothesis:** The Marathon Pack tile was taller than the other products because the photo kept its full height under a text band.
- **Change:** The pack card is a square. The bottle group scales into the space under the title. See [`analyses/2026-10-19-marathon-pack-tile.md`](analyses/2026-10-19-marathon-pack-tile.md).
- **Result:** On the collection page the pack matches the conditioner tile, 480×480 at desktop and 390×390 on a phone. Rankings not promised.
- **Source:** TASK-3358

## 2026-10-16 — storefront — Subscribe and Save

- **Hypothesis:** The selling plan was on the products, and the vintage product form had no place for Shopify’s subscription widget.
- **Change:** `subscriptions_app_embed_block` is inside the product form. A purchase-option group submits the selected selling plan and steps aside if the app embed fills the mount. See [`analyses/2026-10-16-subscribe-embed.md`](analyses/2026-10-16-subscribe-embed.md).
- **Result:** The body wash page shows one-time purchase and the monthly plan. A cart add with that plan returned the plan name. Rankings not promised.
- **Source:** TASK-3148

## 2026-10-16 — storefront — Grey first paint

- **Hypothesis:** The blank flash is the grey page color while `theme.css` and `onehour.css` block rendering.
- **Change:** Those files now load without blocking paint. An inline ring covers the grey and leaves when both have applied. See [`analyses/2026-10-16-first-paint-spinner.md`](analyses/2026-10-16-first-paint-spinner.md).
- **Result:** With the stylesheets held back, the ring is on screen. After they apply, the homepage hero and the body-wash Add to Cart are styled, and the ring is gone. Rankings not promised.
- **Source:** TASK-3140

## 2026-10-16 — catalog — Tile and Add to Cart layout

- **Hypothesis:** Overlapping Add to Cart, review text, the grey strip, and the wide Marathon Pack banner were hiding the products.
- **Change:** Button returned to the column. Pack text sits above the photo. Marathon Pack uses the square image. Race Day Essentials padding-top is 0. See [`analyses/2026-10-16-tile-atc-layout.md`](analyses/2026-10-16-tile-atc-layout.md).
- **Result:** Checked on the live theme at desktop and 390px. Rankings not promised.
- **Source:** TASK-3137

## 2026-10-16 — catalog — Leftover claim lines and Phase 4

- **Hypothesis:** Phase 3 left repair, dandruff, healing, and inflammation lines on the shampoo, the Marathon Pack, the FAQs, and the homepage.
- **Change:** Those lines now use skin and scalp wording. Homepage magnesium, zinc, vitamin, Race Day, and strengthening sentences were replaced. Prior copy is in [`../../sources/audits/2026-10-16-product-copy-before-phase4/README.md`](../../sources/audits/2026-10-16-product-copy-before-phase4/README.md). See [`analyses/2026-10-16-claims-phase4.md`](analyses/2026-10-16-claims-phase4.md).
- **Result:** The product pages and homepage show the new sentences. News articles were not edited. Rankings not promised.
- **Source:** TASK-3131

## 2026-10-16 — catalog — Phase 3 remaining product copy

- **Hypothesis:** The lotion, wash, shampoo, conditioner, and Marathon Pack still described inflammation, pain, conditions, bones, and heart health after Phase 2.
- **Change:** Approved sentences on those five products, including the lotion and wash SEO descriptions. Prior copy is in [`../../sources/audits/2026-10-16-product-copy-before-phase3/README.md`](../../sources/audits/2026-10-16-product-copy-before-phase3/README.md). See [`analyses/2026-10-16-claims-phase3.md`](analyses/2026-10-16-claims-phase3.md).
- **Result:** Those lines are on the live product records. A few lines outside the table, and the other FAQ snippets, are still in place. Rankings not promised.
- **Source:** TASK-3129

## 2026-10-16 — catalog — Phase 2 zinc copy and leftovers

- **Hypothesis:** Zinc blurbs and the leftover balm and anti-chafe lines still named conditions, pain, and repair after Phase 1.
- **Change:** Approved zinc sentences on five products, two balm image alts, the vitamin E span, the anti-chafe painful word, and the balm FAQ. Prior copy is in [`../../sources/audits/2026-10-16-product-copy-before-phase2/README.md`](../../sources/audits/2026-10-16-product-copy-before-phase2/README.md). See [`analyses/2026-10-16-claims-phase2.md`](analyses/2026-10-16-claims-phase2.md).
- **Result:** Those lines are on the live product records and the live theme FAQ. Phase 3 ingredient lines are still in place. Rankings not promised.
- **Source:** TASK-3120

## 2026-10-16 — catalog — Phase 1 claims copy

- **Hypothesis:** The three pages linked from Canada Meta ads still described pain relief, inflammation, cramps, and fungi.
- **Change:** Approved sentences on Muscle Recovery Balm, Race Day Kit, and Anti Chafe Glide Balm, including the balm SEO description. Prior copy is in [`../../sources/audits/2026-10-16-product-copy-before-claims/README.md`](../../sources/audits/2026-10-16-product-copy-before-claims/README.md). See [`analyses/2026-10-16-claims-phase1.md`](analyses/2026-10-16-claims-phase1.md).
- **Result:** Those lines are on the live product records. FAQ answers and one image alt on the balm still say pain relief. Rankings not promised.
- **Source:** TASK-3116

## 2026-10-16 — storefront — homepage grid, cards, and product page

- **Hypothesis:** The homepage stopped at four products because of a section limit, and the product page hid the useful lines under a wall of all-caps copy.
- **Change:** Six handles on the featured grid, review badges and pack contents on cards, bullets plus the existing accordions on the product page, mobile Add to Cart, Race Day buttons under the photo, footer and homepage meta, Refueling spelling. See [`analyses/2026-10-16-storefront-feedback.md`](analyses/2026-10-16-storefront-feedback.md).
- **Result:** Lotion and body wash render with the other four. Ingredient list is open. Long intro sits inside closed Benefits. Rankings not promised. Prices unchanged.
- **Source:** TASK-3065

## 2026-10-15 — storefront — hide Try Free Sample

- **Hypothesis:** The header sample button and the scrolling sample line still send people to a sampler that is draft because packs are short.
- **Change:** Three blocks in `sections/header.liquid` are Liquid comments labeled `RESTORE:`: the scrolling bar, the homepage mobile bar, and the “try free sample” button. See [`analyses/2026-10-15-hide-try-sample.md`](analyses/2026-10-15-hide-try-sample.md).
- **Result:** Homepage at 1440px and 390px shows no sample button and no sample-pack bar. Cart and the runner photo remain. Rankings not promised.
- **Source:** TASK-3041

## 2026-10-14 — storefront — taglines, Race Day buttons, blog tiles

- **Hypothesis:** The buttons drifted because the paragraphs wrapped to different heights, and the serif taglines were an EB Garamond override that loaded after MonoSpec.
- **Change:** Flex columns pin the shop buttons. Narrower desktops use smaller type so the buttons stay on the rock. Taglines are MonoSpec. The Body Recovery em dash is a period. Two existing shop photos replace the duplicate stick on the October posts. See [`analyses/2026-10-14-tagline-buttons-blog.md`](analyses/2026-10-14-tagline-buttons-blog.md).
- **Result:** Buttons align at 1000, 1100, 1200, 1366, and 1440. Taglines compute as MonoSpec. News tiles are the salve comparison and the park stick. Shop Pay still shows on the anti-chafe page. Rankings not promised.
- **Source:** TASK-2939

## 2026-10-14 — storefront — Add to Cart row and first paint

- **Hypothesis:** The mismatched buttons were a fixed 70px title row plus a body-wash rule, and the white hold was the theme hiding `.main-content` until CSS arrived.
- **Change:** `onehour.css` title-row height `auto` and the 1025px body-wash button override removed. `theme.liquid` loads `theme.css` and `onehour.css` as normal stylesheets and no longer hides the page. See [`analyses/2026-10-14-atc-and-first-paint.md`](analyses/2026-10-14-atc-and-first-paint.md).
- **Result:** Kit price clears Shop Pay. Body wash matches the balms at 1000px. Homepage hero `naturalWidth` 1241 and 1440. No `{width}` in image URLs. Rankings not promised.
- **Source:** TASK-2937

## 2026-10-14 — storefront — visual fixes after the phased re-ship

- **Hypothesis:** The screenshots were separate layout and app-markup bugs, not another missing-image WebP failure.
- **Change:** Full-bleed Body Recovery photo, kit button aligned to the divider, affiliate label color, hide Addly’s extra dollar span, featured images on the two new posts. See [`analyses/2026-10-14-visual-fixes.md`](analyses/2026-10-14-visual-fixes.md).
- **Result:** Wide banner is one photo. Bundle prices show one `$`. Blog tiles render. Homepage `_720x.png` is still HTTP 200 `image/png`. Rankings not promised.
- **Source:** TASK-2899

## 2026-10-14 — storefront + Admin — phased Oct 8 re-ship

- **Hypothesis:** The agreed Oct 8 fixes can land one surface at a time if each step keeps the homepage image loading.
- **Change:** Copy, article links, menus, featured order, pack Add to Cart, sampler price label, Shop Pay hidden at $0. Mobile overlay CSS was pushed, failed a 390px screenshot, and rolled back alone. WebP skipped. See [`analyses/2026-10-14-phased-oct8-reship.md`](analyses/2026-10-14-phased-oct8-reship.md).
- **Result:** Homepage `_720x.png` is HTTP 200 `image/png`. 390px after rollback shows the runner photo and both balm sticks. Pack and sampler `name="add"` present. Rankings not promised.
- **Source:** TASK-2893

## 2026-10-07 — storefront + Admin — Body Glide vs + anti-chafe roundup

- **Hypothesis:** “Body Glide vs 1Hour After” and “best anti-chafe balm for runners” had no answer-ready first-party owner.
- **Change:** Two evergreen News articles + chafing-guide cross-link. Proposed Class B competitor rows. See [`analyses/2026-10-07-body-glide-comparison.md`](analyses/2026-10-07-body-glide-comparison.md).
- **Result:** Live 200s, self-canonicals, SEO titles/metas verified this session. Search sample the same day did not yet show the new URLs (too new). Rankings not promised.
- **Source:** TASK-2518

## 2026-10-07 — storefront + Admin — action-plan snippets, hike, Race Day Kit, collections

- **Hypothesis:** CTR on already-ranking posts and thin identical collection URLs were the bottleneck, not a robots overhaul.
- **Change:** Title/meta/H1 rewrites whose numbers match live copy; hike structure; two 404→301s; race-pack rewrite + homepage kit CTA; collection-template H1; noindex featured/frontpage. See [`analyses/2026-10-07-seo-aeo-action-plan.md`](analyses/2026-10-07-seo-aeo-action-plan.md).
- **Result:** Live titles, collection H1s, 301s, and homepage kit CTA verified this session. Rankings not promised.
- **Source:** TASK-2514

## 2026-10-06 — storefront + Admin — gel archive, Organization, affiliate canonical

- **Hypothesis:** A $0 leftover gel PDP and Shopify sample `sameAs` were hurting catalog and entity signals more than another title tweak.
- **Change:** DRAFT gel + 301; delete test blog; keep News; keep affiliate-signup; Organization name + Instagram; vendor/type hygiene. See [`analyses/2026-10-06-seo-aeo-hygiene-org.md`](analyses/2026-10-06-seo-aeo-hygiene-org.md).
- **Result:** Live 301s and JSON-LD verified this session. Rankings not promised.
- **Source:** TASK-2459

## 2026-10-06 — storefront — post-ship re-measure (no write)

- **Hypothesis:** After the five-gap 301s, search would drop the mismatched lotion URL.
- **Change:** None on the store this round. Re-ran the same four queries. See [`analyses/2026-10-06-seo-aeo-post-ship-review.md`](analyses/2026-10-06-seo-aeo-post-ship-review.md).
- **Result:** Storefront 301s still hold. WebSearch still returns `/products/post-workout-body-care-set` for the lotion query (index lag). Highest leftover on-site: leftover `recovery-body-gel` PDP. Rankings not promised.
- **Source:** TASK-2389 read-only review

## 2026-10-06 — storefront + Admin — SEO/AEO five-gap ship

- **Hypothesis:** Duplicate live PDPs and forced collection canonicals were splitting query→page signals.
- **Change:** DRAFT + 301 four handles; collection SEO; theme canonicals / 0562 / FAQ heading / homepage preview URLs. See [`analyses/2026-10-06-seo-aeo-live-fixes.md`](analyses/2026-10-06-seo-aeo-live-fixes.md).
- **Result:** WebFetch confirms old duplicate URLs land on canonical PDPs; frontpage title is no longer `ActiveCollection`; homepage shows ANTI CHAFE (not CHEF) live links. Rankings not promised.
- **Source:** TASK-2388 live write on `1hourafter.myshopify.com`

<!-- AUTO-APPEND:ships:END -->

## How to append

```markdown
## YYYY-MM-DD — <surface> — <what changed>

- **Hypothesis:**
- **Change:**
- **Result:** TBD until measured
- **Source:** link to the draft or analysis
```

Meta results cite the campaign slug from [`../channels/meta-ads.md`](../channels/meta-ads.md).

## 2026-10-06 — catalog — SEO/AEO baseline (no Shopify write)

- **Hypothesis:** Duplicate live PDPs, empty collection SEO, and hardcoded FAQ ids are blocking query→page uniqueness more than copy tweaks.
- **Change:** None on the store. Filed [`analyses/2026-10-06-seo-aeo-catalog-audit.md`](analyses/2026-10-06-seo-aeo-catalog-audit.md) with a fixed benchmark (four queries, en-US, WebSearch + Admin GraphQL).
- **Result:** TBD until a follow-up task applies gap #1 and re-runs the same queries. Sampled visibility on 2026-10-06 is evidence, not a ranking.
- **Source:** that analysis. Next ship should be one Admin/theme write, then the same benchmark.
