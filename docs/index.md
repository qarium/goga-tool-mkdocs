# goga-tool-mkdocs

MkDocs documentation maintenance tool for the Goga framework.

## What it does

`goga-tool-mkdocs` orchestrates creation, synchronization, patching, validation, and maintenance of MkDocs documentation using authoritative project artifacts.

It is invoked via the Goga aggent command:

```bash
/goga:tool mkdocs
```

## How it works

The tool runs a deterministic pipeline of subskills that discover project artifacts, analyze changes, build documentation structure, write content, synchronize navigation, and validate results.

Two execution modes are available:

- **Bootstrap** — generates documentation from scratch when no prior state exists
- **Incremental** — patches existing documentation based on detected changes

## Authoritative sources

Documentation is generated from:

- `CODEMANIFEST` files
- `.usages/**/*.md` files
- `.tests/**/*.yml` / `.tests/**/*.yaml` files

## Quick links

- [Getting Started](getting-started.md)
- [Pipeline](pipeline.md)
- [Skills](skills/mkdocs.md)
