---
name: analyze-architecture
description: "Analyze a software specification against an existing system and design an implementation approach. Use when evaluating feasibility, architectural gaps, invariants, compatibility, risks, alternatives, or design decisions before planning implementation."
---

# Analyze the architecture

Connect the approved or draft contract to the real system without mistaking a proposed design for implemented behavior.

## Procedure

Before writing, resolve architecture and analysis paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/ARCHITECTURE.md` and `docs/PHASE2-ANALYSIS.md` (for a second phase), or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Read the contract, existing architecture, relevant code and tests, project policies, and prior decisions. Establish the current baseline and authoritative sources. Identify what is observed, proposed, or unknown.
   If architecture is missing or supplied only as unformatted source material, use `establish-architecture` when available, or ask for existing documents and collect missing decisions as user-reviewed ADRs at agreed paths. Do not substitute analysis for the user's architecture approval.
2. Map each requirement to existing surfaces and gaps: interfaces, data, dependencies, state transitions, permissions, operational boundaries, and supported environments. Trace end-to-end flows, including failures and recovery.
3. Identify invariants, compatibility and migration constraints, security/privacy risks, concurrency or partial-failure hazards, and changes that must become active atomically. Note any prerequisites and external dependencies.
4. Compare reasonable approaches for material decisions, including tradeoffs and impact on the contract. Ask the owner where choices change intended behavior, scope, cost, or support. Record approved decisions and rationale; do not silently settle unresolved requirements.
5. Propose components and boundaries that reuse project patterns. Define explicit interfaces and ownership, and explain how requirements will be verified at their actual boundaries. Avoid a design that is more detailed than the evidence supports.
6. Write or update an analysis/design artifact using the project's conventions. Link requirements, decisions, risks, implementation dependencies, test implications, and remaining questions. Reconcile contract changes with the owner.
7. Hand the design to `plan-delivery` and `design-test-catalog`. Revisit it if implementation evidence invalidates an assumption.

## Analysis outline

- Baseline and sources
- Requirement-to-existing-system gap map
- Proposed flows, interfaces, state, and invariants
- Alternatives, decisions, rationale, and approvals
- Compatibility, failure, security, and operational risks
- Dependencies, atomic boundaries, validation implications, and open questions

## Done when

The design is traceable to requirements, major tradeoffs are resolved or visibly blocked, and the team can plan safe, independently verifiable work.
