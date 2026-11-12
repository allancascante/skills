---
name: integrate-and-report
description: "Integrate verified task work and produce an evidence-based progress report. Use when closing a development task, deciding readiness to merge, updating a delivery tracker, triaging test failures, or selecting the next eligible task."
---

# Integrate and report

Separate implementation, local verification, integration, and post-integration verification. Never turn an unverified claim into DONE.

## Procedure

Before writing, resolve tracker, evidence, and summary paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, record task status and evidence in `docs/IMPLEMENTATION-TASKS.md` with capability summaries in `README.md`, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect the tracker, selected scenario matrix, actual evidence, branch/worktree status, and project policies. Identify unrelated or uncommitted changes and protect them. Check that task prerequisites, acceptance criteria, and required approvals are satisfied.
2. Review the actual diff and requirement-to-test mapping. Confirm targeted, regression, quality, coverage, and applicable environment checks ran successfully at the required boundary. Note red-green evidence where required, not just the presence of tests.
3. Investigate unexpected failures promptly. Distinguish product, test, and environment causes only as evidence supports. Keep failing cases and exclusions visible; do not classify a failure as harmless or omit it without evidence and the owner's decision.
4. If checks or approvals are missing, record BLOCKED or PARTIAL/DOING and identify precisely what remains. Propose options for any material scope change; only the owner can approve it, and associated contracts and claims must be updated.
5. When authorized, follow the repository's non-destructive commit and integration workflow. Commit only intended changes; do not merge, tag, push, or alter unrelated work without the applicable permission. Record revision identifiers and integration outcome.
   Apply the team's confirmed commit cadence. If undefined, recommend and seek confirmation of a task completion commit after each verified plan task, before starting the next task; accept the user's alternative internal practice. Under that policy, include the task ID, intended implementation/tests/docs and evidence, and record its commit in the tracker. A task-boundary commit does not replace review, integration, or post-integration checks, and does not by itself make the task DONE.
6. Run the project's required checks against the actual integrated revision, including full-suite gates when specified. If integration or a post-integration gate fails, report it and keep status accurate. A pre-integration pass is not proof that the integrated revision passed.
7. Update the tracker and report completed work, exact validation results and environments, outstanding failures and blockers, and the next dependency-ready task. For percentages, show the numerator, denominator, and status definition; do not count PARTIAL or BLOCKED as DONE.

## Integration record

- Task, scope, and contract/scenario IDs
- Baseline, task revision, integration revision, and approvals
- Commands, actual results, coverage measurement, and environment matrix
- Failed, blocked, skipped, and out-of-scope cases with reasons
- Current task status and next ready action

## Done when

Required integration and post-integration checks have actually passed and are recorded, or the remaining blocker and non-DONE status are explicit.
