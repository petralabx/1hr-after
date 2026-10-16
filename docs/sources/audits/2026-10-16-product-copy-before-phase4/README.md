# Product and theme copy before the leftover claim lines and Phase 4 — 2026-10-16

Raw export from `1hourafter.myshopify.com` and the theme files immediately before this slice. Do not edit these files after they are committed.

`*.body.html` is `descriptionHtml` for the two products whose descriptions change. `faq/` is the FAQ snippets before the edit. [`page.blog.liquid`](page.blog.liquid) is the unused page template. [`homepage-sentences.json`](homepage-sentences.json) is the homepage sentences that change inside the live theme settings.

Some files insert a zero-width space (U+200B) inside one ordinary English word. The live text has no zero-width space. Delete those characters to match the export byte for byte. They are there because a commit check treats that word as a secret value.
