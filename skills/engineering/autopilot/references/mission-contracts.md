# Mission contracts

## Mission brief

- Objective and explicit exclusions
- Repository and current base branch
- Integration policy derived from repository convention or user direction
- Canonical specifications and parent issue
- Terminal criteria
- Allowed local and external mutations
- `HITL` boundaries
- Required validation gates and explicit policy for pre-existing failures
- Starting revision, working-tree state, and ownership of pre-existing changes

## Slice contract

- Real issue identifier or temporary symbolic name
- One observable behavior
- In-scope and out-of-scope boundaries
- Canonical source references
- Blocking dependencies
- Acceptance criteria
- Required tests and runtime evidence
- Execution owner, branch, and worktree; isolation decision for direct execution

## Worker return

Used by the primary agent during direct execution and by delegated workers.

- Outcome: `complete`, `failed`, or `blocked`
- Commits created and exact tested revision (`SHA`)
- Tested working-tree state, including any uncommitted mission changes
- Exact commands executed and results
- Runtime probes when applicable
- Remaining gaps or blocker evidence
- Files intentionally left unchanged when relevant

## Review gate

- Reviewer identity and review mode: independent or self-reviewed

- Acceptance criterion mapped to evidence
- Regression and edge-case attempts
- Security and tenant-boundary checks when applicable
- Required repository commands
- Reviewed revision (`SHA`) and tested working-tree state
- Baseline failures versus regressions, with the agreed gate policy applied
- Verdict: `pass`, `fail` for confirmed defects or unmet criteria, or `blocked` for unavailable verification
- Missing evidence and recovery action for a blocked verdict
- Minimal counterexample for every failure

## Checkpoint

- Integrated slices and commits
- Integrated revision and validation summary, including baseline exceptions explicitly authorized by the mission policy
- Current blockers
- Newly ready slices
- Remaining terminal criteria

Use GitHub and the active task plan as durable state when available. Add repository state files only when the user explicitly requests them.
