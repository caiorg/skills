# Recovery

Read this file after failure, interruption, or integration conflict.

## Resume from current truth

Re-read the mission sources, `git status`, worktrees, branches, issue state, and latest validation. Reconstruct state from evidence instead of conversation memory. Preserve dirty or unmerged work until ownership is known.

Resume when each existing artifact is mapped to a slice or explicitly excluded.

## Classify failure

- `implementation`: a reproducible behavior or test fails
- `validation`: required evidence is missing or ambiguous
- `environment`: tooling, service, network, or runtime is unavailable
- `integration`: individually valid slices conflict when combined
- `authority`: progress requires permission or a user decision

Complete classification when one category is supported by exact evidence.

## Change route

For implementation failure, return the smallest counterexample to the owning implementer, including the primary agent. For validation failure, run the missing observable gate. For environment failure, use an equivalent supported environment or request the required external change. For integration failure, reconcile in dependency order and rerun combined gates. For authority failure, present the minimal decision or permission needed.

After the same blocking condition appears three consecutive times, change strategy before another attempt. Mark `HITL` only when safe in-scope alternatives are exhausted and the missing input is external to the mission.

Recovery completes when execution resumes on a new evidenced route or a precise `HITL` boundary is reported.
