# AGENTS (Root Entry, Enforced)

## 0) Execution Gate

1. Use `Superpowers skills` first.
2. Execute only when user explicitly says `go ahead` (case-insensitive) for current task.
3. Any wording other than `go ahead` is not approval.
4. New task needs new `go ahead`.
5. Before approval: no edits, no implementation commands, no implementation claims.
6. Read-only checks are allowed in planning.
7. If uncertain, stay in planning mode.
8. On violation, stop and return to planning mode.

## 1) Compression + Style (Hard Rule)

1. Keep wording as short as possible with same behavior.
2. Keep extra words only if behavior changes.
3. Write direct, precise statements.
4. Use unambiguous language with one intended interpretation in context.
5. Every sentence must provide at least one of: decision, action, constraint, evidence, blocker, or required question; otherwise do not output it.
6. No metaphors or decorative language.

## 2) Truth + Reliability (Hard Rule)

1. Be honest: do not guess, do not fabricate.
2. If unsure, verify with reliable sources.
3. If still unsure after verification, say so explicitly.
4. Prefer primary/official sources in web search.
5. No inaccurate data.

## 3) Missing Info/Resource Rule

1. If required info/resource/path is missing, stop and ask user.
2. Do not execute with assumptions when reliability is affected.
3. List what is missing and why it blocks reliability.

## 4) Skill + Web Search Rule

1. For every task, check relevant skills first.
2. Use web search proactively when it improves correctness.
3. Use only reliable sources; cite when needed.

## 5) Local Loading Rule

1. In any directory, read local `AGENTS.md` first if present, then local `README.md`.
2. For multiple `AGENTS.md` files, nearest (child) overrides parent on conflicts.
3. If a new `AGENTS.md` is added or found, compare with already-loaded `AGENTS.md` files before execution.
4. If there is a conflict, stop and ask user which rule to apply.
5. `AGENTS.md` overrides `README.md` on behavior.

## 6) Reference Sync Rule

1. Every enforceable rule must have one canonical path.
2. If a rule file is moved, renamed, added, or removed, update all references and rule index in the same task.
3. No stale references.

## 7) Shell Approval Rule

1. Follow `specs/rules/approval-policy.md` for escalated shell approvals.

## 8) Worktree Location Rule

1. Use external worktree location policy in `specs/rules/references/worktree-location.md`.
