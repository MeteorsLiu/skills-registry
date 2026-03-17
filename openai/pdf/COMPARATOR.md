---
name: "openai/pdf comparator"
description: "Use when the model needs to compare version directories inside openai/pdf. This document teaches only pairwise ordering for two concrete versions."
---

# openai/pdf Comparator

## Purpose

Define how to compare two published versions under `openai/pdf/`.

This document only defines ordering.
It does not define anything beyond pairwise comparison.

## Comparison Rule

Each version directory under `openai/pdf/` is an exact published snapshot.

To compare two version directories:

1. Read each directory's `source.json`.
2. Extract `source.commit_date`.
3. The directory with the later `source.commit_date` is newer.

If the two commit dates are equal, compare the version directory names lexically as a stable tiebreaker.

## Model Guidance

- Compare only concrete published versions that already exist in the registry.
- Do not interpret version directory names here as semantic versions.
- Do not infer anything beyond pairwise ordering here.
- If required comparison metadata is missing, report that the versions cannot be compared reliably instead of inferring.
- Treat version directories as exact artifacts already published in the registry.

## Rationale

`openai/pdf` currently uses upstream snapshot commits as version directory names.
Those directory names are not a semantic-version scheme, so ordering must come from the upstream commit metadata recorded in `source.json`.
