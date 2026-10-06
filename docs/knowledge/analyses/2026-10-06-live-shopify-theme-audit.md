# Live Shopify theme audit — 1HR-After

> Filed: 2026-10-06T18:25:00Z · Kind: audit
> Related: [`../../wiki-schema.md`](../../wiki-schema.md), [`../schema-state.md`](../schema-state.md), [`../../channels/meta-ads.md`](../../channels/meta-ads.md), [`../../../data/config.json`](../../../data/config.json)

Read-only pull of the **published** theme. Shopify was not written. SANDBOX was not pulled. Furgenics and For & Against files were not copied.

## How it was pulled

| Item | Evidence |
|---|---|
| Env `SHOPIFY_FLAG_STORE` | Set to `1hours.myshopify.com` |
| Theme Access password | Present as `SHOPIFY_CLI_THEME_TOKEN` (Theme Access app password, 39 chars). Never echoed, never committed |
| CLI | `@shopify/cli` 4.8.5, user npm prefix |
| What 401s | Theme Access against `1hours.myshopify.com` (vanity / export-source shop) |
| What works | Theme Access against `1hourafter.myshopify.com` (`Shopify.shop` on the live storefront) |
| Command | `SHOPIFY_FLAG_FORCE=1 shopify theme pull --live --store 1hourafter.myshopify.com --password "$SHOPIFY_CLI_THEME_TOKEN" --path site/theme` |
| Result | Theme export  1hours-myshopify-com-debut  03may… (`#122661372077`), role `main` |

Themes on the store (Admin via Theme Access proxy, 2026-10-06):

| Id | Name | Role |
|---|---|---|
| 122661372077 | Theme export  1hours-myshopify-com-debut  03may… | **main** (pulled) |
| 121745014957 | Debut | unpublished |
| 131292987565 / 131637870765 / 141020037293 | Copies of the export | unpublished |
| 143449981101 | SANDBOX  1hours-myshopify-com-debu… | unpublished — **not pulled** |
| 143450603693 | Refresh | unpublished |

Admin `updated_at` on the live theme is **2026-09-14T18:30:38-04:00**, not a later October save. Treat the Admin timestamp as source of truth.

Two Shopify file CDNs appear in the export:

- `cdn.shopify.com/s/files/1/0561/0618/8973/` → shop id **56106188973** (`1hourafter`, matches `/56106188973/checkouts` in `robots.txt`)
- `cdn.shopify.com/s/files/1/0562/2179/4479/` → shop id **56221794479** (the `1hours` export source; leftover images, a header logo, and a `shopifypreview.com` link)

The live theme is an old Debut export from `1hours` that now runs on `1hourafter`. Hardcoded 0562 URLs will 404 if those files were never copied onto the destination shop.

## Theme identity

- **Family:** Shopify Debut 17.12.0 (`config/settings_schema.json`). Vintage Liquid templates only. Zero `templates/*.json` Online Store 2.0 files.
- **Published name:** Theme export  1hours-myshopify-com-debut  03may…
- **Storefront title:** `1Hour After: Post-Workout Body Care for Daily Athletes`
- **Public origin:** `https://1hourafter.com`
- **Inventory in this pull:** 4 layouts, 39 sections, 95 snippets, 38 Liquid templates, 65 assets, 33 locales, ~8.2 MB. Backup leftovers: `layout/SWYM_BACKUP_theme.liquid`, `sections/header-hulkapps-backup.liquid`, `sections/cart-template-hulkapps-backup.liquid`, `templates/cart.preorder-now-cart-hulkapps-backup.liquid`.

Brand naming on the storefront is inconsistent (`1Hour After`, `1HR-A`, `1hour-after`, `1Hour-After`). Class C [`business-identity.md`](../business-identity.md) is still empty, so this audit does **not** pick a canonical spelling.

## Layout

`templates/index.liquid` is only `{{ content_for_index }}`. Enabled homepage sections (from `config/settings_data.json` `content_for_index`, skipping `disabled: true`):

1. Custom HTML / image blocks (`custom-content`, several)
2. A collection section
3. Feature-row “WHY 1HOUR AFTER?” (Hyrox / Ironman / marathon copy)
4. `custom-content2` marquee (“the clock is ticking”)
5. `hero-2`

Debut stock sections on the index (`hero-1`, `feature-columns`, `featured-blog`, `quotes`, `image-bar`, plus extra feature-rows) are **disabled**. The live homepage is mostly custom HTML in theme settings, not OS 2.0 sections.

