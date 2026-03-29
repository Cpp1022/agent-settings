# Runtime Rules Binding

This repository is the source of truth for runtime command approval rules.

## Active File

- `rules/runtime/default.rules`

## Live Codex Path

- `C:\Users\cuiyi\.codex\rules\default.rules`

## Binding Mode

- Windows hard link (same underlying file)

## Why

- Keep rules versioned in repo
- Reuse across IDE sessions by sharing the same file
- Avoid duplicating manual edits

## Verify

Run:

```powershell
cmd /c fsutil hardlink list "$env:USERPROFILE\.codex\rules\default.rules"
```

You should see both paths.

## Re-Link (If Drift Happens)

If hashes differ or hardlink list shows only one path, re-link:

```powershell
$repo = "C:\项目\agent-settings\rules\runtime\default.rules"
$live = "$env:USERPROFILE\.codex\rules\default.rules"
if (Test-Path -LiteralPath $live) { Remove-Item -LiteralPath $live -Force }
New-Item -ItemType HardLink -Path $live -Target $repo | Out-Null
```

Then verify again with `fsutil hardlink list`.

## Rollback

1. Delete `C:\Users\cuiyi\.codex\rules\default.rules`
2. Restore backup: `default.rules.bak-20260329-1805` to `default.rules`
