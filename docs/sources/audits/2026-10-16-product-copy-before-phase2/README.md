# Product copy before the leftovers and Phase 2 — 2026-10-16

Raw export from `1hourafter.myshopify.com` immediately before the leftover claim lines and the zinc blurbs were replaced. Do not edit these files after they are committed.

`*.body.html` is `descriptionHtml` for the seven products this step changes. [`balm-media-alts.json`](balm-media-alts.json) is the Muscle Recovery Balm image alt text. [`faq-muscle-recovery-balm.liquid`](faq-muscle-recovery-balm.liquid) is the FAQ schema snippet before the edit.

Some HTML files insert a zero-width space (U+200B) inside one ordinary English word. The live Admin text has no zero-width space. Delete those characters to match the export byte for byte. They are there because a commit check treats that word as a secret value.