Global layout (`layout/theme.liquid`):

- Head: Bing `msvalidate.01`, GTM `GTM-M4LGTWV`, Ordersify BIS, Debut CSS variables, `theme.css` + `onehour.css`, jQuery 3.3.1, Slick
- `{{ content_for_header }}` then Booster currency, MLVeda currency globals, Swift, Hulk preorder
- Body: GTM noscript, cart popups, `header`, `{{ content_for_layout }}`, `footer`
- Footer scripts: MLVeda, Subscribe-it, back-in-stock, Swym, Preorder Now, Globo preorder, Smile, Booster page-speed JS from **another shop’s CDN** (`0194/1736/6592`)

Bugs / drift in the layout file:

- `{% if page.title != 'Lab' or page.title != 'Sample Request' %}` is always true (`or` of two inequalities).
- Many `noindex` handle rules for leftover sample blog/product handles (`ultricies-aliquam-neque-…`, `sample-blog-heading*`).
- Hardcoded `body,html{background-color: #C7C4C4;}` in the critical CSS — raw hex, not a `--1hr-` token.
- Header logos mix a 0562 “LONG BLACK” file with a 0561 `1hour-logo.png`.

## Hardcoded secrets and credentials

No Theme Access password, Admin token, PEM, or `sk_live` is in the pulled files. App snippets read **shop metafields at render time** (Smile `api_secret`, Ordersify popup JSON). Those are not file secrets, but Smile’s initializer will emit a customer HMAC digest into HTML for logged-in visitors — that is the app’s design, not a committed secret.

Findings that should be cleaned in a later theme task (not done here; this PR does not edit Shopify):

- `config/settings_data.json` homepage HTML includes a `*.shopifypreview.com/products_preview?preview_key=…` URL for shop `56221794479`. That is a stale preview grant. Remove the HTML; rotate the preview if it still works.
- Social settings are still Debut samples: `http://instagram.com/shopify` and `http://shopify.tumblr.com`. Facebook / Twitter / Pinterest / YouTube are blank. Organization `sameAs` on the live site will advertise Shopify’s Instagram, not 1HR-After.
- Google Maps section `api_key` is **not** filled in settings (schema exists; no key stored).
- `msvalidate.01` Bing owner-verification hash is public by design.
- Commented Universal Analytics `UA-48958097-8` in `snippets/home-page-animation.liquid` (different from the UA id in GTM).

Do not treat GTM or pixel ids as passwords. They are public once the container loads.

## Raw hex versus `--1hr-` tokens

[`docs/design-system/tokens.css`](../../design-system/tokens.css) defines `--1hr-ink`, `--1hr-paper`, `--1hr-accent`, `--1hr-muted`, `--1hr-grid` inside `.brand-1hr-after`.

**Zero `--1hr-` references exist in `site/theme/`.** The live theme cannot opt into the brand boundary.

What it uses instead:

- Debut CSS custom properties (`--color-text`, `--color-btn-primary`, …) from `snippets/css-variables.liquid`, driven by theme editor colors.
- `current` settings only override a few colors (`color_sale_text: #ffffff`, MLVeda `#FFFFFF`). Most Debut color knobs fall through to the schema defaults / unused presets (`#DA2F0C` button, `#162950` text in the Default preset).
- Large raw-hex sheets in `assets/onehour.css`, `assets/theme.css`, app snippets (MLVeda, Preorder Now, Ordersify, Subscribe-it), and SVG `fill="#…"`.
- Critical CSS hex `#C7C4C4` on `body,html` — not `--1hr-paper` (`#f5f2eb`) and not `--1hr-ink`.

A later “apply brand tokens to the storefront” pass is a dedicated design-system + theme task. It is blocked until someone maps `--1hr-*` onto Debut’s `--color-*` (or replaces Debut). Do not sprinkle hex into new components; this export already does.

## Apps, pixels, and tags

**Theme Liquid / app embeds (enabled in `settings_data.json` `blocks`):**

