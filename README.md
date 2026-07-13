# skills

Agent Skills ([agentskills.io](https://agentskills.io)) — portable across Claude Code, Claude.ai, Codex CLI, Gemini CLI, Cursor, Antigravity and other compatible agents.

## Skills

| Skill | Description |
|---|---|
| [`print-art-prompt`](skills/print-art-prompt/SKILL.md) | Guided interview that produces a print-ready image-generation prompt for playmats, mousepads, and posters. |

## Install

Copy the skill folder into your agent's skills directory, e.g.:

```bash
cp -r skills/print-art-prompt ~/.claude/skills/   # Claude Code
cp -r skills/print-art-prompt ~/.codex/skills/    # Codex CLI
cp -r skills/print-art-prompt ~/.gemini/skills/   # Gemini CLI
```

Or symlink everywhere at once with [`npx skills add`](https://skills.sh).
