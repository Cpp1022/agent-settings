# File Hygiene

## Directory Convention

- experiments/<idea-id>/ : temporary scripts and outputs for one idea
- memory/ : durable state and decisions
- rules/ : stable rule docs
- process/archive/ : deprecated but traceable files

## Isolation Policy

- One idea -> one worktree
- One worktree -> one experiments/<idea-id>/ folder
- Do not mix scripts from different ideas in root

## Index Sync Policy

When files are added/moved/deleted, update index docs in same task:

1. docs-level TOC (DocToc if used)
2. project-level INDEX doc (recommended: generated script)

## Keep/Archive/Drop

After each experiment:

- keep: move to stable path + add short usage note
- archive: move to process/archive with reason
- drop: delete only if explicitly approved
