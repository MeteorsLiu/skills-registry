# skills-registry

Hosted registry for versioned AI skills.

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

## Version Selection

- `{owner}/{repo}/COMPARATOR.md` is the repo-level comparison guide for the model.
- It defines how to compare version directory names for that repo.
- If `COMPARATOR.md` is absent, the local installer workflow should follow LLAR's fallback behavior and use GNU version comparison on directory names.
- Exact-version choice, latest-version choice, and MVS-style max selection belong to the local install workflow, not to the repo-level comparison guide.
- Version directories are exact published artifacts. Unlike LLAR formula `fromVer` matching, the registry does not implicitly choose the highest directory less than or equal to a requested version unless the local install workflow explicitly adds that policy.
