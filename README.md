# skills

Agent Skills ([agentskills.io](https://agentskills.io)) — portable across Claude Code, Claude.ai, Codex CLI, Gemini CLI, Cursor, Antigravity and other compatible agents.

## Categories

- [Creativity](skills/creativity/README.md)
- [Engineering](skills/engineering/README.md)

## Agents

- [Maverick](agents/README.md): mission judgment and communication, powered by Autopilot.

Agent profiles have client-specific loading rules. See the linked installation guides.

## Install

Copy a skill folder into your agent's skills directory, e.g.:

```bash
cp -r skills/creativity/print-art-prompt ~/.claude/skills/   # Claude Code
cp -r skills/creativity/print-art-prompt ~/.codex/skills/    # Codex CLI
cp -r skills/creativity/print-art-prompt ~/.gemini/skills/   # Gemini CLI
```
