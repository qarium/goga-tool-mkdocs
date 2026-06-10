# Pipeline

The mkdocs tool executes a deterministic pipeline of subskills. The pipeline order differs between execution modes.

## Traceability

The tool maintains `.goga/tools/mkdocs/traceability.yml` — a mapping from documentation pages to source cell paths:

```yaml
docs/auth.md:
  - auth/data
  - auth/oauth
```

Rules:

- Entries reference cell directory paths (e.g. `auth/data`), not files
- Each cell path must exist as a directory with a `CODEMANIFEST` file
- A page is linked to a cell if it uses information from that cell's `CODEMANIFEST` or `.usages/` files

## Bootstrap mode

Used when no prior documentation state exists.

```
1. Discovery       — scan project for authoritative sources
2. Structure       — build documentation hierarchy
3. Writer          — create documentation content
4. Nav Sync        — generate mkdocs.yml navigation
5. Validator       — validate consistency and integrity
```

## Incremental mode

Used when documentation already exists. Adds impact analysis to detect what changed.

```
1. Discovery       — scan project for authoritative sources
2. Impact Analysis — detect affected and stale documentation pages
3. Structure       — update documentation hierarchy
4. Writer          — patch stale sections, create missing ones
5. Nav Sync        — update mkdocs.yml navigation
6. Validator       — validate consistency and integrity
```

## Reconciliation loop

If the validator returns `requires_reconciliation: true`, the pipeline re-runs a subset:

```
1. Impact Analysis
2. Writer
3. Nav Sync
4. Validator
```

Maximum reconciliation loops: **2**.

## Completion criteria

The pipeline is complete when:

- Documentation is synchronized with authoritative artifacts
- Navigation is valid
- Required sections exist
- Stale docs are resolved
- No blocking questions remain