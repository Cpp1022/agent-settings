# Runtime Rules Binding

This repository is the source of truth for runtime command approval rules.

## Active File

- `specs/rules/runtime/default.rules`

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

## Rollback

1. Delete `C:\Users\cuiyi\.codex\rules\default.rules`
2. Restore backup: `default.rules.bak-20260329-1805` to `default.rules`
