# skills-registry

Hosted registry for versioned AI skills.

## Layout

Skills are stored under:

```text
{owner}/{repo}/{version}/
```

Example:

```text
openai/pdf/77963424cd76/
```

The first published entry uses the verified upstream source commit as the version directory because the upstream `pdf` skill does not publish a separate semantic version.
