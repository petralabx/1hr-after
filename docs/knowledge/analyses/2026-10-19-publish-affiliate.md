# Publish the QA theme and the affiliate form — 1HR-After

> Filed: 2026-10-19T23:35:00Z · Kind: ship
> Related: [`2026-10-19-site-qa-fixes.md`](2026-10-19-site-qa-fixes.md)

TASK-3394. The unpublished preview from that write-up is now the live theme. The Muscle Recovery Balm lines from that draft are on the products. The affiliate page has a real application form.

## Published theme

`shopify theme publish` made **1HR-A QA preview** `#189469851821` the live theme. The previous live theme, `#122661372077`, is unpublished. Homepage and `/collections/all` each still have one signup bar. The footer Instagram link still opens in a new tab.

## Balm wording

Admin `productUpdate` on the product HTML. SEO titles were sent with the HTML and stayed:

- Muscle Recovery Balm: `Menthol Muscle Recovery Balm for Endurance Athletes | 1HR-A`
- Race Day Kit: `Race Day Kit: Anti-Chafe Balm + Recovery Balm | 1HR-A`

| Place | Now |
| --- | --- |
| Balm and Race Day Kit, directions | COMES IN A 75G TWIST-UP STICK. |
| Balm and Race Day Kit, directions | THIS BALM CAN BE APPLIED PRE, DURING AND POST WORKOUT |
| Balm and Race Day Kit, important notes | FOR BEST RESULTS, APPLY AFTER SHOWERING WITH OUR COOLING MENTHOL BODY WASH. The wash link stayed in the sentence. |
| Balm benefits only | THIS BALM DEEPLY NOURISHES AND SOFTENS YOUR SKIN. |

The sentence that starts "THIS MUSCLE RUB NOT ONLY" was left as it was. A customer review still says "roll ons". The product copy does not.

The `/collections/all` description still mentions an athletic sampler pack. The sampler product stays draft.

## Affiliate form

`/pages/affiliate-signup` (`templates/page.affilitate.liquid`).

- SIGN UP NOW goes to `#affiliate-signup`.
- The empty Klaviyo mount is gone. The form is Shopify's contact form. It posts to `/contact#AffiliateSignup` and emails the shop. Fields: name, email, social or website, optional note, and a hidden program value `1HR-A affiliate`.
- A customer record with an affiliate tag would not deliver those fields, so this pass uses the contact form.
- The two empty title bars are gone. "How Does It work?" and "SIGN UP" keep their underlines.
- The page heading, the welcome sentence, and the browser title use 1HR-A. The header image is still the 1HOUR AFTER wordmark.
- The 20% commission and 20% off promo lines are the same sentences as before.

The column rules for this page were nested inside `@media (max-width: 1200px)`, so a desktop window stacked the intro and the four steps. A `min-width: 1201px` block puts the intro in two columns and the steps in one row. That block does not close the older media query, so the cart styles that share it stay where they were.

## Live check

Chrome and Firefox, 2026-10-19, no preview parameter.

- Desktop 1440: intro columns share a top edge (528px and 792px). The four steps share a top edge at 306px each.
- Phone 390: intro and steps stack at 350px.
- Empty submit stays on the page and the name field is invalid.
- Submit button is orange `rgb(250, 90, 22)` on white. Labels are white. Inputs are `rgb(28, 28, 28)` on white.
- Clicking SIGN UP NOW scrolls to the form.

## Rollback

Republish theme `#122661372077`. Restore the page title tag to `Join the 1Hour After Affiliate Program | 1HR-After`. Put the four previous balm sentences back with `productUpdate`, and send the SEO titles in the same call.
