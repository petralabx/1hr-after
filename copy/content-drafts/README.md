# Content drafts

Organic pages destined for the 1HR-After site. Each page has two files:

- `<slug>.md` — canonical source.
- `<slug>.html` — paste-ready HTML, regenerated when the markdown changes.

Meta ads do not go here. They go in [`../ads/meta/`](../ads/meta/README.md).

## Templates

- [`_template.md`](_template.md)
- [`_template.html`](_template.html)

```bash
cp _template.md new-slug.md
cp _template.html new-slug.html
```

Write the markdown first. Keep the HTML semantically aligned. Do not publish a page whose prices, products, or claims are not already in the wiki.

## Workflow

1. Pick a target from [`../../docs/knowledge/target-queries.md`](../../docs/knowledge/target-queries.md) or [`../../docs/knowledge/market-map.md`](../../docs/knowledge/market-map.md). If both are empty, stop and ask a human for the query.
2. Fill the markdown. Leave `TBD` where the wiki has no fact.
3. Align the HTML.
4. Check [`../../docs/compliance/claims.md`](../../docs/compliance/claims.md) and [`../../docs/knowledge/brand-voice.md`](../../docs/knowledge/brand-voice.md).
5. After a human publishes, log a `ship` entry in [`../../docs/knowledge/log.md`](../../docs/knowledge/log.md).

## Inventory

| Slug | Status | Target | Published |
|---|---|---|---|
| `_template` | Template | — | n/a |
