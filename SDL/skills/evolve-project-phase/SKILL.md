---
name: evolve-project-phase
description: "Prepare an existing software project for a new specification, phase, or major feature while preserving its prior baseline. Use when analyzing a draft next-phase spec, evaluating compatibility and existing behavior, or planning staged evolution."
---

# Evolve a project to the next phase

Start from the actual prior system and its limitations, not from an imagined clean slate.

## Procedure

Before writing, resolve phase contract, analysis, tracker, and catalog paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/specs/PHASE2-SPECIFICATION.md`, `docs/PHASE2-ANALYSIS.md`, `docs/PHASE2-IMPLEMENTATION-TASKS.md`, and `docs/PHASE2-TEST-CATALOG.md` for a second phase, or choose custom paths; use `organize-project-docs` if available. Increment the phase number for subsequent phases. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect the new draft, prior accepted contract, architecture, implementation tracker, tests, known limitations, release evidence, and current repository state. Identify the prior baseline or tag if one already exists; do not create or alter it without authorization.
   Run `clarify-supplied-spec` for the newly supplied phase spec when available, or perform its equivalent review and question/response recording directly. Reuse its phase-specific register if already reviewed; do not repeat resolved questions or overwrite earlier phase records.
2. Compare the draft with implemented behavior and existing guarantees. Map additions, changes, incompatibilities, prerequisites, migration/rollback concerns, and unresolved ambiguities. Separate documented intent from verified behavior and unsupported claims.
3. Analyze alternatives and risks with `analyze-architecture`. Ask the owner about material conflicts, scope, compatibility, or support decisions. Record decisions and update the new contract; preserve prior historical evidence rather than rewriting it.
4. Obtain required approval of the new contract and plan. Approval is separate from permission to commit the baseline, implement, merge, or tag. Follow the owner's explicit instructions and repository policy for each operation.
5. Create or extend a dependency-ordered tracker with `plan-delivery` and a traceable catalog with `design-test-catalog`. Include prior-phase regression requirements, new environment needs, atomic activation constraints, and explicit quality/integration gates.
6. Execute eligible work via `implement-tested-slice`, integrate via `integrate-and-report`, and qualify the resulting candidate via `qualify-release`. Track partial work and blockers honestly; retain previous version claims unless the owner approves a change.

## Phase transition record

- Prior baseline, actual behavior, support, and known limitations
- New contract and approval; compatibility and migration decisions
- Gap map, dependencies, and atomic boundaries
- Plan, scenario catalog, regression and environment matrix
- Revision/evidence links, unresolved risks, and release decision

## Done when

The next phase has an approved, traceable contract and evidence-gated plan grounded in the prior baseline; later implementation and release remain separately verified.
