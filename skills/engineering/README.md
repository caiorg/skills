# Engineering skills

| Skill | Description |
|---|---|
| [`autopilot`](autopilot/SKILL.md) | Own software missions through dependency routing, direct or delegated execution, review, and evidence tied to the tested revision. |

## Install Autopilot

From a clone of this repository, choose one directory per client:

```bash
mkdir -p ~/.codex/skills
cp -R skills/engineering/autopilot ~/.codex/skills/

# Claude Code, if used:
mkdir -p ~/.claude/skills
cp -R skills/engineering/autopilot ~/.claude/skills/
```

Inspect an existing destination before copying. Preserve local edits with a backup or reconcile the diff first. Copy the entire folder, including `references/`. Avoid installing duplicate copies of `autopilot` in multiple discovery directories for the same client. Codex also supports `~/.agents/skills/`; an existing installation there needs no second copy.

Restart the client session after installation. In Codex, invoke `$autopilot`. In Claude Code, invoke `/autopilot`. Ask the client to identify the loaded `SKILL.md` and resolve its three reference links before starting a mission.

Autopilot requires no Maverick profile, custom agent, or delegation capability. One primary agent can implement, perform a separate self-review, validate, and finish. Independent review remains required when the mission explicitly demands it. GitHub operations require authenticated `gh` access only when the mission uses GitHub. Runtime tools and validation commands come from the target repository.

## Update

In your clean repository clone, fetch the intended published revision, review its changes, and update with `git pull --ff-only` on the default branch after merge. For an unmerged PR, check out its branch explicitly. Compare the installed directory first:

```bash
diff -ru ~/.codex/skills/autopilot skills/engineering/autopilot
```

`diff` exits with status 1 when differences exist. Back up or reconcile local changes, then repeat the installation copy. Check the diff again. If a release removes files, remove only those obsolete files after reviewing them; copying alone does not delete them. Use the corresponding Claude Code path for that installation. Restart the session and repeat the loading check.

## Contracts and validation

[Mission contracts](autopilot/references/mission-contracts.md) define the brief, slice, implementer return, review, and checkpoint. [GitHub routing](autopilot/references/github-labels.md) applies only to issue or label work. [Recovery](autopilot/references/recovery.md) handles interrupted or failed missions.

Review and validation record the SHA plus the tested working-tree state. Changed state invalidates affected evidence. Missing verification produces a blocked verdict; confirmed defects produce failure. Pre-existing failures require an explicit gate policy and never grant an automatic waiver. User changes remain owned by the user during direct work, isolation, and integration.

See the official [Codex skills documentation](https://developers.openai.com/codex/skills) and [Claude Code skills documentation](https://code.claude.com/docs/en/skills) for discovery rules.
