# Session log

Append-only handoff for humans and agents. **Newest entry at the top.**

Read the latest one to three entries at the start of a working session. Append a short entry in the same PR that lands the work.

This is separate from:

- [`knowledge/log.md`](knowledge/log.md) — operational timeline
- [`knowledge/optimization-log.md`](knowledge/optimization-log.md) — SEO, AEO, and Meta optimization history
- [`knowledge/analyses/`](knowledge/analyses/) — deep write-ups

## Entry format

```markdown
## YYYY-MM-DD — short title

- **Who:** name / agent runtime
- **PR:** #N or n/a
- **Done:** 1–3 bullets
- **Next:** open follow-ups
- **Watch:** risks or fragile files
```

---

## 2026-10-06 — Pull live Shopify theme and audit (no Shopify write)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** draft on `cursor/shopify-live-theme-pull-2638` (TASK-2384)
- **Done:** Pulled published Debut `#122661372077` into `site/theme/`. Recorded `1hourafter.myshopify.com` in `data/config.json`. Filed the audit under `docs/knowledge/analyses/`. SANDBOX not pulled.
- **Next:** Human fills Class C pages. Confirm Meta pixel `1035858581719070` in Events Manager before ads. Map `--1hr-` tokens onto the theme in a later task. Do not `theme push`.
- **Watch:** Theme Access 401s on `1hours.myshopify.com`; use `1hourafter.myshopify.com`. Stale `shopifypreview.com` preview_key and 0562 CDN URLs live in `settings_data.json`. Do not copy Furgenics or For & Against.

## 2026-10-06 — Brand repo scaffold (Furgenics shape, Meta ads, Karpathy wiki)

- **Who:** Stephen Alton + Cursor cloud agent
- **PR:** open with this commit
- **Done:** Added the Karpathy wiki under `docs/knowledge/`, raw `docs/sources/`, content-draft templates, a site placeholder, `data/config.json`, and the Meta ads lane (`docs/channels/meta-ads.md`, `copy/ads/meta/`). Product facts, Shopify domain, and the Meta ad account are left blank.
- **Next:** A human fills Class C pages (`brand-voice.md`, `icp.md`, `business-identity.md`, `content-style-guide.md`, `compliance/claims.md`) and the Shopify plus Meta account rows in `data/config.json`. Then file real products in `docs/knowledge/products.md`.
- **Watch:** Do not paste Furgenics or For & Against copy, prices, or theme files into this repo. Do not invent SKUs or claims to make the empty tables look finished.
