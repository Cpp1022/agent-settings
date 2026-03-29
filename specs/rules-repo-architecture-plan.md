# Rules Repository Architecture Plan (v1)

## 1. Goals

- Use this repository as the single source of truth for agent rules.
- Reuse one core rule set across Codex/Cursor/Claude/OpenCode.
- Keep context token usage low with layered references.
- Support plan-first workflow by default.

## 2. Proposed Structure

```text
agent-settings/
  specs/
    AGENT.md                     # minimal entrypoint
    RULES_INDEX.md               # top-level index
    rules/
      core.md                    # universal hard constraints
      file-hygiene.md            # file organization + index policy
      memory.md                  # durable memory rules
    adapters/
      codex.md                   # Codex-specific mapping
      cursor.md                  # Cursor-specific mapping
      claude-code.md             # CLAUDE.md mapping
      opencode.md                # OpenCode mapping
  sync/
    mappings.example.json        # source -> target locations
    sync-rules.ps1               # distribute rendered rules
  memory/
    PROJECT_STATE.md
    DECISIONS.md
    EXPERIMENTS.md
```

## 3. Distribution Strategy (Cross IDE)

- Author only in `specs/rules/*` and `specs/adapters/*`.
- Use `sync/sync-rules.ps1` to render/copy into each tool format:
  - Codex target: project `AGENTS.md` or tool-specific instruction file.
  - Cursor target: `.cursor/rules/*.mdc`.
  - Claude Code target: `CLAUDE.md`.
  - OpenCode target: config/instruction file per OpenCode docs.
- Keep generated targets thin; include pointers to core sections.

## 4. Low-Token Principles

- Keep `AGENT.md` < 80 lines.
- Put details in leaf files under `specs/rules/`.
- For each session, load only required leaf files.
- Avoid repeating policy text in multiple files.

## 5. Planning Policy

- Default: `Superpowers skills` before execution.
- Execution requires explicit user approval to proceed.
- If uncertain, stay in `Superpowers skills` mode.

## 6. Known Risks

- Drift risk: one tool updates local rules but source repo not updated.
  - Mitigation: sync script one-way from source repo only.
- Overload risk: too many global rules degrade quality.
  - Mitigation: strict layering + scope tags + periodic pruning.
- Compatibility risk: each IDE has different rule injection behavior.
  - Mitigation: adapter files per IDE with automated checks.

## 7. Rollout Steps

1. Freeze source schema (rules + adapters).
2. Implement sync script with dry-run and diff output.
3. Connect one IDE first (Codex), verify behavior for 1 week.
4. Add Cursor and Claude Code.
5. Add OpenCode last (after host installation and config validation).
