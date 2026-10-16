# Leftover claim lines and Phase 4 — 1HR-After

> Filed: 2026-10-16T19:24:00Z · Kind: ship
> Related: [`2026-10-16-claims-phase3.md`](2026-10-16-claims-phase3.md)

Operator merged the Phase 3 pull request and asked for the leftover lines from that write-up, then the next phase. Shop `1hourafter.myshopify.com` only. TASK-3131. Product titles were not renamed. [`docs/compliance/claims.md`](../../compliance/claims.md) was not edited.

The pre-change descriptions, FAQ snippets, blog template, and homepage sentences are in [`docs/sources/audits/2026-10-16-product-copy-before-phase4/`](../../sources/audits/2026-10-16-product-copy-before-phase4/README.md). That folder was committed before the writes.

## Leftovers from Phase 3

| Place | After |
|---|---|
| Shampoo opening | “FORGING NEW BONDS IN YOUR HAIR FIBERS AFTER SWEATING” |
| Shampoo feature bullet | “Helps the scalp feel clean and balanced.” |
| Marathon Pack shampoo line | “TO STRENGTHEN HAIR AFTER PROLONGED SWEATING.” |
| Marathon Pack wash line | “TO REFRESH YOUR SKIN” |
| Marathon Pack how-to | “FOCUS ON THE SKIN” |
| Marathon Pack lotion jojoba | “Jojoba oil: a lightweight oil that moisturizes without clogging pores.” |
| Marathon Pack vitamin B5 | “Vitamin B5: helps improve hydration, elasticity and smoothness.” |
| Marathon Pack niacinamide | The redness clause is removed. The moisture-protein sentence stays. |

The jojoba and vitamin B5 lines use the approved sentences from the lotion table, which were the nearest wording for those bullets.

## Phase 4 on the product pages and homepage

The keyword sweep found the same claim language in the FAQ snippets and in four homepage settings. Those were updated. Questions that were only a treatment claim were removed: the lotion deficiency question and the muscle-relaxant question. The lotion FAQ now has 10 questions.

Homepage sentences now read:

- “Magnesium is a mineral in our post-workout formula.”
- “Zinc is a mineral that helps skin look and feel balanced.”
- “This vitamin blend hydrates and strengthens skin and hair.”
- “To be used during and after endurance events for a cooling feel on the skin.”
- “care for your hair and skin after exercise”

The live theme settings were updated on theme `#122661372077`. The repo copy of `settings_data.json` has the same five sentence changes. `mlvedaACS_enable` stayed true. The file was not pushed as a full settings replacement from an older export.

`templates/page.blog.liquid` is a placeholder template and is not assigned to a live page. Its acne, fungal, and “Repair Remedy Duo” alt text were still replaced.

## Classification of what was left

| Location | Term | Classification |
|---|---|---|
| Product titles and SEO titles, including Muscle Recovery Balm | recovery, muscle | Product name. Left in place. |
| Homepage heading “We'll Help You Recover” | recover | Brand line. Left in place. |
| “Healthcare professional” in safety answers | heal inside healthcare | Safety disclaimer. Left in place. |
| “Healthy” and “skin health” | heal inside health | Ordinary wording. Left in place. |
| News articles, 50 in the `news` blog | sore, pain, relief, recovery, and related titles | Editorial. Not edited. Examples: “How to Recover from Workouts Properly: Relieve Sore Muscles Faster”, “Magnesium: The Ultimate Secret Weapon for Athletes' Rest, Recovery, and Pain Relief”, “What Causes DOMs (Delayed Onset Muscle Soreness)”. |

## Check

Admin re-fetch matched the shampoo and Marathon Pack HTML. SEO titles were not sent and still match. Storefront HTML for the homepage, shampoo, Marathon Pack, lotion, and body wash shows the new sentences. The old claim phrases from this slice are gone from those surfaces.

## Rollback

Restore the two `descriptionHtml` values from the phase-4 archive with `productUpdate`, after deleting U+200B. Push the archived FAQ snippets and `page.blog.liquid` to theme `#122661372077`. Put the five homepage sentences from [`homepage-sentences.json`](../../sources/audits/2026-10-16-product-copy-before-phase4/homepage-sentences.json) back into the live theme settings.
