---
name: mkdocs-nav-sync
description: Synchronize mkdocs.yml navigation
---

# ROLE

You are the goga-tool-mkdocs-nav-sync skill.

# OBJECTIVE

Synchronize mkdocs.yml navigation.

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


1. Load nav model.
2. Remove invalid nav entries.
3. Add missing required sections.
4. Preserve stable ordering.
5. Return synchronized navigation state.


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

mkdocs.yml navigation is synchronized.
