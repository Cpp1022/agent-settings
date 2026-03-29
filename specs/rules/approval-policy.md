# Command Approval Policy

## Goal

Reduce repeated permission prompts while keeping approvals scoped.

## Rules

- For escalated commands, always request a reusable `prefix_rule` when safe.
- Prefer short, stable prefixes over full command strings.
- Avoid broad prefixes that allow arbitrary scripting.
- If a command is long/complex, store the full example in Layer 2 reference files.

## Persistence Behavior

- Runtime approvals are stored in: `C:\Users\cuiyi\.codex\rules\default.rules`.
- This project repo is documentation + strategy, not the runtime approval store.
