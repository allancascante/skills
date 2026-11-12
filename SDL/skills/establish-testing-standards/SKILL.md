---
name: establish-testing-standards
description: "Collect or define automated testing standards with the user. Use when importing a testing guide, choosing coverage thresholds, structuring unit/integration/acceptance suites, or setting requirement-traceable scenario coverage and critical-path acceptance gates."
---

# Establish testing standards

Agree on measurable testing rigor and evidence at each boundary. Code coverage, scenario coverage, and acceptance coverage are different measures.

## Procedure

1. Inspect requirements, risks, existing guides/tests/configuration, and CI. Resolve testing-guide, catalog and runbook paths through the agreed document map. Ask before choosing new locations; offer `docs/TESTING.md`, `docs/TEST-CATALOG.md`, and `docs/ACCEPTANCE-RUNBOOK.md` via `organize-project-docs`.
2. Ask whether the user has testing standards and request their paths/content. Ask whether to format/save only or also review gaps. If supplied, preserve their semantics and provenance in the agreed Markdown structure; ask about contradictions, missing thresholds, or incompatible tooling instead of silently substituting defaults.
3. If absent or incomplete, ask for rigor: essential, strict (recommended), high-assurance, or custom. Present the [testing baseline and choices](./references/testing-baseline.md). Ask separately about unit statement and branch thresholds, changed-code coverage, integration scenario coverage, acceptance paths, supported environments, and gate stages. Recommend the near-total baseline, but require confirmation.
4. Agree on suite structure, such as `tests/unit/`, `tests/integration/`, and `tests/acceptance/`, or equivalent native conventions. Define layer responsibilities, real dependency/process boundaries, fixture isolation, safe resource opt-in, cleanup, timeouts, reproducibility, and failure handling. Ask which happy and critical paths apply; do not make those risk decisions silently.
   If structural guardrails are approved, agree where architecture tests and rule fixtures belong, offering `tests/architecture/` or native framework conventions. Require violating and compliant fixtures for custom rules and assertions, target/rule discovery checks, explicit analyzer-error behavior and executable selectors. Track these separately from behavioral scenario coverage; architecture checks do not replace unit, integration or acceptance tests.
5. Specify exact numerators/denominators, unrounded thresholds, included code/scenarios, approved exclusions, and measurement commands or explicit tooling gaps. Include all in-scope production code, including unimported modules, in unit measurement. Use unit-only evidence for a unit coverage claim; a combined run cannot prove unit coverage.
6. Define requirement -> scenario/variant -> unit/integration/acceptance selector -> actual result -> candidate/environment traceability. Integration must cover all applicable approved scenarios; an inappropriate layer can be explicitly not applicable with rationale, never silently dropped. Acceptance must include agreed happy and critical paths. Planned, implemented, passed, failed, blocked, and not applicable are distinct.
7. Show the proposed policy and obtain confirmation, then save at the agreed paths, update the document map and contributor links, and hand scenario detail to `design-test-catalog`. Keep missing tests and environments visible. No weakening thresholds, skips, xfails, or denominator changes to manufacture success.
8. Check links, policy/configuration consistency, and whether the agreed metrics can actually be measured. Report documentation versus configured enforcement and observed results separately. Implement tooling or CI changes only as an authorized, separately verified task.

## Done when

Existing standards are faithfully saved, or the user has approved explicit layer responsibilities, coverage thresholds, scenario traceability, acceptance paths, and safety/gating rules. Unconfigured checks and unverified behavior remain explicit.
