# SEO/AEO live fixes — 1HR-After

> Filed: 2026-10-06T20:25:00Z · Kind: ship
> Related: [`2026-10-06-seo-aeo-catalog-audit.md`](2026-10-06-seo-aeo-catalog-audit.md), [`../products.md`](../products.md), [`../schema-state.md`](../schema-state.md)

Operator authorized live writes on `1hourafter.myshopify.com` (TASK-2388). This is the follow-up to the read-only audit. **CIP lands PRs; this agent cannot merge.** Class C pages were not rewritten. No SKUs invented. No Furgenics / For & Against. No COGS.

Shop: `1hourafter.myshopify.com` only. `1hours.myshopify.com` was not called.

## What shipped live

### 1. Duplicate PDPs (Admin `productUpdate` status DRAFT + URL redirects)

| Handle set DRAFT | Redirect target | WebFetch 2026-10-06 |
|---|---|---|
| `1hr-adaptogen-shampoo` | `/products/adaptogen-protein-strengthening-shampoo` | Lands on canonical shampoo ($30, full PDP) |
| `post-workout-hair-care-kit` | `/products/muscle-recovery-balm` | Lands on Muscle Recovery Balm with SEO title |
| `post-workout-body-care-set` | `/products/muscle-recovery-magnesium-body-lotion` | Redirect created |
| `lab-ss-001` | `/pages/lab-1hr` | Lands on Lab page |

`publishableUnpublish` was **denied** (`write_publications` is not on the app). DRAFT + `onlineStoreUrl: null` is what the storefront uses.

ACTIVE catalog is now 10 products (was 14).

### 2. Collection SEO + canonicals

Admin `collectionUpdate` SEO titles/descriptions on all six collections. `frontpage` title changed from `ActiveCollection` to **Post-Workout Body Care**. Live `/collections/frontpage` title is now `Post-Workout Body Care for Daily Athletes | 1HR-After`.

Theme: removed Liquid canonical overrides that forced `frontpage` / `featured-collection` / `single` → `/collections/all`. Pushed to live theme `#122661372077`.

`sample-pack` could not be unpublished (same `write_publications` gap). Theme now `noindex`s `handle == 'sample-pack'`.

### 3. Missing meta

Filled product `seo.title` / `seo.description` on sampler, marathon pack, race pack, recovery gel. Sampler live title is **Athletic Sampler Pack | 1HR-After**.

Page metafields `global.title_tag` / `description_tag` on `sample-request` and `refund-policy`.

Removed the global `<title>Blogs | 1Hour After</title>` override so blogs use `page_title`.

### 4. FAQ / AEO

Did **not** add new FAQ copy (Class C claims still empty). Visible empty FAQ heading on PDPs is now gated to the nine product ids that already have FAQ JSON-LD. Duplicate/thin PDPs were drafted, so they no longer compete.

### 5. Crawl clutter

- Stale `1hours` `shopifypreview.com` preview_key URLs on the homepage replaced with `/products/anti-chafe-balm` and `/products/muscle-recovery-balm`. Copy **ANTI CHEF** → **ANTI CHAFE**. Live homepage shows those buttons.
- 0562 CDN images in header, hero, lab, blog template, affiliate arrows, and `onehour.css` slicks replaced with 0561 files or inline SVG.
- `handle contains 'test'` narrowed to `handle == 'test'` (plus `sample-pack`).
- `/blogs/test` still exists as a live blog (Shopify will not 301 over an existing resource). Theme `noindex` is exact `handle == 'test'` (plus `sample-pack`). Affiliate loop deleted; `/affiliate-signup` → `/pages/affiliate-signup` (301).
- MLVeda “DO NOT DELETE” drafts and Repair Remedy clone drafts left as DRAFT (not deleted).

## Theme push

```text
shopify theme push --theme 122661372077 --store 1hourafter.myshopify.com --allow-live --nodelete
  --only layout/theme.liquid sections/header.liquid sections/hero.liquid
  sections/product-template.liquid sections/header-hulkapps-backup.liquid
  templates/page.lab.liquid templates/page.becomeaffiliate.liquid
  templates/product.becomeaffiliateprod.liquid templates/page.blog.liquid
  config/settings_data.json assets/onehour.css
```

Result: `role: live`, shop `1hourafter.myshopify.com`. Admin REST Asset API with the Theme Access password 401'd; CLI `--password` / `SHOPIFY_CLI_THEME_TOKEN` worked. Token not printed.

## Storefront re-sample (2026-10-06, after theme push)

| Check | Result |
|---|---|
| `/products/1hr-adaptogen-shampoo` | 301 → `/products/adaptogen-protein-strengthening-shampoo` |
| `/products/post-workout-hair-care-kit` | 301 → `/products/muscle-recovery-balm` |
| `/products/post-workout-body-care-set` | 301 → `/products/muscle-recovery-magnesium-body-lotion` |
| `/products/lab-ss-001` | 301 → `/pages/lab-1hr` |
| `/affiliate-signup` | 301 → `/pages/affiliate-signup` |
| `/collections/frontpage` title | `Post-Workout Body Care for Daily Athletes \| 1HR-After` |
| `/products/free-1hour-after-athletic-sampler-pack` title | `Athletic Sampler Pack \| 1HR-After` |
| Homepage | `SHOP ANTI CHAFE BALM` |
| `/collections/sample-pack` | `robots: noindex` |
| `/blogs/test` | 200, title `test`, `robots: noindex` (not a 301) |

## Left for a later task

- `write_publications` so `sample-pack` can leave the Online Store / sitemap.
- Organization `sameAs` still sample Shopify Instagram (theme settings).
- FAQ JSON-LD claims still unapproved Class C.
- Canonical Active table in [`../products.md`](../products.md) still empty pending human Class B approval.
- Agents cannot merge; CIP lands.

## Rollback (Shopify)

Re-set the four handles to ACTIVE, delete the new urlRedirects, revert collection titles/SEO, revert page metafields, `shopify theme push` the previous `site/theme` from `main` / PR #10. Or restore theme `#122661372077` from Shopify admin revision if one exists.
