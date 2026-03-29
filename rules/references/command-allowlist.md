# Command Allowlist References

Use ids from this file when a command example is too long for inline rules.

## CMD-001

- Purpose: install oh-my-opencode via bun with fixed flags
- Preferred short form:
  `& "$env:USERPROFILE\.bun\bin\bun.exe" x oh-my-opencode install --no-tui --claude=no --openai=no --gemini=no --copilot=no --opencode-zen=no --zai-coding-plan=no --kimi-for-coding=no --opencode-go=no --skip-auth`
- Note: avoid `$env:Path=...;` prefix to reduce split-segment prompt behavior.
