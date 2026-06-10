# Getting Started

## Installation

```bash
pip install goga-tool-mkdocs
```

## Connect to agent

Install skills into a Goga agent:

```bash
goga connect <agent>
```

## Requirements

- Python 3.10+
- Goga CLI

## Usage

Run the tool from a Goga project root:

```bash
/goga:tool mkdocs
```

The tool detects the execution mode automatically:

- If no prior documentation state exists (no `mkdocs.yml`, no `docs/`), it runs in **bootstrap** mode
- If documentation already exists, it runs in **incremental** mode and patches only affected areas

## Project setup

For the tool to produce documentation, your project should contain at least one of:

- `CODEMANIFEST` files in cell directories
- `.usages/` directories with practice files
- `.tests/` directories with test specifications

## Output

The tool generates:

- `docs/` directory with markdown pages
- `mkdocs.yml` with navigation
- `.goga/tools/mkdocs/traceability.yml` linking docs to source cells
