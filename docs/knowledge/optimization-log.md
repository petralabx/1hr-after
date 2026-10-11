# Optimization log

> Ship log for organic pages and Meta tests. Newest first.
> Auto-generated metric blocks, if a steward is pointed here later, stay inside the markers.
>
> **Last updated:** 2026-10-07 (action-plan ship)

<!-- AUTO-APPEND:ships:START -->

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
