# Phase 3 remaining product copy — 1HR-After

> Filed: 2026-10-16T19:02:00Z · Kind: ship
> Related: [`2026-10-16-claims-phase2.md`](2026-10-16-claims-phase2.md)

Operator merged the Phase 2 pull request and asked for the next phase. Shop `1hourafter.myshopify.com` only. TASK-3129. Product titles were not renamed. [`docs/compliance/claims.md`](../../compliance/claims.md) was not edited; the operator prompt is the approval for these lines.

The pre-change descriptions and SEO fields are in [`docs/sources/audits/2026-10-16-product-copy-before-phase3/`](../../sources/audits/2026-10-16-product-copy-before-phase3/README.md). That folder was committed before the Admin write.

## Write method

Each change is `productUpdate` on `descriptionHtml`. The lotion and the body wash also sent `seo.title` together with `seo.description`, and `global.description_tag` was set to the same description. The other three products’ SEO fields were not sent. The description typeface was not changed.

## Before → after

| Product | Field | After | Count |
|---|---|---|---|
| Lotion | Opening sentence and SEO description | Post-workout body lotion with magnesium chloride, panthenol and niacinamide to hydrate and refresh skin after your shower. | 1 in the body, 1 in SEO |
| Lotion | Description ending | The lead-in stays through “A RELIABLE SOLUTION FOR”, then “refuelling, replenishing and rehydrating your skin after every workout.” | 1 |
| Lotion | Feature bullet | “Reduces inflammation” removed. The list still has the other bullets. | 1 |
| Lotion | Feature bullet | A relaxing post-workout ritual. | 1 |
| Lotion | Vitamin B5 | helps improve hydration, elasticity and smoothness. | 1 |
| Lotion | Niacinamide | The moisture sentence stays. The redness clause is “Helps skin look more even and feel soothed.” | 1 |
| Lotion | Jojoba oil | a lightweight oil that moisturizes without clogging pores. | 1 |
| Lotion | Magnesium | The bones, heart, blood-pressure sentence and the calcium sentence are removed. The bullet still ends on “a deep sea mineral magnesium that is crucial for the body’s functions.” | 1 |
| Lotion | How to use | The dispensing lead-in stays. The joints step and the muscle-discomfort step are one line: “rub onto arms, legs and shoulders using circular motions.” | 1 |
| Body wash | SEO description | Post-workout cooling body wash with menthol and zinc for hot, sweaty skin. Made clean in North America. | 1 |
| Body wash | Description | The lead-in stays through “COOLING DOWN WHILE”, then “leaving skin feeling cool and refreshed.” | 1 |
| Body wash | Feature bullet | Zinc helps skin feel clean and balanced. | 1 |
| Body wash | Feature bullet | A cooling, refreshing post-workout shower. | 1 |
| Body wash | Menthol | delivers a cooling sensation on the skin. | 1 |
| Shampoo | Aloe | Aloe leaf juice: soothes and refreshes the scalp. The following cleanse sentence stays. | 1 |
| Conditioner | Jojoba oil | moisturizes hair and scalp without weighing hair down. | 1 |
| Marathon Pack | Aloe | Aloe leaf juice: soothes the scalp and gently cleanses build-up. | 1 |
| Marathon Pack | Jojoba oil (conditioner block) | moisturizes and helps balance oil. | 1 |
| Marathon Pack | Menthol | provides a cooling sensation. | 1 |
| Marathon Pack | Magnesium | a deep-sea mineral in our post-workout formula. | 1 |

Notes on lines that were not a single swap:

- The lotion SEO description was empty. The quoted magnesium and niacinamide sentence was the opening of the description, so that sentence and the SEO description both use the approved line. The SEO title stayed “Refueling Magnesium Body Lotion for Muscle Recovery | 1HR-A”.
- The body-wash meta already had the approved opening plus the sore-muscles sentence plus “Made clean in North America.” The sore-muscles sentence is now the approved line, and the made-clean sentence stays.
- The lotion how-to quote covered two list items. The bridge “RUB ONTO YOUR BODY, OR DIRECTLY ONTO” went with those items so the line would not read “ONTO rub onto”.
- The magnesium bullet did not need the optional closer. The first sentence was already complete after the two claim sentences were removed.

SEO titles on all five products match the pre-write values. Shampoo, conditioner, and Marathon Pack SEO descriptions were not in this table and were not changed.

## Still on these pages, outside the Phase 3 table

- Shampoo feature bullet: “ANTIFUNGAL PROPERTIES HELP PROTECT AGAINST DANDRUFF”, and the opening line about repairing hair bonds.
- Marathon Pack lotion-block jojoba line still says it promotes healing. Vitamin B5 still says anti-inflammatory. The intro still says the shampoo strengthens and repairs hair.
- FAQ snippets for the lotion, wash, and Race Day Kit still use soreness, cramps, and inflammation language. They were not in the Phase 3 table.
- Phase 4 is the site-wide keyword report. It has not been started.

## Check

Admin re-fetch matched the HTML that was sent. Storefront HTML for the lotion, wash, shampoo, conditioner, and Marathon Pack shows the new sentences. The old claim phrases from this table are gone from those descriptions.

## Rollback

Restore each `descriptionHtml` from the phase-3 archive with `productUpdate`, after deleting U+200B. Restore lotion and wash `seo.description` and `global.description_tag` from [`seo.json`](../../sources/audits/2026-10-16-product-copy-before-phase3/seo.json). Send the SEO title in the same `seo` object. The lotion description was null; clearing it means sending an empty description with the title.
