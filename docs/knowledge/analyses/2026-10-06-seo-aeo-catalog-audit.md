# SEO / AEO catalog audit — 1HR-After

> Filed: 2026-10-06T19:55:00Z · Kind: audit
> Related: [`2026-10-06-live-shopify-theme-audit.md`](2026-10-06-live-shopify-theme-audit.md), [`../schema-state.md`](../schema-state.md), [`../products.md`](../products.md), [`../target-queries.md`](../target-queries.md), [`../../../data/config.json`](../../../data/config.json)

Read-only Admin GraphQL + public storefront sample. **Shopify was not written.** No mutations, no theme push, no product/page/redirect updates. Furgenics and For & Against content was not copied. Class C pages were not rewritten. [`../products.md`](../products.md) stays Class B: the roster below is **proposed from the live catalog**, not canonical.

Sampled visibility is evidence of what this session saw, **not a ranking guarantee**.

## Benchmark (fixed; re-run on the next loop)

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
shop: 1hourafter.myshopify.com (shop id 56106188973)
public: 1hourafter.com
theme: Debut #122661372077 (already in site/theme/; not re-pulled)
api: Admin GraphQL 2024-10, grant_type=client_credentials
```

This PR is **round 0 / baseline only**. The skill says to fix the single highest-leverage gap next; that write is a **follow-up task**. Do not apply live Shopify fixes from this analysis.

## How Admin was queried (read-only)

| Item | Evidence |
|---|---|
| Shop | `1hourafter.myshopify.com` only. `1hours.myshopify.com` was **not** called |
| Env | `ONEHR_AFTER_SHOPIFY_CLIENT_ID` length 32; `ONEHR_AFTER_SHOPIFY_CLIENT_SECRET` length 38. Values never echoed, logged, or committed |
| Grant | `POST /admin/oauth/access_token` with `grant_type=client_credentials`. Client id/secret were **not** sent as `X-Shopify-Access-Token` |
| Token proof | kind prefix `shpa`, length 38, `expires_in` 86399. Prefix only; token not printed |
| GraphQL | `https://1hourafter.myshopify.com/admin/api/2024-10/graphql.json` |
| Scopes observed | `write_products`, `write_content`, `write_online_store_navigation`, `write_files`, `write_metaobjects`, `read_metaobject_definitions`, `write_translations`, `read_locales`, `read_markets`, `read_publications`, `read_themes` |
| Mutations this session | **0** |
| Shop query | `myshopifyDomain=1hourafter.myshopify.com`, primary host `1hourafter.com`, currency USD, tz `America/Toronto`, plan Shopify (not Plus) |

`Page.seo` and `Article.excerpt` / `Article.onlineStoreUrl` are not on this API version. Page/article SEO came from `global.title_tag` / `global.description_tag` metafields. Product and collection SEO used the `seo { title description }` field.

### Verification commands (no tokens printed)

```bash
python3 -c 'import os; print("client_id_len", len(os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_ID"])); print("client_secret_len", len(os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_SECRET"]))'
# expect 32 and 38

python3 - << 'PY'
import json, os, urllib.request
shop = "1hourafter.myshopify.com"
assert shop != "1hours.myshopify.com"
payload = json.dumps({
    "grant_type": "client_credentials",
    "client_id": os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_ID"],
    "client_secret": os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_SECRET"],
}).encode()
req = urllib.request.Request(
    f"https://{shop}/admin/oauth/access_token",
    data=payload,
    headers={"Content-Type": "application/json"},
)
with urllib.request.urlopen(req, timeout=30) as r:
    tok = json.loads(r.read().decode())
token = tok["access_token"]
print("token_kind_prefix", token[:4], "token_len", len(token), "expires_in", tok.get("expires_in"))
print("scope_count", len(tok.get("scope", "").split(",")))
q = json.dumps({"query": "{ shop { myshopifyDomain primaryDomain { host } } }"}).encode()
req2 = urllib.request.Request(
    f"https://{shop}/admin/api/2024-10/graphql.json",
    data=q,
    headers={"Content-Type": "application/json", "X-Shopify-Access-Token": token},
)
with urllib.request.urlopen(req2, timeout=30) as r:
    data = json.loads(r.read().decode())["data"]["shop"]
print("shop", data["myshopifyDomain"], "host", data["primaryDomain"]["host"])
print("used_client_creds_as_access_token", token in (os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_ID"], os.environ["ONEHR_AFTER_SHOPIFY_CLIENT_SECRET"]))
PY
# expect: token_kind_prefix shpa; shop 1hourafter.myshopify.com; used_client_creds_as_access_token False

python3 scripts/check-brand-repo-structure.py
```

