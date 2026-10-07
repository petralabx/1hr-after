# Body Glide comparison + anti-chafe roundup — 1HR-After

> Filed: 2026-10-07T19:00:00Z · Kind: ship
> Related: [`2026-10-07-seo-aeo-action-plan.md`](2026-10-07-seo-aeo-action-plan.md), [`../competitor-intel.md`](../competitor-intel.md), [`../products.md`](../products.md)

Operator asked to start the Body Glide comparison after CIP landed the action-plan slice (PR #15 / TASK-2514). This TASK writes two evergreen News posts, proposes Class B competitor rows, cross-links the existing chafing guide, and publishes live on `1hourafter.myshopify.com` only.

Shop: `1hourafter.myshopify.com`. Theme `#122661372077` not pushed (copy-only). CIP lands; this agent cannot merge.

## Benchmark (same loop; sampled visibility is evidence, not a rank)

```yaml
priority_pages:
  - https://1hourafter.com/blogs/news/body-glide-vs-1hr-a-anti-chafe-balm
  - https://1hourafter.com/blogs/news/best-anti-chafe-balm-for-runners
  - https://1hourafter.com/blogs/news/how-to-prevent-chafing-when-running
  - https://1hourafter.com/products/anti-chafe-balm
  - https://1hourafter.com/products/marathon-race-pack
target_queries:
  - "Body Glide vs 1Hour After anti-chafe balm"
  - "best anti-chafe balm for runners"
search_engines: [Google via WebSearch]
answer_engines: [WebSearch synthesis / AI-answer overlay]
locale: en-US
benchmark_method: "live URL 200 + title/H1/canonical + opening answer present; search sample recorded with date"
date: 2026-10-07
shop: 1hourafter.myshopify.com (shop id 56106188973)
public: 1hourafter.com
api: Admin GraphQL 2024-10, grant_type=client_credentials
```

## Query → page

| Query | Owner |
|---|---|
| Body Glide vs 1Hour After / 1HR-A anti-chafe | `/blogs/news/body-glide-vs-1hr-a-anti-chafe-balm` |
| best anti-chafe balm for runners | `/blogs/news/best-anti-chafe-balm-for-runners` |
| how to prevent chafing when running | existing `/blogs/news/how-to-prevent-chafing-when-running` (now links both) |

## What shipped

### Drafts (canonical markdown + HTML twins)

- [`../../../copy/content-drafts/body-glide-vs-1hr-a-anti-chafe-balm.md`](../../../copy/content-drafts/body-glide-vs-1hr-a-anti-chafe-balm.md)
- [`../../../copy/content-drafts/best-anti-chafe-balm-for-runners.md`](../../../copy/content-drafts/best-anti-chafe-balm-for-runners.md)

Evergreen titles (no year). No prices. No hold-time test. Honest **Body Glide wins** section (20+ years, four sizes, dry plant-wax, vegan, wetsuit-safe). 1HR-A wins on shea / coconut / tapioca / magnesium salts / piroctone olamine (named, not medicalized) and the [Race Day Kit](https://1hourafter.com/products/marathon-race-pack) pair. Sampler CTA states the sachets are **not** the balms. North America, not Made in Canada. Did not copy PDP “outperform the competition” or FAQ “outperform industry standards.”

### Shopify News (`gid://shopify/Blog/78468710573`)

Published as `Vincent Alton` (same author as the rest of News). SEO via `global.title_tag` / `global.description_tag`. Tags include `anti-chafe-balm` so Debut’s tag-match product card can render **after** the article (same pattern as the hike fix: cards stay below the body).

| Handle | Article title (H1) | SEO title | SEO description |
|---|---|---|---|
| `body-glide-vs-1hr-a-anti-chafe-balm` | Body Glide vs 1HR-A Anti-Chafe Balm: Which Stick Fits Runners? | Body Glide vs 1HR-A Anti-Chafe Balm for Runners | Body Glide Original is a dry plant-wax anti-chafe stick with 20+ years of use. 1HR-A adds shea, coconut oil, tapioca, and magnesium salts in a twist-up stick. See who each fits. |
| `best-anti-chafe-balm-for-runners` | Best Anti-Chafe Balm for Runners: Stick vs Cream by Use | Best Anti-Chafe Balm for Runners: Stick vs Cream | No single winner. Body Glide for a dry plant-wax stick, 1HR-A for shea and magnesium salts plus a race-day kit, SNB for four natural ingredients, Gold Bond for drugstore zinc oxide, Chamois Butt'r for cycling cream. |

### Cross-link

`how-to-prevent-chafing-when-running` (`gid://shopify/Article/561753325741`): one sentence under “Use Anti-Chafe Balms” pointing at both new posts. SEO title/meta unchanged.

### Class B proposed rows (not canonical)

[`../competitor-intel.md`](../competitor-intel.md), [`../target-queries.md`](../target-queries.md), [`../market-map.md`](../market-map.md), [`../keyword-universe.md`](../keyword-universe.md). Body Glide was human-named. SNB, Gold Bond, and Chamois Butt’r came with the operator-reviewed roundup. Meta ads still must not name competitors (`claims.md` empty).

## Sources (official pages, 2026-10-07)

| Brand | URL | Used |
|---|---|---|
| Body Glide Original | https://bodyglide.com/product/body/ | sizes, INCI, dry/vegan/no petroleum, wetsuit-safe |
| Body Glide ingredients | https://bodyglide.com/why-body-glide/ingredients/ | Original INCI |
| Body Glide about | https://bodyglide.com/about/ | Santa Barbara / 1996 LA Marathon / REI |
| 1HR-A Anti Chafe | https://1hourafter.com/products/anti-chafe-balm | INCI, directions, badges, handle |
| 1HR-A anti-chafe `.js` | https://1hourafter.com/products/anti-chafe-balm.js | SKU `OH800-KIT`, available true |
| SNB Original | https://squirrelsnutbutter.com/products/anti-chafe-sticks | four ingredients, Flagstaff |
| Gold Bond Friction Defense | https://www.goldbond.com/en-us/products/friction-defense | 1.75 oz unscented; INCI listed on that domain |
| Chamois Butt’r Original | https://www.chamoisbuttr.com/products/original-anti-chafe | cream; soothes already chafed; no parabens/phthalates/gluten/artificial fragrances |
| Chamois ingredients blog | https://www.chamoisbuttr.com/blogs/news/chamois-buttr-ingredients-what-do-they-mean-and-free-from-harsh-chemicals-list | common INCI; attributed as blog, not packing |

Not used as a company “made in USA” claim: customer reviews on Body Glide. Not used: W Sternoff / Bellevue factory location. Chamois full INCI is blog-attributed.

## Deliberately left

- No robots `Disallow` of affiliate-signup or `/apps/`
- No October slug 301s
- No magnesium-article merge
- No FAQ claim rewrite
- No prices in the new posts
- No year-stamped titles
- No hold-time / lab test
- No Made in Canada
- No invented “7 proven” / “9 fixes” / “treat in 24 hours”
- Theme not pushed
- Class C pages not rewritten
- Canonical Class B tables still empty (proposed sections only)

## Live checks (2026-10-07)

`articleCreate` ids: vs `gid://shopify/Article/634953957549`, roundup `gid://shopify/Article/634953990317`. Chafing update on `gid://shopify/Article/561753325741`.

| URL | Result |
|---|---|
| `/blogs/news/body-glide-vs-1hr-a-anti-chafe-balm` | 200. Title `Body Glide vs 1HR-A Anti-Chafe Balm for Runners`. Canonical self. Meta matches `description_tag`. Opening answer present. “Where Body Glide Original wins” present. No `outperform`. “Made in Canada” only as a negation. Product card after body (`sidenav-product-wrap`). |
| `/blogs/news/best-anti-chafe-balm-for-runners` | 200. Title `Best Anti-Chafe Balm for Runners: Stick vs Cream`. Canonical self. Opening “not one best.” Chamois Butt’r called a cream. Product card after body. |
| `/blogs/news/how-to-prevent-chafing-when-running` | 200. Title/meta unchanged. New sentence links both posts. |

Search sample 2026-10-07 en-US (WebSearch): the two new URLs were **not** in the first-page mix yet (published this session). `1hourafter.com/products/anti-chafe-balm` did appear among “Body Glide vs 1Hour After” results. That is evidence of recency, **not** a ranking.

Brand-repo validator: `python3 scripts/check-brand-repo-structure.py` exit 0.

## Rollback (Shopify)

Delete or unpublish the two new articles (`body-glide-vs-1hr-a-anti-chafe-balm`, `best-anti-chafe-balm-for-runners`). Revert the chafing article body to the pre-link version. Git: revert this PR. Class B proposed tables can stay or be dropped with the revert.
