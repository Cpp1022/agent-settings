# Worktree Location Rule

## Default

- Use external worktrees: `<HOME>/worktrees/<repo>/`.

## Platform Mapping

- Windows: `%USERPROFILE%\worktrees\<repo>\`
- macOS/Linux: `~/worktrees/<repo>/`

## Conflict Handling

- If `<repo>` conflicts, use `<repo>-<owner>`.

## Command Safety

- Always quote path arguments in shell commands.
