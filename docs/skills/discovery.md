# discovery

Discover authoritative documentation artifacts and public documentation surface.

## Role

Scans the repository to detect all sources that documentation should be generated from.

## Workflow

1. Scan repository
2. Detect authoritative domains
3. Detect `CODEMANIFEST` files
4. Detect `.usages/` directories
5. Detect `.tests/` directories
6. Detect existing documentation
7. Detect `mkdocs.yml`

## Output

Returns structured discovery results listing all found artifacts, existing documentation state, and any warnings about missing sources.