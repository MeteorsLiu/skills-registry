# COMPARATOR.md Template

Use this template for repos that follow the default semantic-version workflow.
Under that workflow, the first version is `v0.1.0` when the user does not specify a version.

If the target repo already uses a different verified versioning scheme, do not use this template blindly.
Investigate the repo's real ordering rule first, and ask the user if it is still unclear.

```md
---
name: "<owner>/<repo> comparator"
description: "Use when the model needs to compare version directories inside <owner>/<repo>. This document teaches only pairwise ordering for two concrete versions."
---

# <owner>/<repo> Comparator

## Purpose

Define how to compare two published versions under `<owner>/<repo>/`.

This document only defines ordering.
It does not define anything beyond pairwise comparison.

## Comparison Rule

Each version directory under `<owner>/<repo>/` is an exact published snapshot.

To compare two version directories:

1. Interpret both version directory names as semantic versions.
2. Compare them by semantic version precedence.
3. A higher semantic version is newer.
4. If two versions have equal semantic precedence, compare the raw version strings lexically as a stable tiebreaker.

## Model Guidance

- Compare only concrete published versions that already exist in the registry.
- Do not infer selection policy, installation workflow, or search behavior here.
- If a version string is not a valid semantic version, stop using this template and investigate the repo's actual versioning rule.
- Treat version directories as exact artifacts already published in the registry.

## Rationale

`<owner>/<repo>` follows semantic versioning by default, so ordering comes from semantic version precedence.
```
