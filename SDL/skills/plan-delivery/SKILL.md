---
name: plan-delivery
description: "Create or update a dependency-ordered software implementation plan and task tracker. Use when decomposing an approved specification, selecting the next ready task, recording blockers, or coordinating staged delivery."
---

# Plan delivery

Convert the contract and architecture into tasks whose completion is based on evidence, not activity.

## Procedure

Before writing, resolve roadmap and tracker paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/IMPLEMENTATION.md` and `docs/IMPLEMENTATION-TASKS.md`, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect the approved contract, design, current baseline, existing tracker, tests, and repository state. Establish which artifacts are authoritative and what approval is needed before work or integration.
2. Decompose work into cohesive tasks with stable IDs. Record production surfaces, requirement IDs, dependencies, explicit exclusions, acceptance criteria, risk, and required validation layers. Preserve atomic cross-cutting invariants: do not activate an incompatible partial feature merely to make a task smaller.
3. Order tasks by actual dependencies, not document order. Identify independently parallelizable work only when ownership and file or state boundaries do not conflict. Plan incremental vertical or behavioral slices within each task.
4. Collaborate with `design-test-catalog` to map tasks to concrete scenario IDs and test selectors, including negative paths, compatibility, and regression cases. Set explicit project-approved quality and coverage gates; do not assume a universal threshold.
5. Track each task as TODO, DOING, BLOCKED, PARTIAL, or DONE, or use the project's equivalent. Record owners, blockers, decisions, validation commands/results, versions, evidence locations, and integration status. Ready to integrate is not DONE if integration or required post-integration validation is outstanding.
6. Select the next task whose prerequisites and approvals are satisfied. If no task is ready, report the dependency or decision blocking progress. Do not conceal failed checks or invent a passing result.
7. Update the tracker as work progresses. An owner-approved scope change must update the contract, affected tasks, tests, and claims; an unresolved failure remains visible.

## Task record

- ID and title; status and owner
- Requirements, production surfaces, dependencies, and explicit exclusions
- Slices and atomicity constraints
- Scenario IDs, test selectors, environments, and acceptance/quality gates
- Commands and actual outcomes; evidence, blockers, decisions, and integration reference
- Remaining work and next eligible action

## Done when

Every planned task has clear prerequisites and measurable completion criteria, and the next ready task can be selected without guessing.
