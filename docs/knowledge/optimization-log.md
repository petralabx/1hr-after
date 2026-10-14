# Optimization log

> Ship log for organic pages and Meta tests. Newest first.
> Auto-generated metric blocks, if a steward is pointed here later, stay inside the markers.
>
> **Last updated:** 2026-10-14 (taglines, buttons, blog tiles)

<!-- AUTO-APPEND:ships:START -->

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
