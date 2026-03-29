# Skill: Design Agent Rules System

- Trigger: when creating or refactoring agent rules and index structure.
- Steps:
  1. Keep `AGENTS.md` as the single root entry.
  2. Maintain `RULES_INDEX.md` as the canonical rule loading index.
  3. Maintain `FILE_INDEX.md` as the repository file index.
  4. Keep concise active rules in `rules/` and detailed rules in `rules/references/`.
  5. Keep runtime rule assets in `rules/runtime/`.
  6. Move deprecated or historical docs to `archive/`.
- Notes:
  - Apply compression-first writing; keep rules executable and unambiguous.
  - When files move, update references and indexes in the same task.
  - If rule precedence is uncertain, stop and ask the user.
- Related Files:
  - `AGENTS.md`
  - `RULES_INDEX.md`
  - `FILE_INDEX.md`
  - `rules/`
