---
name: "openai/pdf comparator"
description: "Use when the model needs to compare version directories inside openai/pdf. This document defines ordering only; exact-version choice, latest-version choice, and maximum-version selection across multiple requests belong to the local installer workflow."
---

# openai/pdf Comparator

## Purpose

Define how to compare two published versions under `openai/pdf/`.

This document only defines ordering.
It does not decide whether to choose an exact version.
It does not decide whether to choose the latest version.
It does not decide how to merge multiple requested versions.

## Comparison Rule

Each version directory under `openai/pdf/` is an exact published snapshot.

To compare two version directories:

1. Read each directory's `source.json`.
2. Extract `source.commit_date`.
3. The directory with the later `source.commit_date` is newer.

If the two commit dates are equal, compare the version directory names lexically as a stable tiebreaker.

## Boundaries

- Do not interpret version directory names here as semantic versions.
- Do not apply implicit `<= target` fallback here.
- Do not choose `max` here just because multiple candidates exist; that decision belongs to the local installer workflow.
- Treat version directories as exact artifacts already published in the registry.

## Rationale

`openai/pdf` currently uses upstream snapshot commits as version directory names.
Those directory names are not a semantic-version scheme, so ordering must come from the upstream commit metadata recorded in `source.json`.
