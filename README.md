# skills-registry

Hosted registry for versioned AI skills.

## Layout

Skills are stored under:

```text
{owner}/{repo}/selector.json
{owner}/{repo}/{version}/
```

Example:

```text
openai/pdf/selector.json
openai/pdf/77963424cd76/
```

The first published entry uses the verified upstream source commit as the version directory because the upstream `pdf` skill does not publish a separate semantic version.

## Version Selection

- `{owner}/{repo}/selector.json` is the repo-level version selection contract.
- It defines how to compare version directory names for that repo and how to pick the selected version.
- If `selector.json` is absent, the default comparator should follow LLAR's fallback behavior and use GNU version comparison on directory names.
- Latest-version selection follows LLAR's current idea: enumerate candidate versions and choose the maximum version according to that repo's comparator.
- Multi-request resolution also follows the same MVS-style rule: when multiple requests name different versions of the same repo, select the maximum requested version according to the same comparator.
- Version directories are exact published artifacts. Unlike LLAR formula `fromVer` matching, the registry does not implicitly choose the highest directory less than or equal to a requested version unless a repo-level selector explicitly adds that rule later.
