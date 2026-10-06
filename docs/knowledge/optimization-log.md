# Optimization log

> Ship log for organic pages and Meta tests. Newest first.
> Auto-generated metric blocks, if a steward is pointed here later, stay inside the markers.
>
> **Last updated:** 2026-10-06 (baseline audit filed; no ship)

<!-- AUTO-APPEND:ships:START -->

_No ships yet._

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
