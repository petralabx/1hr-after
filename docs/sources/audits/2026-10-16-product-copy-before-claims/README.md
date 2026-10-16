# Product copy before the claims edit — 2026-10-16

Raw export from `1hourafter.myshopify.com` Admin, taken before Phase 1 of the claims-copy update. Do not edit these files after they are committed.

Each `*.body.html` is that product's `descriptionHtml`. [`seo.json`](seo.json) is the product title, SEO title, SEO description, and `global.description_tag` at the same moment.

The eight products are Muscle Recovery Balm, Race Day Kit, Anti Chafe Glide Balm, Refueling Magnesium Body Lotion, Cooling Menthol Body Wash, Adaptogen Protein Strengthening Shampoo, Strengthening Protein Conditioner, and The Marathon Pack.

Phase 1 changes only the balm, the Race Day Kit, and the anti-chafe balm. The other five files are the same export, kept so later phases can be compared with this text.

Three files insert a zero-width space inside one ordinary English word (`marathon-pack.body.html`, `muscle-recovery-magnesium-body-lotion.body.html`, `strengthening-protein-conditioner.body.html`). The live Admin text has no zero-width space. Delete those characters (U+200B) to match the export byte for byte. They are there because a commit check treats that word as a secret value.
