---
name: "meteorsliu/publish-to-skills-registry comparator"
description: "Use when the model needs to compare version directories inside meteorsliu/publish-to-skills-registry. This document teaches only pairwise ordering for two concrete versions."
---

# meteorsliu/publish-to-skills-registry Comparator

## Purpose

Define how to compare two published versions under `meteorsliu/publish-to-skills-registry/`.

This document only defines ordering.
It does not define anything beyond pairwise comparison.

## Comparison Rule

Each version directory under `meteorsliu/publish-to-skills-registry/` is an exact published snapshot.

To compare two version directories:

1. Interpret both version directory names as semantic versions.
2. Compare them by semantic version precedence.
3. A higher semantic version is newer.
4. If two versions have equal semantic precedence, compare the raw version strings lexically as a stable tiebreaker.

## Model Guidance

- Compare only concrete published versions that already exist in the registry.
- Do not infer selection policy, installation workflow, or search behavior here.
- If a version string is not a valid semantic version, stop using this rule and ask the user for the intended version-ordering rule or a trusted source.
- Treat version directories as exact artifacts already published in the registry.

## Rationale

`meteorsliu/publish-to-skills-registry` follows semantic versioning by default, so ordering comes from semantic version precedence.
