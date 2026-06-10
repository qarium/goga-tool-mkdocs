# impact-analysis

Determine affected documentation areas and stale pages.

## Role

Analyzes changes (git diff) against the traceability mapping to identify which documentation pages need updating.

## Workflow

1. Analyze git diff
2. Load traceability mapping
3. Detect affected documentation pages
4. Detect stale sections
5. Detect required patches

## When it runs

Only in **incremental** mode and during reconciliation loops. Not part of the bootstrap pipeline.

## Output

Returns a deterministic patch plan listing affected pages, stale sections, and required patches.