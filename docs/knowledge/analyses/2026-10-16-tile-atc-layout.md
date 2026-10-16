# Tile and Add to Cart layout

Filed 2026-10-16. Live theme `122661372077` on `1hourafter.myshopify.com`. Prices, product names, and claims copy were not changed.

## What was wrong

- Add to Cart was `position: absolute; right: 0` inside the product column, so the button covered the first benefit line and, on the anti-chafe balm, the Race Day Kit sentence.
- Review counts and pack-contents lines sat in the middle of the product photo because `.product-name-price` spread those items across the card.
- The grey strip above Race Day Essentials was the 35px / 55px `.index-section` padding. The page background is `#c7c4c4`, and that section’s photo starts after the padding.
- The Marathon Pack card used `product.images[3]`, the 1920×800 banner, inside a square tile.

## What changed

- Add to Cart is back in the column: quantity, full-width button, then the kit link, then the bullets. The mobile bar appended to `document.body` is unchanged.
- Review counts stay in the top-left of ordinary tiles, beside the title, instead of across the bottle.
- Race Day Kit and Marathon Pack titles, reviews, and contents sit on a studio-grey band above the photo. The photo uses `object-fit: contain` and the full card width.
- The Marathon Pack card uses the featured square bottle group.
- `#shopify-section-custom_content_Bq8YWE` padding-top is 0. The mobile rule that stacks the photo and then the buttons is unchanged.

## Check

Desktop and a 390px viewport: homepage grid, `/collections/all` Marathon Pack tile, body wash, anti-chafe, and Race Day Kit product pages. Add to Cart no longer intersects the bullets. Pack text no longer intersects the photo. Race Day Essentials meets the runner photo. On a phone, the Race Day photo still comes before the buttons, and the fixed Add to Cart bar is still present.
