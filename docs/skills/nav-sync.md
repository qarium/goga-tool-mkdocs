# nav-sync

Synchronize mkdocs.yml navigation.

## Role

Updates the `mkdocs.yml` navigation tree to reflect the current documentation structure.

## Workflow

1. Load navigation model
2. Remove invalid navigation entries
3. Add missing required sections
4. Preserve stable ordering

## Output

Returns synchronized navigation state indicating what was added, removed, or reordered.