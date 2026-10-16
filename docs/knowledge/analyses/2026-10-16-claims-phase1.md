# Phase 1 claims copy — three ad-linked products — 1HR-After

> Filed: 2026-10-16T18:20:00Z · Kind: ship
> Related: [`2026-10-16-storefront-feedback.md`](2026-10-16-storefront-feedback.md)

Operator approved Phase 1 of the claims-copy prompt: Muscle Recovery Balm, Race Day Kit, and Anti Chafe Glide Balm. Shop `1hourafter.myshopify.com` only. TASK-3116. The other five products were not edited. Phases 2–5 have not started.

The pre-change descriptions and SEO fields for all eight products are in [`docs/sources/audits/2026-10-16-product-copy-before-claims/`](../../sources/audits/2026-10-16-product-copy-before-claims/README.md). That folder was committed before the Admin write.

## Write method

These strings live on the product record, not in the theme. Each change is `productUpdate` on `descriptionHtml`. The balm SEO description was set in the same mutation’s `seo.description` and in `global.description_tag`.

Sending `seo` with only a description cleared the balm’s SEO title for a moment. It was written back in the same session to `Menthol Muscle Recovery Balm for Endurance Athletes | 1HR-A`. The live page title is that string. Product titles were not renamed.

The description typeface was not changed. Replacement sentences are stored in the casing from the prompt. Bold headings stay bold. CSS does not force the description into all caps.

## Before → after

| Product | Field | Before | After | Count |
|---|---|---|---|---|
| Recovery balm | SEO description | Accelerate muscle recovery with 1HR-A menthol and magnesium balm. Formulated for endurance athletes to reduce soreness after intense training. | Menthol and magnesium post-workout balm with a cooling feel, made for endurance athletes. | 1 |
| Recovery balm | Description sentence | FORMULATED TO TARGET SORE AND TIRED MUSCLES, THIS POST WORKOUT PAIN RELIEF BALM… COOLING RELIEF TO THE TARGETED AREAS AFTER AN INTENSE WORKOUT. | This post-workout balm blends menthol crystals, coconut oil, magnesium hydroxide and peppermint oil for an instant cooling sensation after intense training. | 1 |
| Recovery balm | Feature bullet | ACCELERATES RECOVERY: … SOOTHES SORE MUSCLES, HELPING YOU RECOVER FASTER… | COOL DOWN FAST: menthol and peppermint oil deliver an immediate cooling sensation, the perfect end to your session. | 1 |
| Recovery balm | Feature bullet | ENHANCES PERFORMANCE: MAGNESIUM HYDROXIDE WORKS TO PREVENT MUSCLE CRAMPS AND FATIGUE, ALLOWING YOU TO PUSH HARDER AND GO THE EXTRA MILE. | BUILT FOR TRAINING DAYS: a magnesium-enriched formula made for your post-workout ritual. | 1 |
| Recovery balm | Ingredient | MENTHOL CRYSTALS: DELIVER A COOLING EFFECT TO RELIEVE MUSCLE SORENESS AND PAIN. | MENTHOL CRYSTALS: deliver a refreshing cooling sensation on the skin. | 1 |
| Recovery balm | Ingredient | MAGNESIUM HYDROXIDE: HELPS PREVENT MUSCLE CRAMPS AND SUPPORTS MUSCLE FUNCTION. | MAGNESIUM HYDROXIDE: a mineral ingredient that helps the balm glide on smoothly. | 1 |
| Recovery balm and Race Day Kit | How to use | …EASY TO APPLY TO THE AFFECTED AREAS THAT ARE EXPERIENCING PAIN, FATIGUE OR TIREDNESS. | COMING IN A 75G ROLL ON FORMAT. Apply to calves, quads, glutes and shoulders after training. | 1 on each product |
| Recovery balm and Race Day Kit | How to use | SIMPLY DRY OFF THE AREA YOU WANT TO TARGET AND RUB ON THE ROLL-ON PAIN RELIEVER UNTIL FULLY ABSORBED. | Twist up the stick and massage in until fully absorbed. | 1 on each product |
| Race Day Kit | Description | Menthol cools at the skin; magnesium and zinc are in the formula for the deeper ache. | Menthol cools at the skin, and the formula is enriched with magnesium and zinc. | 1 |
| Anti-chafe | Description clause | COCONUT OIL FOR ITS ANTI-INFLAMMATORY PROPERTIES | Coconut oil for a smooth, conditioning glide | 1 |
| Anti-chafe | Ingredient | PIROCTONE OLAMINE: REGULATES FUNGI GROWTH, REDUCES SEBUM SECRETION, AND PREVENTS INFLAMMATION. | Piroctone olamine: helps keep skin feeling fresh during long sessions. | 1 |
| Anti-chafe | Ingredient | SHEA BUTTER: RICH BUTTER THAT PROTECTS SKIN AND REPAIRS DAMAGE | Shea butter: a rich butter that moisturizes and conditions skin. | 1 |

The kit how-to lines are a copy inside the kit description, not a live inherit from the balm, so both records were edited. Kit and anti-chafe SEO descriptions were left as they were. The other five products’ `descriptionHtml` still matches the archive.

Two punctuation choices, both visible in the diff:

- The coconut line sits in the middle of a sentence that already had a comma after the old clause. The approved period was not added, so the line reads “conditioning glide, OUR” rather than “glide.,”.
- The 75g format fact stayed as its own sentence in front of the new apply line. The dry-off clause was in the same sentence as the pain-reliever line, so it went with that sentence. The middle sentence about applying pre, during, and post workout was not in the table and is still there.

## Still on these pages, outside the Phase 1 table

- Recovery balm image alt: “post-workout pain relief”.
- Recovery balm FAQ answers still say “PAIN RELIEF MUSCLE RECOVERY BALM”.
- Recovery balm vitamin E line still says it protects and repairs the skin.
- Anti-chafe still has “PREVENTING PAINFUL CHAFING” in the paragraph above the coconut line.

Those were not in the Phase 1 table, so they were not changed.

## Rollback

Put the archived `descriptionHtml` back with `productUpdate`, and put the archived SEO description back on the balm. The three Phase 1 HTML files have no zero-width spaces. Strip U+200B before restoring the other three files in that folder.
