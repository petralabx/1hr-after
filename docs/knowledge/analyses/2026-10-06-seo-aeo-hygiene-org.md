# SEO/AEO hygiene + Organization ship — 1HR-After

> Filed: 2026-10-06T21:30:00Z · Kind: ship
> Related: [`2026-10-06-seo-aeo-live-fixes.md`](2026-10-06-seo-aeo-live-fixes.md), [`../products.md`](../products.md), [`../schema-state.md`](../schema-state.md)

Operator answers on the post-ship review, applied live on `1hourafter.myshopify.com` (TASK-2459). FAQ claims were **not** rewritten (operator: a study exists). Gel was archived, not deleted. News blog kept. **CIP lands; this agent cannot merge.**

Shop: `1hourafter.myshopify.com` only.

## Operator answers (and what shipped)

### Recovery Body Gel — archived

Real product, not being made for about a year. Set **DRAFT** (not deleted) + 301 `/products/recovery-body-gel` → `/products/muscle-recovery-balm`. Gone from the product sitemap. Re-publish later when it is in stock.

### 1. Keep the News blog

`/blogs/news` stays. That is the SEO blog (chafing article already appears in search). The leftover was `/blogs/test` (title `test`, one unpublished article). **Deleted the test blog**; existing redirect `/blogs/test` → `/blogs/news` now fires. Do not delete News.

### 2. Google recrawl (operator)

Paste these into Search Console → URL inspection → Request indexing:

- `https://1hourafter.com/products/post-workout-body-care-set`
- `https://1hourafter.com/products/post-workout-hair-care-kit`
- `https://1hourafter.com/products/1hr-adaptogen-shampoo`
- `https://1hourafter.com/products/lab-ss-001`
- `https://1hourafter.com/products/recovery-body-gel`
- `https://1hourafter.com/pages/affiliate`
- `https://1hourafter.com/pages/athletic-affiliate-program-in-usa-and-canada`
- `https://1hourafter.com/blogs/test`

This session cannot sign in to Search Console.

### 3. Affiliate canonical = `/pages/affiliate-signup`

Kept that URL because it is the page **with the Klaviyo signup form** and 20% commission copy. `/pages/affiliate` was an identical duplicate. `/pages/athletic-affiliate-program-in-usa-and-canada` is a long recruiting pitch with follower tiers (25–40%) that **contradict** the 20% form page, plus an 89-character title. Unpublished the two extras and 301'd them to signup. Title on the keeper: `Join the 1Hour After Affiliate Program | 1HR-After`. H1 added on the form template.

### 4. Organization + Instagram (theme)

Live JSON-LD: `"name": "1Hour After"`, `"sameAs": ["https://www.instagram.com/1hourafter/"]`. Shopify sample Instagram/Tumblr removed. Empty social slots no longer emit blank strings. Facebook/YouTube left empty (not invented). Pushed to live theme `#122661372077`.

### 5. Knowledge-base facts

Reviewed Shopify Shop facts. **Published** only rows that match the live site and do not invent policies:

| Fact | Published? |
|---|---|
| Description (time-based body care, daily athletes, HYROX/Ironman) | yes (worded off the homepage/About, no new medical claims) |
| Target audience | yes |
| Brand values | yes, **without** “cellular health” (that phrase is stronger than the study-backed recovery copy) |
| Brand aesthetic | yes |
| Owned brand name `1Hour After` | yes |
| Is second-hand = false | yes |
| Start year, gift cards/wrap/receipts, sustainability, animal-testing policy, main brands | **no** — empty or unverified. Do not guess a founding year or gift-card policy |

### 6. Homepage / About H1s

- Homepage hero H1: **1Hour After is post-workout body care for daily athletes** (still followed by the existing functional/race-day copy).
- About H1: **1HOUR AFTER IS TIME-BASED BODYCARE FOR THE HOUR AFTER TRAINING** (replaces “WELCOME TO A NEW ERA…”). Body copy under it was not rewritten.

### 7. Catalog hygiene

Vendor on live SKUs → `1Hour After`. Types: Shampoo, Conditioner, Body Wash, Magnesium Lotion, Recovery Balm, Anti-Chafe Balm, Sampler Pack, Marathon Pack, Race Pack. Display titles title-cased (CSS still uppercases on PDPs). Sampler pipe junk removed from the Admin title. Redirect chains collapsed to one hop. **SKUs not invented.** MLVeda / Repair Remedy drafts not deleted. FAQ JSON-LD not touched.

## Live checks (2026-10-06)

| URL | Result |
|---|---|
| `/products/recovery-body-gel` | 301 → muscle-recovery-balm; not in product sitemap |
| `/pages/affiliate` | 301 → `/pages/affiliate-signup` |
| `/pages/athletic-affiliate-program-in-usa-and-canada` | 301 → signup |
| `/blogs/test` | 301 → `/blogs/news` |
| `/blogs/news` | 200, still in sitemap |
| Homepage Organization | name `1Hour After`, Instagram only |

## Rollback

Re-set gel to ACTIVE and delete its redirect. Re-publish the two affiliate pages and delete those redirects. Restore the test blog from Shopify if a backup exists (otherwise recreate). `shopify theme push` `site/theme` from `main` / PR #12. Revert vendor/type/title productUpdates. Set knowledge-base `published` back to false.
