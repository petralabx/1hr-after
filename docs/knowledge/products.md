# Products

> **Owner:** Class B (agent proposes, human approves semantic changes)
> **Status:** Canonical tables still empty. A **proposed** snapshot from live Admin (2026-10-06) is below; it is not approved.
> **Last updated:** 2026-10-07

Canonical product list. Shopify, Amazon, page drafts, and Meta catalog ads sync from this table. If a surface disagrees, fix this page first after checking the live catalog.

## Active

| SKU | Name | Size | Status | Handle / URL | Notes |
|---|---|---|---|---|---|
| — | — | — | — | — | — |

## Draft or discontinued

| SKU | Name | Status | Notes |
|---|---|---|---|
| — | — | — | — |

## Proposed from live Shopify catalog (2026-10-06) — not canonical

Class B. Copied from Admin GraphQL on `1hourafter.myshopify.com`. **Do not treat this table as the roster** until a human approves it. SKUs are observed, not invented; blank means Admin had no SKU. Full notes and duplicates: [`analyses/2026-10-06-seo-aeo-catalog-audit.md`](analyses/2026-10-06-seo-aeo-catalog-audit.md).

| Observed SKU | Admin title | Handle | Status | Human decision |
|---|---|---|---|---|
| OH100 | Adaptogen Protein Strengthening Shampoo | `adaptogen-protein-strengthening-shampoo` | ACTIVE | vendor/type cleaned 2026-10-06 |
| OH100-A | ADAPTOGEN PROTEIN STRENGTHENING SHAMPOO | `1hr-adaptogen-shampoo` | DRAFT (2026-10-06 live) | 301 → `adaptogen-protein-strengthening-shampoo` |
| OH800-KIT | Anti Chafe Glide Balm | `anti-chafe-balm` | ACTIVE | vendor/type cleaned 2026-10-06 |
| OH300-FBA | Cooling Menthol Body Wash | `cooling-menthol-body-wash` | ACTIVE | vendor/type cleaned 2026-10-06 |
| OHSP50 | Free 1Hour-After Athletic Sampler Pack | `free-1hour-after-athletic-sampler-pack` | ACTIVE | pending (SKU also on a draft) |
| 2 | LAB/SS-001 | `lab-ss-001` | DRAFT (2026-10-06 live) | 301 → `/pages/lab-1hr` |
| OH701-KIT | Muscle Recovery Balm | `post-workout-hair-care-kit` | DRAFT (2026-10-06 live) | 301 → `muscle-recovery-balm` |
| — | Muscle Recovery Balm | `muscle-recovery-balm` | ACTIVE | pending (SKU blank in Admin) |
| — | Recovery Body Gel | `recovery-body-gel` | DRAFT (2026-10-06 archive) | Real SKU, not produced ~1 year; 301 → `muscle-recovery-balm`. Do not delete. |
| OH600-FBA | Refueling Magnesium Body Lotion | `muscle-recovery-magnesium-body-lotion` | ACTIVE | vendor/type cleaned 2026-10-06 |
| — | REFUELING MAGNESIUM BODY LOTION | `post-workout-body-care-set` | DRAFT (2026-10-06 live) | 301 → `muscle-recovery-magnesium-body-lotion` |
| OH200 | Strengthening Protein Conditioner | `strengthening-protein-conditioner` | ACTIVE | vendor/type cleaned 2026-10-06 |
| OH700-KIT | The Marathon Pack | `marathon-pack` | ACTIVE | vendor/type cleaned 2026-10-06 |
| — | Race Day Kit: Anti-Chafe + Recovery Balm | `marathon-race-pack` | ACTIVE | Display title renamed 2026-10-07 (handle unchanged). Compare-at set to $32.98 (sum of the two live balm prices). |

Draft clones (`repair-remedy-duo*`, MLVeda sentinels, `1hr-a-sample-pack`) stay out of the canonical Draft table until a human says they belong there.

## Rules

- A Meta catalog id, if one exists later, is a column added here. It is not invented in the ad playbook.
- Prices belong in this table once a human confirms them. Drafts read the price from here.
- Ingredients and claims wait on [`../compliance/claims.md`](../compliance/claims.md).