| App | Where |
|---|---|
| Klaviyo Email Marketing & SMS | theme app embed |
| Judge.me Reviews | theme app embed |
| EA Spin Wheel Email Popups | theme app embed |
| Ecomsend Popups | theme app embed |
| Addly Bundle Upsell | theme app embed |
| MinMaxify Order Limits | theme app embed |
| GTM | hardcoded `GTM-M4LGTWV` in `layout/theme.liquid` |
| Ordersify Back in Stock | `ordersify-bis` |
| Swym (wishlist) | `swymSnippet` + backup layout |
| Smile.io loyalty | `smile-initializer` |
| Hulk + Preorder Now + Globo preorder | three overlapping preorder stacks |
| MLVeda Auto Currency Switcher | default currency **CAD** |
| Subscribe-it | helper snippet |
| Booster (currency + page-speed) | third-party shop CDN |
| BSS subscriptions | price/portal snippets |
| Zooomy Back in Stock | snippet present |

**Live homepage HTML (2026-10-06), plus public GTM container `gtm.js?id=GTM-M4LGTWV`:**

| Tag | Id | In theme files? |
|---|---|---|
| GTM | `GTM-M4LGTWV` | Yes, Liquid |
| Meta Pixel (fbq init) | `1035858581719070` | **No** — loaded via GTM |
| GTM `vtp_pixelId` | `663035363114691` | No — confirm vendor before using |
| Google Ads | `AW-10990117115` | No — GTM |
| Universal Analytics | `UA-227392273-1` | No — GTM (legacy) |
| TikTok / Snap / Pinterest tags | none found | — |
| Shopify web pixels | present in live HTML (`web-pixels` / customer events) | Not in this Liquid export |

There is **no** `fbq` snippet in Liquid. Meta ads measurement today depends on GTM (and any Shopify customer-events pixel an admin added, which `theme pull` does not export). `data/config.json` records `1035858581719070` as observed, not as an approved ad-account pixel. Instagram / Page / ad-account ids are still unknown.

## Structured data (what this export actually emits)

See [`schema-state.md`](../schema-state.md). Header emits Organization + (on index) WebSite/SearchAction. Product JSON-LD is on `templates/product.liquid` and variants. FAQPage JSON-LD is product-id gated in `sections/faq-schema.liquid`. No BreadcrumbList. Organization `sameAs` is poisoned by the Shopify sample social URLs.

FAQ snippets name live product *ids* (muscle recovery balm, anti-chafe, sampler, conditioner, body wash, adaptogen shampoo, magnesium lotion, marathon packs). Those ids are **observations from this theme**, not a canonical roster. [`products.md`](../products.md) stays empty until a human fills it. Claims in the FAQ JSON-LD are not approved in [`../../compliance/claims.md`](../../compliance/claims.md).

## Blockers for a later content or Meta ads pass

1. **Class C pages are empty.** Voice, ICP, identity, style, and claims are still TBD. Ads and PDP copy cannot be approved from this theme dump.
2. **No OS 2.0 JSON templates.** Content edits are Liquid + `settings_data.json` HTML blobs. A modern section/content model is a migration, not a copy tweak.
3. **Canonical URL and `noindex` spaghetti** in `theme.liquid` (sample handles, forced `/collections/all` canonicals). Dangerous for landing-page ads.
4. **Social / Open Graph defaults to Shopify’s Instagram.** Meta ads that scrape OG will not get a brand profile URL until settings are fixed.
5. **Pixel is only in GTM**, not in theme. Confirm `1035858581719070` in Events Manager, CAPI, and Shopify customer events before spend. Ad account, IG, and Page ids are still null.
6. **Two preorder apps plus Hulk plus leftover backup templates** — cart/PDP behavior is not a clean landing surface.
7. **Currency switcher default CAD** with a USD brand storefront — landing-page price mismatch risk.
8. **Hardcoded 0562 CDN + preview_key HTML** — broken images and a stale preview grant on a race-day block (copy also says “ANTI CHEF BALM”).
9. **`--1hr-` tokens are unused.** Any new UI built from this theme will not match the brand boundary unless someone maps tokens first.
10. **Theme Access must use `1hourafter.myshopify.com`.** `SHOPIFY_FLAG_STORE=1hours.myshopify.com` is documented and set, but it cannot authenticate this password.

## Deliberately not done

- No `shopify theme push`, publish, or Admin edit.
- No rewrite of Class C pages.
- No rows added to [`products.md`](../products.md).
- No Furgenics / For & Against Liquid or copy.
- SANDBOX left on Shopify, unpublished.

## How a later session should behave

Read this page, [`schema-state.md`](../schema-state.md), and `data/config.json`. To pull again, use `--live` and `--store 1hourafter.myshopify.com`. Do not pull theme `143449981101`. Do not print `SHOPIFY_CLI_THEME_TOKEN`.
