# Meta ad copy

Approved and draft Meta (Facebook and Instagram) ads for 1HR-After. One markdown file per variant. This folder is the addition on top of the Furgenics-style content archive.

Playbook: [`../../../docs/channels/meta-ads.md`](../../../docs/channels/meta-ads.md).
Checklist: [`../../../docs/knowledge/best-practices/meta-ads.md`](../../../docs/knowledge/best-practices/meta-ads.md).
Claims: [`../../../docs/compliance/claims.md`](../../../docs/compliance/claims.md).

## Start a variant

```bash
cp _template.md <campaign-slug>/<creative-slug>.md
```

Create the campaign folder with the first file. The folder name matches the campaign slug in the playbook.

## Status

| Value | Meaning |
|---|---|
| `Draft` | Not cleared to run |
| `Approved` | A human set this, and every claim in the ad is named in `docs/compliance/claims.md` |
| `Paused` | Ran, then stopped. Keep the file. |

No file in this folder is `Approved` yet. Do not mark one approved while the claims table is empty.

## Inventory

| File | Campaign | Status |
|---|---|---|
| `_template.md` | — | Template |
