---
name: "alaminrifat/file-to-markdown comparator"
description: "Use when the model needs to compare version directories inside alaminrifat/file-to-markdown. This document teaches only pairwise ordering for two concrete versions."
---

# alaminrifat/file-to-markdown Comparator

## Purpose

Define how to compare two published versions under `alaminrifat/file-to-markdown/`.

This document only defines ordering.
It does not define anything beyond pairwise comparison.

## Comparison Rule

Each version directory under `alaminrifat/file-to-markdown/` is an exact published snapshot.

To compare two version directories:

1. Parse each directory name as a valid SemVer 2.0.0 version.
2. Compare `major`, `minor`, and `patch` numerically.
3. A version without a pre-release field has higher precedence than one with the same `major.minor.patch` and a pre-release field.
4. If both versions have pre-release fields, compare dot-separated pre-release identifiers from left to right:
   - compare numeric identifiers numerically
   - compare non-numeric identifiers lexically in ASCII sort order
   - treat numeric identifiers as lower precedence than non-numeric identifiers
   - if all compared identifiers are equal so far, the version with fewer pre-release identifiers has lower precedence
5. Ignore build metadata for precedence.
6. If the two versions still have equal precedence, treat them as semantically equal for ordering under this comparator.

## Model Guidance

- Compare only concrete published versions that already exist in the registry.
- Do not infer selection policy, installation workflow, or search behavior here.
- If a version directory name does not match plain SemVer 2.0.0, stop using this comparator and investigate the repo's actual versioning rule.
- Treat version directories as exact artifacts already published in the registry.

## Rationale

The upstream skill metadata publishes `latest.version` values like `1.0.0`, which follow plain SemVer 2.0.0 without a leading `v`.
