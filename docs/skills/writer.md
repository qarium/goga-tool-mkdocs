# writer

Create and patch markdown documentation content.

## Role

Generates new documentation pages and updates existing ones based on the structure model and patch plan.

## Workflow

1. Load patch plan
2. Load structure model
3. Patch stale sections
4. Create missing sections
5. Synchronize examples
6. Synchronize configuration docs

## Output

Returns updated documentation state with lists of created, updated, and removed pages.