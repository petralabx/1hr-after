# SEO/AEO post-ship website review — 1HR-After

> Filed: 2026-10-06T20:45:00Z · Kind: audit
> Related: [`2026-10-06-seo-aeo-live-fixes.md`](2026-10-06-seo-aeo-live-fixes.md), [`2026-10-06-seo-aeo-catalog-audit.md`](2026-10-06-seo-aeo-catalog-audit.md), [`../schema-state.md`](../schema-state.md), [`../products.md`](../products.md)

Read-only re-sample after [PR #12](https://github.com/petralabx/1hr-after/pull/12) merged (TASK-2388). **Shopify was not written.** No theme push. Class C pages were not rewritten. Sampled visibility is evidence, **not a ranking guarantee**.

Shop: `1hourafter.myshopify.com` only. `1hours.myshopify.com` was not called. Auth: client_id_len 32, secret_len 38, token prefix `shpa`, length 38.

## Benchmark (same as round 0)

```yaml
priority_pages:
  - https://1hourafter.com/
  - https://1hourafter.com/products/anti-chafe-balm
  - https://1hourafter.com/products/muscle-recovery-balm
  - https://1hourafter.com/products/muscle-recovery-magnesium-body-lotion
  - https://1hourafter.com/products/adaptogen-protein-strengthening-shampoo
  - https://1hourafter.com/blogs/news/how-to-prevent-chafing-when-running
target_queries:
  - "1Hour After anti chafe balm athletes"
  - "how to prevent chafing when running 1Hour After"
  - "1HR-A magnesium body lotion for athletes"
  - "site:1hourafter.com post-workout body care"
search_engines: [Google via WebSearch]
answer_engines: [WebSearch synthesis / AI-answer overlay]
locale: en-US
benchmark_method: "top results returned to this session; cite URL if 1hourafter.com appeared"
date: 2026-10-06
shop: 1hourafter.myshopify.com
```

Round 0 = TASK-2387 audit. Round 1 = TASK-2388 live five-gap ship. **This filing is round 1 re-measure + ranked leftovers.** No new live write.

## What already improved (do not re-do)

| Check | Live 2026-10-06 after #12 |
|---|---|
| ACTIVE products | 10 (was 14). Drafted dupes have `onlineStoreUrl: null` |
| `/products/1hr-adaptogen-shampoo` | 301 → adaptogen shampoo |
| `/products/post-workout-hair-care-kit` | 301 → muscle-recovery-balm |
| `/products/post-workout-body-care-set` | 301 → magnesium lotion (storefront). **Google WebSearch still lists the old URL** |
| `/products/lab-ss-001` | 301 → `/pages/lab-1hr` |
| Product sitemap | 10 PDPs + homepage. Drafted handles gone from sitemap |
| Frontpage title | `Post-Workout Body Care for Daily Athletes \| 1HR-After` |
| Sampler title | `Athletic Sampler Pack \| 1HR-After` |
| `/affiliate-signup` path | 301 → `/pages/affiliate-signup` |
| Homepage | `SHOP ANTI CHAFE BALM` live product URLs |
| `sample-pack` / `/blogs/test` | `robots: noindex` (both still in sitemaps) |

## Sampled visibility (re-run, en-US, WebSearch)

| query | engine | locale | date | result vs round 0 |
|---|---|---|---|---|
| 1Hour After anti chafe balm athletes | Google via WebSearch | en-US | 2026-10-06 | Canonical `/products/anti-chafe-balm` still present. Also marathon-race-pack, homepage, EIN presswire |
| how to prevent chafing when running 1Hour After | Google via WebSearch | en-US | 2026-10-06 | Canonical article still present, plus anti-chafe PDP. Third-party how-tos still compete |
| 1HR-A magnesium body lotion for athletes | Google via WebSearch | en-US | 2026-10-06 | Canonical lotion URL **and** `/products/post-workout-body-care-set` still returned (index lag; live 301 works) |
| site:1hourafter.com post-workout body care | Google via WebSearch | en-US | 2026-10-06 | Body wash, blogs, homepage, **and** the old body-care-set URL still in the set |

## Ranked remaining website improvements

Impact heuristic: critical technical first, then intent/answer, then schema/citations, then metadata. **Next live TASK should pick one.**

### 1. High — leftover live SKU `recovery-body-gel`

Indexed (`sitemap_products_1.xml`). Title `Recovery BodyGel`. Admin vendor `Company 1234`, type `Repair Remedy Duo22`. Storefront Product JSON-LD: `availability: OutOfStock`, **`price: 0.0`**, brand `Company 1234`. No FAQPage. Looks like a Repair Remedy clone that stayed ACTIVE.

Human Class B choice: DRAFT + 301 (if it is not a real SKU) **or** give it a real title, vendor `1hourafter`, SKU, price, and FAQ. Do not invent a SKU in the wiki.

### 2. High — sitemap still advertises noindex URLs

| URL | Storefront | Sitemap |
|---|---|---|
| `/collections/sample-pack` | empty, `robots: noindex` | yes (all 6 collections) |
| `/blogs/test` | live blog titled `test`, `robots: noindex` | yes |

Shopify URL redirect `/blogs/test` → `/blogs/news` exists in Admin but **does not fire** because the blog resource still exists. Unpublishing `sample-pack` from Online Store needs `write_publications` (denied on this app) **or a human in Admin**. Deleting or unpublishing the `test` blog is a human/Admin content action.

Until then, Google sees a sitemap URL that the HTML says not to index.

### 3. High — three affiliate pages still compete

All published, all in the page sitemap, overlapping titles:

- `/pages/affiliate` — `Join the 1HR-A Affiliate Program for Athletes \| 1HR-A`
- `/pages/affiliate-signup` — `Join Our Affiliate Program - Earn Commissions \| 1HR-A`
- `/pages/athletic-affiliate-program-in-usa-and-canada` — 89-char title with a leading space; only one of the three has an H1

Pick one owner, 301 the other two. The path `/affiliate-signup` already 301s to the middle page, which is the wrong hop if the long-form page is the keeper.

### 4. High — Organization `sameAs` still Shopify sample socials

Live homepage JSON-LD:

```json
"sameAs": ["", "", "", "http://instagram.com/shopify", "http://shopify.tumblr.com", "", "", ""]
```

Footer already links `https://www.instagram.com/1hourafter/`. Theme setting `social_instagram_link` is still `http://instagram.com/shopify`. Answer engines that read Organization markup will cite Shopify, not the brand. Cheap theme-settings fix; needs the real Facebook/YouTube URLs from a human if those exist. Do not invent them.

Shop knowledge-base facts (12) are all `published: false`. Shop/UCP/`agents.md` are live; Google HTML is not getting those facts.

### 5. Medium-high — query → page ownership still fuzzy

| Query | Best live URL | Problem |
|---|---|---|
| How to prevent chafing when running | article **and** `/products/anti-chafe-balm` | Both rank. Pick one owner; cross-link the other |
| What is 1Hour After? | `/` or `/pages/about-us` | Homepage H1 is `1hourafter`. About H1 is `WELCOME TO A NEW ERA IN ACTIVE RECOVERY`. Neither is an answer-first definition |
| Magnesium lotion | canonical PDP | Google still shows the drafted URL until recrawl |
| Recovery gel | `/products/recovery-body-gel` | $0 / OOS / leftover vendor — see #1 |

[`../target-queries.md`](../target-queries.md) is still empty (strategy human).

### 6. Medium-high — FAQ / claims still blocked on Class C

Nine PDPs emit FAQPage JSON-LD. Gel does not. Copy in those snippets still has unapproved medical-adjacent language. [`../../compliance/claims.md`](../../compliance/claims.md) and [`../faq-corpus.md`](../faq-corpus.md) are empty. **Do not rewrite FAQ answers** until claims exist. Orphan snippet `faq-1hr-adaptogen-shampoo-stregthning.liquid` is still unused.

### 7. Medium — catalog hygiene on the 10 ACTIVE products

- Vendors: `Company 123`, `Company 1234`, `1 HRA` mixed with `1hourafter`
- Types: body wash = `Lotion & Moisturizer`; lotion = `Repair Remedy Duo2`; gel = `Repair Remedy Duo22`
- Blank SKUs: `muscle-recovery-balm`, `recovery-body-gel`, `marathon-race-pack` — do not invent
- Sampler Admin **title** still `Free 1Hour-After Athletic Sampler Pack |` (trailing pipe); SEO title was fixed
- H1s on several PDPs are ALL CAPS
- Marathon pack SEO title is 29 chars (`The Marathon Pack | 1HR-After`)
- 25 DRAFT products remain (MLVeda sentinels, 13 Repair Remedy clones, duplicate sampler `1hr-a-sample-pack`). Leave them unless a human says delete
- Redirect **chains** still hop 2–3 times (`repair-remedy-duo` → old shampoo handles → canonical)

### 8. Medium — markets / merchandising

Primary market handle is `uni` (enabled). **US Retail is disabled**. Canada + International enabled. Plan is Shopify (not Plus). Conversion and US ads can disagree with that market map; a human decides.

### 9. Lower — structured data polish

- No BreadcrumbList
- Recovery gel Offer `price: 0.0` + OutOfStock
- Article schema on the chafing post, no FAQPage
- One published news article still missing `title_tag`: `you-should-not-be-overly-sore-after-a-workout-let-s-fix-that`
- Lab page has SEO but no H1

## Recommended next write (one loop)

Highest-leverage single fix, after a human nods:

1. **If gel is not a real SKU:** DRAFT `recovery-body-gel` + 301 to magnesium lotion or Lab. Same pattern as TASK-2388.
2. **If gel is real:** Class B roster + price/vendor/SKU, then FAQ only after claims.
3. **Parallel cheap theme fix (does not need claims):** set `social_instagram_link` to `https://www.instagram.com/1hourafter/` and clear Shopify Tumblr so Organization `sameAs` matches the footer.
4. Then **GSC URL inspection** on the four 301'd handles so Google drops `post-workout-body-care-set`.

Do not invent SKUs. Do not rewrite Class C. Agents do not merge.

## Deliberately not done this TASK

- No Admin mutation, no theme push.
- Canonical [`../products.md`](../products.md) Active table still empty.
- No Furgenics / For & Against. No COGS.

## Verification (no tokens)

```bash
python3 -c 'import os; print("client_id_len", len(os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_ID"])); print("client_secret_len", len(os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_SECRET"]))'
# expect 32 and 38
python3 scripts/check-brand-repo-structure.py
curl -sS -o /dev/null -w '%{http_code} %{redirect_url}\n' https://1hourafter.com/products/post-workout-body-care-set
curl -sS https://1hourafter.com/ | python3 -c "import sys,re; h=sys.stdin.read(); print(re.search(r'instagram.com/[^\"]+', h).group(0) if re.search(r'instagram.com/[^\"]+', h) else 'no ig')"
```
