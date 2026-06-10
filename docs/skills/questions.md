# questions

Generate blocking questions required for deterministic execution.

## Role

Identifies unresolved ambiguities that prevent the pipeline from proceeding and escalates them to the user.

## Workflow

1. Analyze unresolved ambiguities
2. Detect blocking uncertainties
3. Generate concise blocking questions
4. Return escalation output

## When it runs

Invoked when the pipeline encounters situations that cannot be resolved deterministically — for example, missing authoritative sources or conflicting configurations.

## Output

Returns a list of blocking questions that must be answered before execution can continue.