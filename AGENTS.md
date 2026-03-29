# AGENTS (Root Entry, Enforced)

This file is the repository root instruction entrypoint.

## 0) Non-Negotiable Gate: Superpowers Skills First

These rules are mandatory and highest priority inside this repository context:

1. Default: enable and follow `Superpowers skills`.
2. Before approval, execution is blocked:
   - no file edits
   - no implementation commands
   - no implementation-start claims
3. `approval` means explicit user approval to proceed with execution.
4. If uncertain, stay in `Superpowers skills` mode.
5. If this gate is violated, stop immediately and return to `Superpowers skills` mode.

## 1) Load Order Inside This Repo

1. `AGENTS.md` (this file)
2. `specs/AGENT.md`
3. `specs/RULES_INDEX.md`
4. Referenced rule files listed below

## 2) Rule References (Cover All Repo Rules)

Core and workflow:

- `specs/rules/core.md`
- `specs/rules/file-hygiene.md`
- `specs/rules/memory.md`
- `specs/rules/approval-policy.md`

Runtime and references:

- `specs/rules/references/command-allowlist.md`
- `specs/rules/README.md`

Legacy and architecture context:

- `specs/rules-legacy.md`
- `specs/rules-repo-architecture-plan.md`
- `specs/file-index.md`

## 3) Plan-First Compliance Output

Before any implementation action, output a short preflight status:

- `mode=<planning|execution>`
- `plan_trigger=<matched phrase or rule>`
- `next_skill=<brainstorming|writing-plans|executing-plans>`

If `mode=planning`, execution actions are blocked.

## 4) Auto-Injection Experiment Marker

Use this marker to test whether root `AGENTS.md` was auto-injected in a fresh session:

- `AGENTS_ROOT_MARKER=PLAN-FIRST-ENFORCED-20260329`

Expected behavior in a fresh session:

1. User asks for plan first.
2. Assistant should stay in planning mode.
3. Assistant should not perform implementation edits/commands before plan approval.

## 5) Shell Approval Rule (Short)

- For escalated shell commands, request a reusable `prefix_rule` when safe.
