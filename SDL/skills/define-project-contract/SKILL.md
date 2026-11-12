---
name: define-project-contract
description: "Define or refine a software project's specification and acceptance contract. Use when starting a project, turning an idea or draft into implementable requirements, identifying scope and ambiguities, or reviewing requirements before development."
---

# Define the project contract

Turn the request and existing evidence into a reviewed, testable contract. An approved specification is not proof of implementation.

## Procedure

Before writing, resolve the contract and related document paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/specs/SPECIFICATION.md`, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect available requirements, existing behavior, constraints, architecture, and project instructions. Identify the owner and the authoritative sources; distinguish observed facts from assumptions. Preserve existing changes.
   When a detailed spec is supplied but has not been reviewed, begin with `clarify-supplied-spec` if available, or perform its equivalent source review and question/response recording directly. Reuse its clarification register and confirmed answers rather than repeating the interview; carry unresolved blockers into contract finalization.
2. Describe the problem, users, goals, non-goals, operating context, dependencies, supported environments, and compatibility requirements. Include security, privacy, reliability, accessibility, performance, and operational constraints where relevant.
3. Give each significant requirement a stable ID. Specify observable inputs, outputs, state changes, errors, refusal behavior, edge cases, and measurable acceptance criteria. State what must remain unchanged.
4. Identify ambiguous, conflicting, or consequential choices. Propose options and tradeoffs, then ask the owner before deciding scope or behavior. Record answers, rationale, unresolved questions, and explicit exclusions; do not silently downgrade requirements.
5. Review the contract for consistency, feasibility, testability, and safety. Link existing evidence, and call out unknowns and dependencies rather than inventing answers.
6. Put the result in the project's chosen documentation location, preserving existing structure. Seek the required owner approval before implementation; record approval separately from permission to commit, integrate, or release.
7. Hand the approved contract to `analyze-architecture` and `plan-delivery`; revise it if later analysis exposes a material gap.

## Contract outline

- Context and sources; problem and goals
- In scope / explicitly out of scope
- Actors and workflows
- Requirements: ID, behavior, constraints, acceptance criterion
- Compatibility, operational and nonfunctional requirements
- Error, safety, and recovery behavior
- Open questions, decisions, dependencies, and approval status

## Done when

The owner can distinguish agreed requirements from assumptions; each material claim can be verified; unresolved decisions and implementation authorization are explicit.
