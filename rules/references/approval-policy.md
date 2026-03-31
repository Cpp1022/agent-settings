# Command Approval Policy

## Goal

Default-pass non-destructive work. Ask approval only for delete/destructive actions.

## Rules

- For escalated commands, request reusable `prefix_rule` for non-destructive categories first.
- Keep read/write/dev prefixes pre-approved in `rules/runtime/default.rules`.
- Do not pre-approve delete/destructive commands.
- Use short, stable prefixes instead of full command strings.
- Split complex shell lines into simple commands to improve prefix matching.
- In aggressive mode, prefer toolchain-wide non-delete prefixes to minimize prompts.

## Prefix Selection Order

1. Use command-category prefixes for non-destructive work.
2. If category prefix is too broad, narrow by subcommand.
3. Use full-command prefix only as last resort.
4. Keep delete/destructive operations outside the baseline.

## Matching Notes (Important)

- Prefix matching works best with simple command forms.
- Heavy shell features can bypass matching and still prompt.
- Split workflows into small plain commands.
- Never hide delete/destructive behavior in long one-liners.

## Baseline Prefixes (Recommended)

- PowerShell read: `Get-ChildItem`, `Get-Content`, `Select-String`, `Get-Item`, `Test-Path`, `Resolve-Path`, `Get-FileHash`
- PowerShell write (non-delete): `New-Item`, `Copy-Item`, `Move-Item`, `Rename-Item`, `Set-Content`, `Add-Content`
- Git flow: `git status`, `git diff`, `git log`, `git add`, `git commit`, `git fetch`, `git pull`, `git push`, `git remote`, `git branch`, `git checkout`, `git switch`, `git merge`, `git rebase`, `git cherry-pick`, `git tag`, `git stash`
- Package/test flow: `npm install`, `npm run`, `pnpm install`, `pnpm run`, `yarn install`, `yarn run`, `bun install`, `bun run`, `pytest`

## Aggressive Mode (Current)

- Runtime baseline is intentionally broad for non-delete work to reduce repeated approval friction.
- This includes toolchain-wide prefixes such as `npm`, `pnpm`, `yarn`, `bun`, `node`, `python`, `pip`, `go`, `cargo`, `dotnet`, `mvn`, `gradle`, `cmake`, `make`.
- Keep delete/destructive commands outside baseline even in aggressive mode.

## Reliability Boundary

- Prefix rules cannot perfectly infer intent for script-driven actions.
- If a broad toolchain command executes internal deletion, approval prompts may not trigger.
- Operational safeguard: agent must still request explicit user confirmation before intentional delete/destructive actions.

## Delete/Destructive Gate

- Always ask explicit user approval for delete/destructive actions.
- Examples: `Remove-Item`, `del`, `rd`, `rmdir`, `git clean`, `git reset --hard`, forced branch delete, task/service/process hard-kill.
- If user approves, prefer a scoped prefix (path + command family) instead of global delete permission.
- If user rejects, stop and ask for an alternative.

## Anti-Patterns

- Repeatedly approving near-identical full commands with different args.
- Prefixes that effectively allow arbitrary scripting (`python`, `powershell -Command <any>`).
- Hiding multi-step workflows in one long shell line when plain steps are possible.
- Pre-approving delete/destructive commands in baseline runtime rules.

## Persistence Behavior

- Runtime approvals are stored in: `C:\Users\cuiyi\.codex\rules\default.rules`.
- This repo keeps a versioned mirror at `rules/runtime/default.rules`.
- Recommended setup: keep both files hard-linked so runtime and repo stay in sync.
