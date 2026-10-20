# Site QA fixes — 1HR-After

> Filed: 2026-10-19T23:20:00Z · Kind: ship
> Related: [`2026-10-19-tile-separation.md`](2026-10-19-tile-separation.md)

Browser QA on 1hourafter.com. Theme `#122661372077` stayed published. The fixes are on unpublished theme **1HR-A QA preview** `#189469851821`. TASK-3392. Preview: `https://1hourafter.com?preview_theme_id=189469851821`.

## What changed

| Issue | Fix |
| --- | --- |
| 1. FAQ answer text | The product column forces white text. Scoped rules in `onehour.css` set the Webkul answer to `#1c1c1c` on the light panel. Contrast on the balm page is 16.6:1. |
| 2. FAQ toggle | The row's plus link already toggled. The heading now triggers that same control, the hash jump is cancelled, and the stray `alert('hii')` is gone. The icon flips between plus and minus. |
| 3. Instagram | The footer link has `target="_blank"` and `rel="noopener noreferrer"`. It is the only Instagram link in the theme. |
| 4. Star icons | `* { font-family: MonoSpec !important }` was winning over Judge.me's star font, and the star glyphs were white. Card stars now use `JudgemeStar` in `#3a3a3a`. |
| 5. Card type | Review counts and the two pack subtitles are 12px, weight 400, on every tile. |
| 6. Signup copy | Heading "Join the 1HR-A list" and the twice-a-month sentence. Placeholder "Email address". Button stays "Subscribe". Both strings are section settings. |
| 7. Duplicate signup | The collection template and `templates/collection.liquid` each printed a form, and the lab-tag loop often skipped the photo wrapper. One bar remains, under the collection grid, with the same photo as the homepage bar. |

The signup still posts to Shopify's customer form (`/contact`) with the `newsletter` tag.

## Left for a decision

- **Affiliate page (issue 8).** The header, footer, and page stay as they are. Option A pauses the links. Option B wires a real form. Nothing was changed.
- **Phase 5 product copy.** These lines are still in the live product HTML. They were not edited, because a product write would publish immediately and this pass stays on the preview theme.

| Product | Current | Proposed |
| --- | --- | --- |
| Muscle Recovery Balm, Directions | COMING IN A 75G ROLL ON FORMAT. | COMES IN A 75G TWIST-UP STICK. |
| Muscle Recovery Balm, Directions | THIS MUSCLE CARE ROLL ON CAN BE APPLIED PRE, DURING AND POST WORKOUT | THIS BALM CAN BE APPLIED PRE, DURING AND POST WORKOUT |
| Muscle Recovery Balm, Important notes | FOR EVEN MORE BETTER RESULTS, APPLY THIS MUSCLE CARE ROLL ON AFTER TAKING A BATH WITH OUR COOLING MENTHOL BODY WASH! | FOR BEST RESULTS, APPLY AFTER SHOWERING WITH OUR COOLING MENTHOL BODY WASH. |
| Muscle Recovery Balm, Benefits | …THIS MUSCLE RUB DEEPLY NOURISHES YOUR SKIN WHILE PROVIDING ESSENTIAL NUTRIENTS TO YOUR MUSCLES. | …THIS BALM DEEPLY NOURISHES AND SOFTENS YOUR SKIN. |

The collection description's "athletic sampler pack" line was left as it is. The sampler product stays draft.

## Live check

Chrome and Firefox, cache off, preview theme, 2026-10-19.

- Balm FAQ: heading click opens the block and the icon becomes minus. A second click closes it and the icon returns to plus. The open answer is `rgb(28, 28, 28)` on `rgb(251, 252, 254)`.
- The same answer color is on the other six product templates that share this FAQ block. Marathon Pack and Race Day Kit use the same product section.
- Collection tiles: every review count is 12px / 400. Both subtitles are 12px / 400. Star font is `JudgemeStar`, color `rgb(58, 58, 58)`. No failed Judge.me requests.
- Homepage and `/collections/all`: one signup bar each, at 1440px and 390px, with the lab-series photo. The form action is `/contact`.
- Footer Instagram opens with `target="_blank"`.

`shopify theme check` still reports existing Debut schema type errors in older settings. The new signup settings are plain text fields.

## Rollback

In Shopify admin, delete unpublished theme `#189469851821`, or leave it unpublished. The published theme `#122661372077` was not updated.
