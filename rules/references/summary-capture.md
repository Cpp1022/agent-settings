# Summary Capture Rule

1. After each non-trivial task, generate separate Knowledge and Skill drafts.
2. Knowledge draft fields: fact, evidence, scope, confidence.
3. Skill draft fields: trigger, steps, checks, fallback.
4. Do not persist Knowledge or Skill without explicit user confirmation.
5. If spot-check fails, report immediately and request user action in the same turn.
6. If unresolved, mark `REVIEW_REQUIRED` and remind at each later task start until user explicitly clears it.
