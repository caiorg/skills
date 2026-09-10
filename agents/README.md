# Agents

| Profile | Dependency | Purpose |
|---|---|---|
| [Maverick](maverick/agent.md) | [Autopilot](../skills/engineering/README.md) | Adds mission judgment and concise communication to Autopilot. |

Maverick is a portable instruction profile. Its `id`, `name`, `description`, and `enabled` frontmatter describes the source profile; it is not a universal client registration format. Autopilot owns workflow, contracts, gates, and recovery. Install Autopilot first.

## Install and use Maverick

From this repository:

```bash
mkdir -p ~/.agents/agents/maverick
cp agents/maverick/agent.md ~/.agents/agents/maverick/agent.md
```

Inspect and back up an existing destination before copying. This stores the profile; it does not register it automatically. In Codex or another client with local file access, begin the mission with:

```text
Read ~/.agents/agents/maverick/agent.md and apply Maverick to this mission.
Activate the installed autopilot skill and its required references.
Mission: <objective, repository, acceptance criteria, and permissions>.
```

Confirm that the client read both files before execution. Do not assume it loads `~/.agents/AGENTS.md` or discovers this agent directory. No model is pinned. This explicit loading route keeps Maverick usable as the primary agent without a client-specific subagent configuration.

### Claude Code registration

Claude Code supports named agents in `~/.claude/agents/`. Generate its native frontmatter from the canonical profile, preserving one source for the body. This command refuses to overwrite an existing agent. For updates, follow the backup and regeneration steps below before running it again.

```bash
mkdir -p ~/.claude/agents
python3 - <<'PY'
from pathlib import Path
source = Path('agents/maverick/agent.md').read_text()
body = source.split('---', 2)[2].lstrip()
target = Path.home() / '.claude/agents/maverick.md'
with target.open('x') as out:
    out.write('---\nname: maverick\n')
    out.write('description: Own approved software missions using Autopilot.\n')
    out.write('skills:\n  - autopilot\n---\n\n' + body)
PY
claude --agent maverick
```

The native `skills` field preloads Autopilot. The profile also requires its references. There is no model or tool restriction override. Use `--agent maverick` as the main session for missions that may delegate; Claude Code subagents cannot spawn further subagents. See [Claude Code agent configuration](https://code.claude.com/docs/en/sub-agents).

## Update

Update your repository clone to the intended revision as described in [Autopilot updates](../skills/engineering/README.md#update). Review `diff -u ~/.agents/agents/maverick/agent.md agents/maverick/agent.md`, preserve local edits, and repeat the profile copy. Update Autopilot with it. For Claude Code, review local edits and move `~/.claude/agents/maverick.md` to an unused backup path outside `~/.claude/agents/`. Moving preserves the old adapter and frees the destination required by `target.open('x')`; copying a backup alone does not. Confirm the original path no longer exists, then rerun the registration command above to regenerate the adapter from the updated profile. Start a new session and verify that Maverick and Autopilot resolve to the updated files.

## Optional writing skill

`unslop` is a third-party writing skill, not a dependency of either profile or workflow. It is not bundled here. Install it separately from its upstream source if desired. Global writing preferences belong in each client's documented personal configuration and are not part of this repository.
