# Filing analyses

An analysis is a durable answer. Chat history is not.

File one when a session synthesizes several wiki pages, or when someone asks for a write-up that the next session should not rediscover.

## How to file

1. Add `docs/knowledge/analyses/YYYY-MM-DD-<slug>.md`.
2. Prepend a bullet between the `AUTO-APPEND:analyses` markers in [`../index.md`](../index.md), newest first:

```markdown
- [Title](analyses/YYYY-MM-DD-<slug>.md) — filed YYYY-MM-DD as `query` · one-line summary
```

Kinds: `query` · `synthesis` · `brief` · `analysis` · `infra`.

3. Append a matching entry at the top of the timeline in [`../log.md`](../log.md):

```markdown
## [YYYY-MM-DDTHH:MM:SSZ] query | Title
```

4. Do not edit Class C pages as a side effect of filing. Propose those changes in the PR instead.

## Do not file

- Secrets, customer lists, or COGS.
- Another brand's analysis pasted under a 1HR-After title.
- A restatement of a page that already says the same thing. Link that page instead.
