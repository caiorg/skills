---
name: autopilot
description: Runs software missions as an evidence-gated closed loop by mapping dependencies, routing GitHub issues with labels, executing directly or coordinating isolated subagents, reviewing, integrating, and repeating to acceptance. Use when asked to autonomously own a software backlog, manage planner-eligible GitHub issues, or replace an external coding orchestrator such as Sandcastle.
---

# Autopilot

Use [the mission contracts](references/mission-contracts.md) for briefs, slices, reviews, and checkpoints. When a mission reads or writes GitHub issues or labels, read [GitHub label routing](references/github-labels.md) before classifying its backlog. Read [recovery](references/recovery.md) only after failure, interruption, or integration conflict. This skill works with the primary agent alone and requires no named agent profile. Generate task-local role prompts from the contracts only when delegation is useful and available.

## 1. Establish the mission

Identify the objective, repository, source of truth, base branch, terminal criteria, permissions, and `HITL` boundaries. Infer only reversible details that preserve scope; ask when a missing choice changes the outcome or authority.

Complete when the mission brief satisfies every field in `Mission brief`.

## 2. Capture current truth

Enumerate mission items from the canonical parent, label, or approved scope. Read applicable `AGENTS.md`, specifications, issue bodies and author updates, repository state, worktrees, CI, tests, planner-facing queries, and only the implementation evidence needed to classify those items. Expand inspection when a classification remains ambiguous. Prefer current evidence over historical completion claims. Record pre-existing user changes and run the required gates on the starting revision. Classify baseline failures separately from regressions; record whether each blocks delivery under the mission policy. A baseline failure is not an automatic waiver of a required gate.

Complete when every mission item is classified as complete with evidence, ready, blocked by named work, or `HITL` for a concrete reason.

## 3. Build the route

Create tracer-bullet slices that each deliver observable behavior. Build an acyclic dependency graph using real issue identifiers when they exist. Separate `AFK` execution from decisions, credentials, hardware, and external validation.

Complete when every required behavior belongs to one slice, every slice has acceptance evidence, and every dependency is explicit.

Obtain user approval before creating issues when the breakdown materially changes scope. Derive label semantics from repository evidence or explicit user direction.

## 4. Dispatch a wave

Choose direct execution for a small slice or tightly coupled work when delegation adds no useful independence. Use an appropriate branch and isolate work when needed to preserve user changes. For parallel execution, select ready slices with non-overlapping ownership and create one isolated worktree and branch per worker. Give each worker its slice contract and task-local evidence. Bound concurrency by ownership, shared resources, client capacity, and coordination cost; retain one primary agent for coordination.

Complete when the implementer, whether the primary agent or a worker, returns the Worker return contract.

## 5. Pass the evidence gate

Review the issue, raw diff, repository rules, and raw validation evidence. Use an independent reviewer when useful and available; otherwise the primary agent performs a separate review pass and records that it was self-reviewed. If the mission explicitly requires independent review, its unavailability blocks that gate. Reproduce failures, stress changed behavior, and report confirmed defects with minimal counterexamples. Keep implementation ownership with the assigned implementer.

Bind the verdict and validation evidence to the exact reviewed revision and tested working-tree state. Changes to that state invalidate affected evidence; rerun affected checks and review the resulting diff before accepting it. Return confirmed defects to implementation with the smallest reproducible counterexample. Report unavailable verification as blocked with the missing evidence and recovery action, never as a pass or a confirmed code defect.

Complete when acceptance criteria and required repository gates pass with exact command or runtime evidence.

## 6. Integrate the wave

Integrate approved slices into the current base in dependency order using the mission's integration policy. Derive the policy from repository history when unambiguous; ask before changing history semantics. Preserve user changes. Resolve conflicts from the specification and current behavior, then rerun combined gates on the integrated result.

Complete when the base contains the approved work, no mission-owned changes remain uncommitted, pre-existing user changes are preserved, and combined validation passes under the agreed gate policy. Bind this evidence to the integrated revision; worker validation alone does not validate integration.

## 7. Checkpoint and loop

Update existing plans, issues, labels, and comments only within granted authority. Record concise status, evidence, remaining blockers, and newly ready work; keep secrets and raw private logs local. After label changes, verify the planner-visible backlog. Re-read current truth and dispatch the next wave.

Complete only when every terminal criterion has evidence and no required work remains. Treat a verified external dependency or missing authority as `HITL`; use the recovery route for every other failure.
