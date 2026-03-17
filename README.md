# skills-registry

Hosted registry for versioned AI skills.

## Search

- Use [INDEX.md](./INDEX.md) as the primary discovery surface for skills.
- Keep `INDEX.md` concise: names, short summaries, tags, and the latest published version.
- Use repo-level and version-level documents only after search narrows the candidate set.

## Layout

Skills are stored under:

```text
{owner}/{repo}/COMPARATOR.md
{owner}/{repo}/{version}/
```

Example:

```text
openai/pdf/COMPARATOR.md
openai/pdf/77963424cd76/
```

The first published entry uses the verified upstream source commit as the version directory because the upstream `pdf` skill does not publish a separate semantic version.

## Comparator Files

- `{owner}/{repo}/COMPARATOR.md` is the repo-level comparison guide for the model.
- It should define only how to compare concrete version directories for that repo.
- It should not define anything beyond pairwise ordering.
- If `COMPARATOR.md` is absent, the local installer workflow may use its own default comparison logic.
- Version directories are exact published artifacts.