## Catalog counts (live Admin, 2026-10-06)

| Resource | Count | Notes |
|---|---|---|
| Products | 35 | **14 ACTIVE**, 21 DRAFT |
| Collections | 6 | Zero SEO titles/descriptions |
| Pages | 10 | All `isPublished` |
| Blogs | 2 | `news` (50 articles), `test` (1 article) |
| Articles | 51 | 38 published, 13 unpublished |
| URL redirects | 39 | Several multi-hop chains; one affiliate loop |
| Publications | 6+ | Online Store, POS, Google & YouTube, Facebook & Instagram, Shop, TikTok. Product `resourcePublications` also showed **Microsoft Copilot** and **Meta AI and Muse** |
| Locales | 1 | `en` primary, published |
| Markets | 4 | Primary **`uni`** (enabled); Canada + International enabled; **US Retail disabled** |
| Metaobject definitions | 1 | `shopify--knowledge-base-fact` (12 facts) |
| Metaobjects | 13 | All sampled facts `published: false` (Shopify agentic / UCP suggestions, not public FAQ) |

Sitemap index (live `200`): products (15 loc, includes homepage), pages (10), collections (6), blogs (40), plus `sitemap_agentic_discovery.xml` → [`https://1hourafter.com/agents.md`](https://1hourafter.com/agents.md).

`/collections/all` is **not** in the collections sitemap (Shopify automatic collection). Theme Liquid still forces some collection canonicals there.

## Proposed product roster (live catalog only — Class B)

Do **not** invent SKUs. Empty SKU cells are empty in Admin. Duplicate titles/handles are the live catalog, not a naming suggestion. Human must approve before this is canonical in [`../products.md`](../products.md).

### ACTIVE (Online Store published)

| Observed SKU | Admin title | Handle / URL | Desc chars | SEO title | SEO desc | FAQ schema in theme? | Notes |
|---|---|---|---|---|---|---|---|
| OH100 | ADAPTOGEN PROTEIN STRENGTHENING SHAMPOO | [adaptogen-protein-strengthening-shampoo](https://1hourafter.com/products/adaptogen-protein-strengthening-shampoo) | 5383 | yes (60) | yes (151) | yes (`6668255461549`) | Core PDP |
| OH100-A | ADAPTOGEN PROTEIN STRENGTHENING SHAMPOO | [1hr-adaptogen-shampoo](https://1hourafter.com/products/1hr-adaptogen-shampoo) | 787 | yes (55) | yes (149) | **no** (id `7286045999277`; unused snippet `faq-1hr-adaptogen-shampoo-stregthning.liquid`) | **Duplicate title**; thinner body; $35 vs $30 sibling |
| OH800-KIT | ANTI CHAFE GLIDE BALM | [anti-chafe-balm](https://1hourafter.com/products/anti-chafe-balm) | 3417 | yes (52) | yes (148) | yes (`7878684934317`) | Core PDP; sampled sold out |
| OH300-FBA | COOLING MENTHOL BODY WASH | [cooling-menthol-body-wash](https://1hourafter.com/products/cooling-menthol-body-wash) | 3715 | yes (57) | yes (160) | yes (`6668255723693`) | Product type is wrongly `Lotion & Moisturizer` |
| OHSP50 | Free 1Hour-After Athletic Sampler Pack \|Post Workout Recovery Products | [free-1hour-after-athletic-sampler-pack](https://1hourafter.com/products/free-1hour-after-athletic-sampler-pack) | 6865 | **missing** | yes (143) | yes (`7389948575917`) | Same SKU as draft `1hr-a-sample-pack` |
| 2 | LAB/SS-001 | [lab-ss-001](https://1hourafter.com/products/lab-ss-001) | 215 | yes (58) | **missing** | no | Thin lab leftover; **in sitemap**; $4 sold out |
| OH701-KIT | Muscle Recovery Balm | [post-workout-hair-care-kit](https://1hourafter.com/products/post-workout-hair-care-kit) | 1013 | **missing** | **missing** | no | **Handle/title mismatch**; WebFetch title is Muscle Recovery Balm; empty FAQ heading |
| *(blank)* | Muscle Recovery Balm | [muscle-recovery-balm](https://1hourafter.com/products/muscle-recovery-balm) | 3745 | yes (59) | yes (142) | yes (`7878684901549`) | Core PDP; SKU blank in Admin; sampled sold out |
| *(blank)* | Recovery BodyGel | [recovery-body-gel](https://1hourafter.com/products/recovery-body-gel) | 752 | yes (38) | yes (148) | no | Thin vs core PDPs |
| OH600-FBA | REFUELING MAGNESIUM BODY LOTION | [muscle-recovery-magnesium-body-lotion](https://1hourafter.com/products/muscle-recovery-magnesium-body-lotion) | 3841 | yes (60) | yes (141) | yes (`6668255920301`) | Core PDP |
| *(blank)* | REFUELING MAGNESIUM BODY LOTION | [post-workout-body-care-set](https://1hourafter.com/products/post-workout-body-care-set) | 830 | **missing** | **missing** | no | **Duplicate title**; description talks about a *set* / body wash |
| OH200 | Strengthening Protein Conditioner | [strengthening-protein-conditioner](https://1hourafter.com/products/strengthening-protein-conditioner) | 6243 | yes (57) | yes (144) | yes (`7145590358189`) | Core PDP |
| OH700-KIT | The Marathon Pack | [marathon-pack](https://1hourafter.com/products/marathon-pack) | 4594 | yes (31) | yes (154) | yes (`7162482262189`) | Short SEO title |
| *(blank)* | THE MARATHON RACE PACK | [marathon-race-pack](https://1hourafter.com/products/marathon-race-pack) | 3026 | yes (32) | yes (153) | yes (`8140422578349`) | SKU blank |

Vendors on live products are inconsistent (`Company 123`, `Company 1234`, `1hourafter`, `1 HRA`). Product types include leftovers (`Repair Remedy Duo2`, `Repair Remedy Duo22`). Not a roster to copy into ads or Class B until a human picks the real SKUs.

### DRAFT (not a storefront roster)

| Observed SKU | Title | Handle | Why it is here |
|---|---|---|---|
| OHSP50 | 1HR-A Sample Pack | `1hr-a-sample-pack` | Draft duplicate of the live sampler SKU |
| *(blank)* | coming soon | `1hour-after-cooling-body-gel` | Theme `noindex` if this handle is ever published (`handle contains '1hour-after-cooling-body-gel'`) |
| *(blank)* | DO NOT DELETE THIS PRODUCT - MLVEDA | `do-not-delete-this-product-mlveda` (+ `-1`) | Currency-app sentinels |
| *(blank)* | Join 1Hour-After’s Sports & Athletic Affiliate Program | `join-1hour-after-s-sports-athletic-affiliate-program` | Product-shaped affiliate page |
| 4 / 5 / 8 / blank | Repair Remedy Duo2…20 | `repair-remedy-duo2` … `repair-remedy-duo20` | **13 clone drafts**; numeric leftover SKUs |

## Collections, pages, blogs

### Collections — all missing SEO

| Handle | Title | Products | SEO title | SEO desc | Live sample |
|---|---|---|---|---|---|
| frontpage | ActiveCollection | 8 | none | 30-char desc | WebFetch H1/title **ActiveCollection** |
| featured-collection | Featured Collection | 8 | none | none | Theme forces canonical → `/collections/all` |
| single | Single | 1 | none | none | Theme forces canonical → `/collections/all` |
| sample-pack | Sample Pack | **0** | none | 22-char desc | Empty collection still in sitemap |
| race-day-essentials | Race Day Essentials | 3 | none | none | — |
| body-care-collection | Body Care Collection | 7 | none | none | — |

`layout/theme.liquid` also forces canonical `/collections/all` when `handle contains 'frontpage'`. That collapses three named collections plus the homepage-adjacent `frontpage` collection onto one URL.

Blog template override: **every** `template == 'blog'` page gets `<title>Blogs \| 1Hour After</title>` and a shared meta description. WebFetch of `/blogs/test` confirmed that title. `handle contains 'test'` also emits `noindex`.

### Pages

| Handle | SEO title | SEO desc | Notes |
|---|---|---|---|
| about-us | yes | yes | Fine vs other pages |
| lab-1hr | yes (trailing space) | yes (82 chars, thin) | |
| refund-policy | "Refund Policy" only | **missing** | |
| privacy-policy | yes | yes | |
| terms-of-service-1hr-a | yes | yes | |
| sample-request | **missing** | **missing** | WebFetch: marketing H2, no unique title |
| contact-us | "Contact Us \| 1 Hour After" | yes | Brand spelling drift |
| affiliate | yes | yes | |
| affiliate-signup | yes | yes | Redirect loop with `/affiliate-signup` (see below) |
| athletic-affiliate-program-in-usa-and-canada | 89 chars (overlong, leading space) | yes | |

### Articles

- 38 published on `news`. 12 published-or-not missing `title_tag`; 11 missing `description_tag`.
- Unpublished leftovers still listed in theme `noindex` rules: `sample-blog-heading*`, `ultricies-aliquam-neque-…`, `the-importance-of-catching-z-s`, `sample-page-6`.
- `/blogs/test` + article `test/test` unpublished but the **blog index is live**.

## Redirects

39 Admin `urlRedirect` rows. Several **chains** (old Repair Remedy handles hop through retired handles before the live PDP). WebFetch of `/products/repair-remedy-duo` did land on the live adaptogen shampoo PDP in this session — so at least that chain currently resolves. Still fragile: Shopify redirect behavior across hops is not something to rely on.

Loop:

- `/pages/affiliate-signup` → `/affiliate-signup`
- `/affiliate-signup` → `https://1hourafter.com/pages/affiliate-signup`

Stale hop examples still in Admin (intermediate target is not a current product handle): `/products/1hour-after-cooling-body-wash`, `/products/adaptogen-shampo`, `/products/the-complete-active-recovery-system`.

## Storefront sample (titles, robots, schema, AEO)

### Crawl / indexation

| URL | Method | Result |
|---|---|---|
| `/robots.txt` | curl 200 | Shopify defaults + shop id `56106188973`; **GPTBot / ChatGPT-User / OAI-SearchBot Allow: /**; sitemap `https://1hourafter.com/sitemap.xml` |
| `/sitemap.xml` + children | curl 200 | See counts above. `sitemap_agentic_discovery.xml` points at `/agents.md` |
| `/agents.md` | curl 200 | Shopify UCP / Shop skill instructions (agentic commerce, not brand FAQ) |
| HTML storefront from this VM | urllib + Chrome UA | **HTTP 429** on `/`, collections, PDPs, blogs after robots/sitemaps succeeded |
| Same HTML URLs | WebFetch | 200 markdown (titles/H1/body). Canonical/robots meta not visible in the markdown conversion |
| Theme Liquid | `site/theme/layout/theme.liquid` | Source of truth for `noindex` handle list + forced collection canonicals |

Re-measure HTML `robots` / `canonical` / `ld+json` from a non-429 network on the next loop. Until then, treat Liquid + Admin SEO fields + WebFetch titles as the baseline.

Theme `noindex` handles (from Liquid, not applied in this PR): `1hour-after-cooling-body-gel`, any handle containing `test`, tag `noindex`, leftover lorem/sample blog handles. `handle contains 'test'` is a blunt rule — it will noindex `/blogs/test` **and** any future handle with `test` in it.

### Sampled page titles / answer-readiness (WebFetch 2026-10-06)

| URL | Observed title / H1 | Answer-ready? | Schema expectation from theme |
|---|---|---|---|
| `/` | `1Hour After: Post-Workout Body Care for Daily Athletes` | Hero copy, not a Q→A block. Stale 0562 CDN + `shopifypreview.com` still in homepage HTML per theme audit | Organization + WebSite/SearchAction |
| `/collections/all` | markdown title `Products` | Product grid; no collection SEO | none special |
| `/collections/frontpage` | `ActiveCollection` | Same grid; **bad title** | Forced canonical → `/collections/all` |
| `/products/anti-chafe-balm` | SEO title matches Admin | Benefits + how-to near top; FAQ JSON-LD expected | Product + FAQPage |
| `/products/muscle-recovery-balm` | SEO title matches Admin | Same; FAQ expected | Product + FAQPage |
| `/products/post-workout-hair-care-kit` | **Muscle Recovery Balm** (wrong) | Thin duplicate body; empty `FAQ's` heading | Product only (id not in `faq-schema.liquid`) |
| `/products/1hr-adaptogen-shampoo` | distinct SEO title, **same H1** as OH100 | Short body; empty FAQ heading | Product only; unused FAQ snippet exists |
| `/products/lab-ss-001` | LAB/SS-001 | Thin lab teaser; empty FAQ | Product only |
| `/blogs/test` | **Blogs \| 1Hour After** | Empty | `noindex` via handle `test` |
| `/pages/sample-request` | Sample Request | Form page; no SEO metafields | — |
| `/blogs/news/how-to-prevent-chafing-when-running` | article title (search + sitemap) | Answer-first guide; good AEO candidate | Article / OG from Debut |

Homepage race-day block still says **ANTI CHEF BALM** and a `1hours` preview URL in `settings_data.json` (theme audit). Not re-fixed here.

### Structured data vs live product ids

[`../schema-state.md`](../schema-state.md) is still correct for *what the export emits*. Coverage vs **today’s ACTIVE catalog**:

| ACTIVE product id | FAQ snippet wired? |
|---|---|
| 6668255461549 shampoo | yes |
| 7286045999277 `1hr-adaptogen-shampoo` | **no** (orphan snippet in repo) |
| 7878684934317 anti-chafe | yes |
| 6668255723693 body wash | yes |
| 7389948575917 sampler | yes |
| 6670616264877 lab | no |
| 7299791126701 hair-care-kit (titled Muscle Recovery Balm) | no |
| 7878684901549 muscle recovery balm | yes |
| 7162656456877 recovery gel | no |
| 6668255920301 magnesium lotion | yes |
| 7299805315245 body-care-set (titled lotion) | no |
| 7145590358189 conditioner | yes |
| 7162482262189 marathon pack | yes |
| 8140422578349 race pack | yes |

No BreadcrumbList. Organization `sameAs` still includes sample Shopify Instagram/Tumblr from theme settings.

FAQ JSON-LD copy includes unapproved medical-adjacent claims (eczema, rosacea, chronic muscle pain, etc.). [`../../compliance/claims.md`](../../compliance/claims.md) is empty Class C — **do not treat those answers as approved**. Do not copy them into [`../faq-corpus.md`](../faq-corpus.md) until voice + claims exist.

### Knowledge-base metaobjects / AEO storefront

Shopify `shopify--knowledge-base-fact` entries (return policy, gift cards, owned brand name “1Hour After”, …) are **unpublished**. `/agents.md` + UCP are live. Answer engines that use Shop/UCP may see a cleaner merchant profile than Google sees from the Debut HTML.

## Query → page map (proposed; not written to `target-queries.md`)

| Query | Best live URL | Status |
|---|---|---|
| How to prevent chafing when running | `/blogs/news/how-to-prevent-chafing-when-running` **and** `/products/anti-chafe-balm` | Article is answer-first; PDP has FAQ. Two URLs compete — pick one owner later |
| Anti chafe balm for endurance athletes | `/products/anti-chafe-balm` | Strong PDP; sampled sold out |
| Magnesium lotion for athletes / muscle recovery | `/products/muscle-recovery-magnesium-body-lotion` | **Competing URL** `/products/post-workout-body-care-set` uses the same title |
| Post-workout protein shampoo | `/products/adaptogen-protein-strengthening-shampoo` | **Competing URL** `/products/1hr-adaptogen-shampoo` |
| Muscle recovery balm / muscle rub | `/products/muscle-recovery-balm` | **Competing URL** `/products/post-workout-hair-care-kit` |
| What is 1Hour After? | `/` or `/pages/about-us` | Homepage is not Q&A; About has SEO |
| Athletic affiliate program | three pages (`affiliate`, `affiliate-signup`, `athletic-affiliate-program-in-usa-and-canada`) | Diluted |
| Lab / new formulas | `/pages/lab-1hr` vs `/products/lab-ss-001` | Thin product should not own this |

[`../target-queries.md`](../target-queries.md) and [`../faq-corpus.md`](../faq-corpus.md) stay empty until a human sets strategy / voice. This table is analysis-only.

## Sampled visibility (2026-10-06, en-US, WebSearch — not a rank promise)

| query | engine | locale | date | result |
|---|---|---|---|---|
| site:1hourafter.com post-workout body care | Google via WebSearch | en-US | 2026-10-06 | Homepage, cooling body wash, recovery gel, **and** the mismatched `/products/post-workout-body-care-set` titled as the lotion |
| 1Hour After anti chafe balm athletes | Google via WebSearch | en-US | 2026-10-06 | `/products/anti-chafe-balm` first-party URL present among returned links |
| how to prevent chafing when running 1Hour After | Google via WebSearch | en-US | 2026-10-06 | `/blogs/news/how-to-prevent-chafing-when-running` present; also Healthline / other sites |
| 1HR-A magnesium body lotion for athletes | Google via WebSearch | en-US | 2026-10-06 | Canonical lotion URL **and** duplicate `/products/post-workout-body-care-set` both returned |

## Ranked gaps (impact heuristic)

Critical technical first, then intent/answer, then schema, then metadata. **No live writes in this PR.**

1. **Critical — duplicate live PDPs / wrong titles.** Three collisions: two shampoos with the same title; two “Muscle Recovery Balm” titles (one is handle `post-workout-hair-care-kit`); two “REFUELING MAGNESIUM BODY LOTION” titles (one is handle `post-workout-body-care-set`). Search already returns the wrong URL for the lotion query. Unpublish, 301, or retitle+rewrite — human picks. Highest leverage for both SEO and AEO.
2. **Critical — collection indexation.** Zero collection SEO; `frontpage` title is `ActiveCollection`; `featured-collection` / `single` / `frontpage` canonicalized to `/collections/all`; empty `sample-pack` still in the sitemap. Theme `noindex` list does not cover these.
3. **High — missing SEO fields on live URLs.** Sampler missing title; hair-care-kit and body-care-set missing title **and** description; lab missing description; all six collections missing both; `sample-request` and refund-policy description missing. Blog index title is hardcoded and non-unique.
4. **High — FAQ / AEO coverage holes.** FAQPage is hardcoded to nine product ids. Duplicate/thin PDPs show an empty FAQ heading and emit no FAQ JSON-LD. Orphan snippet for `1hr-adaptogen-shampoo` is never rendered. Unpublished knowledge-base facts do not fill the gap. Claims in existing FAQ JSON-LD are not Class C–approved.
5. **Medium-high — crawl clutter.** Live `lab-ss-001` (SKU `2`) in the product sitemap; `/blogs/test`; 21 drafts including 13 Repair Remedy clones; 39 redirects with loops/chains; stale **0562 / 1hours** CDN and preview_key on the homepage; `handle contains 'test'` noindex sledgehammer; Organization `sameAs` still Shopify’s Instagram.

Lower but real: short SEO titles on marathon packs; vendors/types leftover from migrations; primary market handle `uni` with **US Retail disabled**; MLVeda default CAD (theme audit) vs shop currency USD; several core PDPs sampled **sold out** (availability in Product/Offer schema).

## Follow-up Shopify writes (later task — do not do here)

A later TASK should check out a **new** branch from the integration branch after this PR lands, then apply **one** highest-leverage fix and re-run this same benchmark:

1. Human-approve the roster. Unpublish or 301 the three duplicate ACTIVE PDPs (`1hr-adaptogen-shampoo`, `post-workout-hair-care-kit`, `post-workout-body-care-set`) and `lab-ss-001` unless Lab is meant to be a public SKU.
2. Remove Liquid canonical overrides for `frontpage` / `featured-collection` / `single`. Add collection SEO titles/descriptions. Unpublish empty `sample-pack`.
3. Fill missing `seo.title` / `seo.description` (and page `global.title_tag` / `description_tag`) on remaining live URLs. Drop the global “Blogs | 1Hour After” title override.
4. Wire or delete FAQ snippets so every **kept** PDP either has FAQPage + visible Q&A or has no empty FAQ heading. Do not ship claims until Class C [`../../compliance/claims.md`](../../compliance/claims.md) exists.
5. Clean redirects (collapse chains, break the affiliate loop), remove 0562 CDN + preview_key HTML, narrow `noindex` from `contains 'test'` to exact leftover handles, unpublish `/blogs/test`.

Do **not** `theme push` until that task says so. Do **not** invent SKUs for blank Admin SKU fields.

## Deliberately not done

- No Admin mutation, no theme push, no product/page/redirect edits.
- No rewrite of Class C (`brand-voice`, `icp`, `business-identity`, `content-style-guide`, `compliance/claims`).
- Canonical [`../products.md`](../products.md) Active table left empty; proposed table is labeled and points here.
- No Furgenics / For & Against content.
- No COGS/margins. Public storefront prices were observed in WebFetch and omitted from the roster.
- SANDBOX theme not pulled. `site/theme/` not modified.

## How a later session should behave

Re-run the **same** `priority_pages` + `target_queries` + locale. Prove Admin with the verification commands above (length + `shpa` prefix + shop domain only). Fetch HTML canonicals/robots from a network that is not 429-limited. Fix gap #1 only, then re-sample. Never invent `dsp_*` or write to Shopify from an audit TASK.
