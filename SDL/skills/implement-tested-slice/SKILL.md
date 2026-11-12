---
name: implement-tested-slice
description: "Implement an eligible software task in small test-driven slices. Use when coding from a specification and test catalog, fixing a regression, or continuing a tracked implementation with red-green-refactor and explicit evidence."
---

# Implement a tested slice

Implement a ready task against its contract and scenario matrix. Preserve unrelated work and existing behavior.

## Procedure

Before writing, resolve guide, tracker, catalog, and contract paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `CONTRIBUTING.md`, `docs/CODING.md`, `docs/TESTING.md`, `docs/IMPLEMENTATION-TASKS.md`, `docs/TEST-CATALOG.md`, and `docs/specs/SPECIFICATION.md`, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect project instructions, tracker, approved contract, relevant existing code/tests, repository status, dependencies, and catalog scenarios. Verify prerequisites, scope, and available environments. If a necessary decision is unresolved, ask rather than inventing behavior.
   If coding or testing standards are missing, collect supplied guides or agree the rigor and coverage policy using `establish-coding-standards` and `establish-testing-standards` when available. Otherwise ask directly. Do not infer approved thresholds or analyzer strictness from examples.
2. Record the selected scenario IDs and exact test cases before implementation: input, expected outputs and state, negative assertions, isolation, selector, and expected environment. Confirm how required coverage will be measured.
3. Choose a cohesive behavioral slice small enough to understand and verify. Keep changes that must preserve an atomic invariant together. Reuse existing helpers and patterns.
4. Add or modify a focused test and run it. Record an actual meaningful RED caused by the missing behavior; a fixture, import, infrastructure, or unrelated failure is not proof of RED. Diagnose and surface unexpected failures promptly.
5. Implement the smallest complete change for the slice. Run the same test to observe GREEN, then refactor while retaining behavior and rerun the relevant tests. Repeat for remaining cases; cover negative paths and side-effect boundaries as well as happy paths.
6. Run the required targeted unit, real-dependency integration, installed-process/acceptance, and regression checks as applicable; run the project's lint, formatting, type, and coverage gates. Measure the actual requested thresholds and output/state, not a proxy. Report exact commands, results, environment versions, and missing evidence.
7. Update directly related documentation, test catalog, and tracker. Record failures and blockers without narrowing tests, changing requirements, or claiming unsupported completion. Seek owner approval before a material scope change.
8. Hand the verified task and its evidence to `integrate-and-report`; follow the team's confirmed commit cadence. If no policy exists, ask whether to adopt a task completion commit after each verified plan task before starting the next task, or use another internal practice. This is a task-level checkpoint, not a commit required for every slice. Do not commit, integrate, or tag without authorization and the project's policies.

## Slice evidence

Record task/scenario IDs, baseline or revision, RED command and behavioral failure, GREEN and regression commands/results, coverage measurements and scope, environment, deviations, blockers, and remaining work. If red-green evidence was not captured, say so rather than reconstructing it.

## Done when

The slice satisfies its selected scenarios, preserves relevant behavior, passes the agreed gates at the relevant boundaries, and has truthful reproducible evidence. A task may require multiple slices and later integration before it is DONE.
