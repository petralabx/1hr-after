# Products

> **Owner:** Class B (agent proposes, human approves semantic changes)
> **Status:** Canonical tables still empty. A **proposed** snapshot from live Admin (2026-10-06) is below; it is not approved.
> **Last updated:** 2026-10-06

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
| OH100 | ADAPTOGEN PROTEIN STRENGTHENING SHAMPOO | `adaptogen-protein-strengthening-shampoo` | ACTIVE | pending |
| OH100-A | ADAPTOGEN PROTEIN STRENGTHENING SHAMPOO | `1hr-adaptogen-shampoo` | ACTIVE | pending (duplicate title) |
| OH800-KIT | ANTI CHAFE GLIDE BALM | `anti-chafe-balm` | ACTIVE | pending |
| OH300-FBA | COOLING MENTHOL BODY WASH | `cooling-menthol-body-wash` | ACTIVE | pending |
| OHSP50 | Free 1Hour-After Athletic Sampler Pack | `free-1hour-after-athletic-sampler-pack` | ACTIVE | pending (SKU also on a draft) |
| 2 | LAB/SS-001 | `lab-ss-001` | ACTIVE | pending (thin; likely unpublish) |
| OH701-KIT | Muscle Recovery Balm | `post-workout-hair-care-kit` | ACTIVE | pending (handle/title mismatch) |
| — | Muscle Recovery Balm | `muscle-recovery-balm` | ACTIVE | pending (SKU blank in Admin) |
| — | Recovery BodyGel | `recovery-body-gel` | ACTIVE | pending (SKU blank) |
| OH600-FBA | REFUELING MAGNESIUM BODY LOTION | `muscle-recovery-magnesium-body-lotion` | ACTIVE | pending |
| — | REFUELING MAGNESIUM BODY LOTION | `post-workout-body-care-set` | ACTIVE | pending (duplicate title) |
| OH200 | Strengthening Protein Conditioner | `strengthening-protein-conditioner` | ACTIVE | pending |
| OH700-KIT | The Marathon Pack | `marathon-pack` | ACTIVE | pending |
| — | THE MARATHON RACE PACK | `marathon-race-pack` | ACTIVE | pending (SKU blank) |

Draft clones (`repair-remedy-duo*`, MLVeda sentinels, `1hr-a-sample-pack`) stay out of the canonical Draft table until a human says they belong there.

## Rules

- A Meta catalog id, if one exists later, is a column added here. It is not invented in the ad playbook.
- Prices belong in this table once a human confirms them. Drafts read the price from here.
- Ingredients and claims wait on [`../compliance/claims.md`](../compliance/claims.md).
