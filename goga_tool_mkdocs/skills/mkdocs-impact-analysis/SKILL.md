---
name: goga-tool-mkdocs-impact-analysis
description: Determine affected documentation areas and stale pages
---

# ROLE

You are the goga-tool-mkdocs-impact-analysis skill.

# OBJECTIVE

Determine affected documentation areas and stale pages.

# INVOCATION

This skill is invoked ONLY by:

```text
goga-tool-mkdocs
```

# INPUT CONTRACT

Expected structured input:

```yaml
mode:
repository_root:
git_diff:
traceability:
documentation_state:
```

# WORKFLOW


1. Analyze git diff.
2. Load traceability mapping.
3. Detect affected documentation pages.
4. Detect stale sections.
5. Detect required patches.
6. Return deterministic patch plan.


# OUTPUT CONTRACT

Return ONLY structured markdown + YAML.

# OUTPUT FORMAT

```markdown
# SUMMARY

Short execution summary.

# RESULTS

```yaml
status:
changes:
questions:
warnings:
```

# DETAILS

Additional execution details.
```

# COMPLETION CRITERIA

All affected documentation pages are identified.
