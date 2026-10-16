# Phase 2 zinc copy, plus the Phase 1 leftovers — 1HR-After

> Filed: 2026-10-16T18:29:00Z · Kind: ship
> Related: [`2026-10-16-claims-phase1.md`](2026-10-16-claims-phase1.md)

Operator asked for the four leftover lines from Phase 1, then Phase 2. Shop `1hourafter.myshopify.com` only. TASK-3120. Product titles were not renamed. `docs/compliance/claims.md` was not edited; the operator prompt is the approval for these specific lines.

The pre-change descriptions, the two balm image alts, and the balm FAQ snippet are in [`docs/sources/audits/2026-10-16-product-copy-before-phase2/`](../../sources/audits/2026-10-16-product-copy-before-phase2/README.md). That folder was committed before the Admin write and the theme push.

## Write method

Product sentences are `descriptionHtml` via `productUpdate`. The mutation did not send `seo`, so SEO titles and SEO descriptions stayed as they were. Image alts used `productUpdateMedia` on the balm. The FAQ is JSON-LD in [`site/theme/snippets/faq-muscle-recovery-balm.liquid`](../../../site/theme/snippets/faq-muscle-recovery-balm.liquid), pushed alone to theme `#122661372077`. The asset `updated_at` is `2026-10-16T14:28:28-04:00`.

The description typeface was not changed. New sentences use the casing from the prompt. Bold labels stay bold.

## Leftovers from Phase 1

| Place | Before | After | Count |
|---|---|---|---|
| Balm media `27959679516845` | 1HR-A Muscle Recovery Balm jar with cooling menthol formula for post-workout pain relief | 1HR-A Muscle Recovery Balm jar with a cooling menthol formula. | 1 |
| Balm media `27786065871021` | 1HR-A Muscle Recovery Balm stick for fast relief targeting Hyrox competitors and endurance athletes | 1HR-A Muscle Recovery Balm stick for Hyrox competitors and endurance athletes. | 1 |
| Balm vitamin E span | a AN ANTIOXIDANT THAT PROTECTS AND REPAIRS THE SKIN. | an antioxidant in the balm. | 1 |
| Anti-chafe paragraph | PREVENTING PAINFUL CHAFING AND IRRITATION | PREVENTING CHAFING AND IRRITATION | 1 |

Only the word PAINFUL was removed from the anti-chafe sentence. The rest of that paragraph is unchanged.

The balm FAQ answers were rewritten, and the question “CAN THIS BALM HELP WITH CHRONIC MUSCLE PAIN?” was removed with its answer. The conjunction question now says “OTHER SKIN PRODUCTS” in the question and the answer. Sensitive-skin, ages, storage, animals, and shelf-life answers were left as they were. “Muscle Recovery Balm” and “muscle rub” stay as product names. The schema now has 11 questions.

## Phase 2 zinc sentences

Each old zinc sentence was replaced once. The label stays in its existing tag.

| Product | After |
|---|---|
| Magnesium body lotion | Zinc: a mineral that helps skin look and feel balanced. |
| Cooling menthol body wash | Zinc: a mineral that helps skin look and feel balanced. |
| Adaptogen protein shampoo | Zinc: helps keep the scalp feeling clean and balanced. |
| Strengthening protein conditioner | Zinc: helps keep the scalp feeling clean and balanced. |
| Marathon Pack, shampoo block | Zinc: helps skin and scalp feel clean and balanced. |
| Marathon Pack, body wash block | Zinc: helps skin look and feel balanced. |
| Marathon Pack, lotion block | Zinc: helps skin look and feel balanced. |

The lotion block on the Marathon Pack was not in the Phase 2 table. The live line was “ZINC: ANTI-INFLAMMATORY AND ANTI-FUNGAL PROPERTIES HELP WITH VARIOUS SKIN CONDITIONS.” It is mapped to the nearest approved sentence, “Zinc: helps skin look and feel balanced.”

The conditioner intro still lists “ZINC, AMINO ACIDS…”. INCI lines that say “ZINC PCA” were left on every product that has them.

The Race Day Kit’s only zinc mention is the Phase 1 sentence, “the formula is enriched with magnesium and zinc.” That record was not edited in this slice.

## Still present, owned by Phase 3

These zinc-adjacent lines were not in the Phase 2 table and were not changed:

- Body wash feature bullet: “ANTIFUNGAL ZINC HELPS COMBAT SKIN DRYNESS AND ACNE”, and the earlier line about fighting inflammation next to the menthol–zinc wash.
- Lotion opening: niacinamide “to reduce inflammation” sits in the same sentence as “microbiome-balancing zinc.”
- Shampoo feature language about antifungal properties and dandruff, which is not the zinc ingredient sentence.
- Conditioner vitamin E, jojoba, and the other ingredient claims in the Phase 3 table.
- Marathon Pack lines for aloe, jojoba, menthol, magnesium, vitamin E, and vitamin B5.
- FAQ snippets for the lotion, wash, shampoo, conditioner, packs, and anti-chafe balm.

## Check

Admin re-fetch matched the HTML that was sent. SEO titles on all seven edited products matched the pre-write values. Storefront HTML for the balm, anti-chafe balm, lotion, and Marathon Pack shows the new sentences and does not show the old claim phrases. The balm page includes the new FAQ answer and does not include the chronic-pain question.

## Rollback

Restore each `descriptionHtml` from the phase-2 archive with `productUpdate`, after deleting U+200B. Some archived HTML files insert that character inside one ordinary English word; the live Admin text has none. Restore the two alts from [`balm-media-alts.json`](../../sources/audits/2026-10-16-product-copy-before-phase2/balm-media-alts.json). Push the archived FAQ snippet to theme `#122661372077`.
