---
name: design-test-catalog
description: "Design a traceable test catalog and verification matrix for software requirements. Use when defining acceptance scenarios, test layers, fixtures, negative cases, environment matrices, or coverage and evidence before implementation."
---

# Design the test catalog

Make the evidence needed for each behavioral claim explicit before implementing it.

## Procedure

Before writing, resolve testing-policy and catalog paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/TESTING.md` and `docs/TEST-CATALOG.md`, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Read the contract, architecture, delivery tasks, existing tests, and test policy. Identify supported platforms, runtime dependencies, system boundaries, and applicable safety properties. Reuse valid existing tests but do not relabel them as evidence for behavior they do not exercise.
   If testing standards are absent or unresolved, use `establish-testing-standards` when available, or ask for existing standards and confirm explicit unit coverage floors, suite layers, requirement-matrix integration coverage, and happy/critical acceptance paths before adopting gates.
2. Give each scenario a stable ID and link it to requirement and task IDs. Split materially different variants into separately verifiable cases. Include normal flows, edge cases, invalid input, permissions, failure/refusal, recovery, compatibility, and regressions where relevant.
3. For each scenario define setup and fixture identity, inputs or command, expected result and observable state, negative assertions, isolation/cleanup, selector, environment, and evidence to retain. Assert absence of unwanted mutations, leaks, or artifacts where those are contractual.
4. Assign appropriate evidence layers independently: unit tests for local logic, real-dependency integration tests for external semantics, and installed-process or end-to-end acceptance tests for user-facing behavior when applicable. Mocks and in-process calls do not establish behavior at a real system boundary.
5. Define reproducible environment/version matrices, required privileges, data isolation, timeout and cleanup rules, secret handling, and safe use of external resources. Missing environments must remain visible as unverified, not be treated as passes.
6. Agree on measurable quality gates, including statement and branch coverage separately if required. Define the baseline and changed-code measurement method before claiming a threshold. Record exclusions and explain how they are approved.
7. Map requirement -> scenario -> test selector -> actual run result -> relevant revision. Feed the catalog to the delivery tracker; update it when approved requirements or observed behavior change.

## Scenario record

`ID | requirement/task | behavior and variant | setup and environment | input | expected output and state | negative assertions | layer/selector | status and evidence`

Statuses should distinguish planned, implemented, passed, failed, blocked, and not applicable. A documented test plan is not an executed test.

## Done when

Material requirements have observable scenarios at appropriate layers, with reproducible commands and explicit gaps, and each required case can be traced to real evidence.
