# Command Approval Policy

## Goal

Reduce repeated permission prompts while keeping approvals scoped.

## Rules

- For escalated commands, always request a reusable `prefix_rule` when safe.
- Prefer short, stable prefixes over full command strings.
- Avoid broad prefixes that allow arbitrary scripting.
- If a command is long/complex, store the full example in Layer 2 reference files.
- Prefer category prefixes for daily work (for example: `git add`, `git commit`, `git push`, `Get-Content`).

## Prefix Selection Order

1. Use command-category prefixes first (for example: `git add`, `git commit`, `git push`, `Get-Content`).
2. If category prefix is too broad, use a narrower subcommand prefix.
3. Use full-command prefix only as last resort.
4. After successful approval, prefer adding a reusable prefix rather than another one-off full command.

## Matching Notes (Important)

- Prefix matching works best with simple command forms.
- Commands with heavy shell features (long inline scripts, complex quoting, env-var assignments, redirection) may bypass prefix matching and still prompt.
- To reduce prompts, split workflows into small, plain commands when possible.
- Keep destructive operations intentionally unapproved by default.

## Baseline Prefixes (Recommended)

- PowerShell reads: `Get-ChildItem`, `Get-Content`, `Select-String`
- Git daily flow: `git status`, `git diff`, `git log`, `git add`, `git commit`, `git fetch`, `git pull`, `git push`, `git remote`
- Package/test flow (scoped): `npm install`, `npm run`, `pnpm install`, `pnpm run`, `pytest`

## Anti-Patterns

- Repeatedly approving near-identical full commands with different args.
- Prefixes that effectively allow arbitrary scripting (`python`, `powershell -Command <any>`).
- Hiding multi-step workflows in one long shell line when plain steps are possible.

## Persistence Behavior

- Runtime approvals are stored in: `C:\Users\cuiyi\.codex\rules\default.rules`.
- This repo keeps a versioned mirror at `rules/runtime/default.rules`.
- Recommended setup: keep both files hard-linked so runtime and repo stay in sync.
