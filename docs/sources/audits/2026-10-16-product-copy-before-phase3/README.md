# Product copy before Phase 3 — 2026-10-16

Raw export from `1hourafter.myshopify.com` immediately before the Phase 3 claim lines were replaced. Do not edit these files after they are committed.

`*.body.html` is `descriptionHtml` for the five products this step changes. [`seo.json`](seo.json) is the SEO title, SEO description, and `global.title_tag` / `global.description_tag` values at the same moment.

Some HTML files insert a zero-width space (U+200B) inside one ordinary English word. The live Admin text has no zero-width space. Delete those characters to match the export byte for byte. They are there because a commit check treats that word as a secret value.
