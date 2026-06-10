# mkdocs

Master orchestration skill for MkDocs documentation maintenance.

## Role

Coordinates all subskills in deterministic order to create, synchronize, patch, validate, and maintain MkDocs documentation.

## Invocation

```text
/goga:tool mkdocs
```

Invoked via the Goga tool agent command dispatcher. Not invoked directly by other skills.

## Execution modes

| Mode | When |
|------|------|
| Bootstrap | No prior documentation state exists |
| Incremental | Documentation already exists, needs patching |

## Subskills

| Subskill | Purpose |
|----------|---------|
| [Discovery](discovery.md) | Discover authoritative artifacts |
| [Impact Analysis](impact-analysis.md) | Detect affected and stale pages |
| [Structure](structure.md) | Build documentation hierarchy |
| [Writer](writer.md) | Create and patch content |
| [Nav Sync](nav-sync.md) | Synchronize mkdocs.yml navigation |
| [Validator](validator.md) | Validate consistency and integrity |
| [Questions](questions.md) | Escalate blocking uncertainties |

## Authoritative sources

Documentation is generated from:

- `CODEMANIFEST` — cell contract definitions
- `.usages/**/*.md` — usage practice files
- `.tests/**/*.yml` / `.tests/**/*.yaml` — test specifications

## Traceability

Maintains `.goga/tools/mkdocs/traceability.yml` mapping documentation pages to source cell paths.

## Reconciliation

If validation fails, the pipeline re-runs impact analysis through validator (max 2 loops).
