# Session summary, October 6–20 — 1HR-After

> Filed: 2026-10-20T15:30:00Z · Kind: query
> Related: [`2026-10-19-publish-affiliate.md`](2026-10-19-publish-affiliate.md), [`../../sessions.md`](../../sessions.md)

One summary of the storefront work on 1hourafter.com in this agent run. Each slice has its own write-up, linked below. TASK-3481.

## Where the site is now

- The live theme is **1HR-A QA preview** `#189469851821`. It was published on 2026-10-19. The previous live theme `#122661372077` is unpublished and is the rollback.
- Theme files are pushed with the Shopify CLI, file by file. A merge on GitHub does not deploy anything. The open PRs record work that is already live.
- Product copy, page title tags, redirects, and blog posts were written through the Admin API. They are live and not in git, except where a slice archived the before-copy under `docs/sources/audits/`.

## What shipped

| Dates | PRs | Work | Write-up |
| --- | --- | --- | --- |
| Oct 6 | #12–#14 | Catalog and theme audit, duplicate product pages drafted and redirected, collection SEO, gel archived, Organization schema, affiliate canonical | [`2026-10-06-seo-aeo-hygiene-org.md`](2026-10-06-seo-aeo-hygiene-org.md) |
| Oct 7 | #15–#16 | SEO action plan, two 301s, Race Day Kit rewrite, Body Glide comparison and anti-chafe roundup posts | [`2026-10-07-seo-aeo-action-plan.md`](2026-10-07-seo-aeo-action-plan.md), [`2026-10-07-body-glide-comparison.md`](2026-10-07-body-glide-comparison.md) |
| Oct 14 | #21–#26 | Phased Oct 8 fixes, visual fixes, page-load review, Add to Cart alignment, first paint, taglines, Race Day buttons, blog tiles | [`2026-10-14-phased-oct8-reship.md`](2026-10-14-phased-oct8-reship.md), [`2026-10-14-tagline-buttons-blog.md`](2026-10-14-tagline-buttons-blog.md) |
| Oct 15 | #27 | Try Free Sample button parked while the sampler is draft | [`2026-10-15-hide-try-sample.md`](2026-10-15-hide-try-sample.md) |
| Oct 16 | #28 | Six-product homepage grid, card reviews and pack contents, product page bullets and mobile Add to Cart | [`2026-10-16-storefront-feedback.md`](2026-10-16-storefront-feedback.md) |
| Oct 16 | #29–#32 | Claims copy in four phases on all eight products, FAQs, and five homepage sentences | [`2026-10-16-claims-phase4.md`](2026-10-16-claims-phase4.md) |
| Oct 16 | #33–#35 | Add to Cart overlap, loading ring for the grey first paint, Subscribe and Save in the product form | [`2026-10-16-subscribe-embed.md`](2026-10-16-subscribe-embed.md) |
| Oct 19 | #36–#37 | Marathon Pack and Race Day Kit tiles are the same square as the others, with an 8px gap | [`2026-10-19-tile-separation.md`](2026-10-19-tile-separation.md) |
| Oct 19 | #38 | FAQ contrast and toggle, Instagram new tab, star icons, card type, one email signup bar | [`2026-10-19-site-qa-fixes.md`](2026-10-19-site-qa-fixes.md) |
| Oct 19 | #39 | QA theme published, balm twist-up and shower lines, affiliate contact form | [`2026-10-19-publish-affiliate.md`](2026-10-19-publish-affiliate.md) |

## PRs to merge

Four draft PRs are open, plus this summary. They are stacked, so merge them in this order. Each one targets the branch of the PR before it.

1. [#36](https://github.com/petralabx/1hr-after/pull/36) Marathon Pack tile → `main`
2. [#37](https://github.com/petralabx/1hr-after/pull/37) Tile separation → after #36
3. [#38](https://github.com/petralabx/1hr-after/pull/38) Site QA fixes → after #37
4. [#39](https://github.com/petralabx/1hr-after/pull/39) Publish and affiliate form → after #38
5. [#40](https://github.com/petralabx/1hr-after/pull/40) Session summary → after #39

After each merge, set the next PR's base to `main` if GitHub does not do it. All five touch `docs/sessions.md` and the wiki logs, so merging out of order will cause conflicts in those files.

## Still open

- Claims Phase 5, the consolidated check, has not started.
- News article titles are waiting on a decision.
- The `/collections/all` description still names the athletic sampler pack. The sampler product stays draft.
- The affiliate form emails the shop. It does not create a tagged customer.
- Rotate the Judge.me token that used to sit in the product template.

## Rules that still apply

Do not push `config/settings_data.json` as a whole. Do not call `1hours.myshopify.com`. Do not add `format: 'webp'` on `img_url: '1x1'`. Do not activate US Retail, reinstall Mlveda, or undraft the Athletic Sampler. Send the SEO title in the same `productUpdate` as the description.
