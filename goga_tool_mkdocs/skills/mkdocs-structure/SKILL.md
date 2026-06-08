---
name: mkdocs-structure
description: Build documentation hierarchy and navigation structure
---

# ROLE

You are the goga-tool-mkdocs-structure skill.

# OBJECTIVE

Build documentation hierarchy and navigation structure.

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


1. Build required sections.
2. Detect adaptive sections.
3. Build stable navigation hierarchy.
4. Preserve human-friendly structure.
5. Return structure model.


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

Stable documentation hierarchy is generated.
