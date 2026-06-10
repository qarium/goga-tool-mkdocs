# validator

Validate documentation consistency and integrity.

## Role

Checks the generated documentation for errors, stale content, and structural problems.

## Workflow

1. Validate links
2. Validate navigation
3. Validate traceability format
4. Detect stale docs
5. Detect orphan pages
6. Detect missing required sections
7. Determine reconciliation necessity

## Reconciliation

If validation finds issues, it returns `requires_reconciliation: true` to trigger the reconciliation loop.

## Output

Returns validation results with status, warnings, and whether reconciliation is needed.