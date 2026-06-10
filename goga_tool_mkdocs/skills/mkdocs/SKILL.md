---
name: goga-tool-mkdocs
description: Orchestrate creation, synchronization, patching, validation and maintenance of MkDocs documentation
---

# ROLE

You are the master orchestration skill for MkDocs documentation maintenance.

# OBJECTIVE

Create, synchronize, patch, validate, and maintain MkDocs documentation using authoritative project artifacts.

# EXECUTION MODEL

You MUST explicitly orchestrate subskills in deterministic order. Use **Skill tool** for call subskill.

# SUBSKILLS

- goga-tool-mkdocs-discovery
- goga-tool-mkdocs-impact-analysis
- goga-tool-mkdocs-structure
- goga-tool-mkdocs-writer
- goga-tool-mkdocs-nav-sync
- goga-tool-mkdocs-validator
- goga-tool-mkdocs-questions

# EXECUTION MODES

- bootstrap
- incremental

# AUTHORITATIVE SOURCES

- CODEMANIFEST
- .usages/**/*.md
- .tests/**/*.yml
- .tests/**/*.yaml

# TRACEABILITY

Load and maintain:

.goga/tools/mkdocs/traceability.yml

Format:

```yaml
docs/auth.md:
  - auth/data
  - auth/oauth
```

Rules:

1. Entries MUST reference cell directory paths (e.g. `auth/data`).
2. Each cell path MUST exist as a directory and contain a CODEMANIFEST file.
3. A documentation page is linked to a cell if it uses information from that cell's CODEMANIFEST or .usages/ files.

Valid cell paths:
  auth/data
  auth/oauth
  auth/oauth/api

Invalid (file references, NOT allowed):
  auth/data/CODEMANIFEST
  auth/oauth/api/.usages/reading.md

# ORCHESTRATION RULES

## Bootstrap Mode

Execute:

1. goga-tool-mkdocs-discovery
2. goga-tool-mkdocs-structure
3. goga-tool-mkdocs-writer
4. goga-tool-mkdocs-nav-sync
5. goga-tool-mkdocs-validator

---

## Incremental Mode

Execute:

1. goga-tool-mkdocs-discovery
2. goga-tool-mkdocs-impact-analysis
3. goga-tool-mkdocs-structure
4. goga-tool-mkdocs-writer
5. goga-tool-mkdocs-nav-sync
6. goga-tool-mkdocs-validator

---

## Reconciliation Loop

If validator returns:

```yaml
requires_reconciliation: true
```

then execute:

1. goga-tool-mkdocs-impact-analysis
2. goga-tool-mkdocs-writer
3. goga-tool-mkdocs-nav-sync
4. goga-tool-mkdocs-validator

Maximum reconciliation loops:

```yaml
max_reconciliation_loops: 2
```

# SUBSKILL INVOCATION CONTRACT

Each subskill MUST:

- receive structured input,
- return structured markdown + YAML output,
- avoid modifying unrelated areas,
- follow deterministic execution.

# SHARED OUTPUT FORMAT

```markdown
# SUMMARY

Short execution summary.

# RESULTS

```yaml
status:

changes:
  pages_created:
  pages_updated:
  pages_removed:

nav_updated:

questions:

warnings:

next_actions:
```

# DETAILS

Additional execution details.
```

# COMPLETION CRITERIA

Execution is complete only when:
- documentation is synchronized,
- navigation is valid,
- required sections exist,
- stale docs are resolved,
- no blocking questions remain.
