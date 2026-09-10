# GitHub label routing

Read this file only when a mission uses GitHub issues or labels. Use `gh` and the repository's actual conventions.

## Discover the protocol

- Read `AGENTS.md`, planner configuration, issue templates, contributing docs, existing labels, and representative issues.
- Find the exact planner-facing query when one exists.
- Classify existing labels as routing, execution (`AFK` or `HITL`), descriptive, or lifecycle labels.
- Use names such as `Sandcastle`, `Autopilot`, `AFK`, `HITL`, and `phase:*` only when repository evidence defines them.
- Ask one focused question when repository evidence does not establish the routing protocol.

Complete when the exact planner query and every managed label's semantics have a cited repository source or explicit user decision.

## Plan the delta

For every issue, record current labels, intended labels, reason, and authority. Add a routing label only when the issue is open, in approved scope, dependency-ready, has testable acceptance criteria, and needs no human decision during execution.

Keep `HITL`, blocked, ambiguous, duplicate, and complete work outside the automatic route. Use transient lifecycle labels only when the repository defines their transitions and owner.

Complete when every issue has current labels, intended labels, eligibility evidence, reason, and mutation authority.

## Mutate safely

- Preview exact label creation, addition, and removal before writing unless the mission already grants that authority.
- Reuse existing labels; create only missing labels explicitly required by the confirmed protocol.
- Apply only the computed delta. Re-running the operation must produce no further changes.
- Preserve unrelated labels and user changes.
- Keep requirements and dependencies explicit in issue bodies; use labels only for their confirmed routing or classification role.

Complete when the observed labels match the computed delta and repeating it produces no change.

## Complete the lifecycle

Keep routing labels aligned with planner eligibility. After approved work is integrated and combined gates pass, follow the repository's established policy to remove routing labels or close issues.

Complete when each integrated issue has the repository-defined terminal label and state.

## Verify visibility

Re-run the repository's planner-facing query after every mutation. Confirm that it returns exactly the intended automatic backlog, excludes every `HITL` issue, and contains every eligible issue. Reconcile any mismatch before dispatch.

Complete when the query result equals the intended issue-number set.
