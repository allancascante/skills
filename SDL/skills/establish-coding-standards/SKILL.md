---
name: establish-coding-standards
description: "Collect or define coding standards with the user. Use when choosing coding rigor, Semgrep/static analysis, source vulnerability scanning (SAST), dependency scanning (SCA), architecture tests, structural guardrails, typing, review, or importing a coding guide."
---

# Establish coding standards

Make the team's preferred rigor explicit. Written standards and configured enforcement are separate deliverables.

## Procedure

1. Inspect existing instructions, contributor/coding guides, tooling manifests, configuration, and CI. Resolve destinations through the document map; ask before choosing new paths. Offer `CONTRIBUTING.md` as the entry point and `docs/CODING.md` for detailed policy. Use `organize-project-docs` when available.
2. Ask whether standards already exist and request their paths or content. Ask whether to format/save only or also review gaps. If provided, preserve meaning and provenance while normalizing Markdown and saving at approved locations. Flag contradictions with existing policies/configuration for resolution; do not silently replace stricter rules.
3. If standards are absent or need decisions, ask the desired stringency using the [guardrail profiles](./references/guardrail-profiles.md): essential, strict (recommended for production work), high-assurance, or custom. Explain the cost and scope of each. Ask which checks should block local completion, integration, or release, and whether existing violations need a separately approved baseline/ratchet.
4. Confirm applicable language/runtime constraints, formatter/linter, static analysis/type rigor, warning/suppression policy, dependency and error-handling conventions, complexity/design rules, review, test-first workflow, and branch/integration requirements. Offer existing project tools first. Do not invent executable commands or prescribe tooling for other stacks.
   Use the [structural guardrails guide](./references/structural-guardrails.md) to ask which architecture invariants the engineer wants enforced. Offer Semgrep or equivalent source rules, stack-appropriate dependency/architecture frameworks, existing custom checks, or minimal custom structural tests. Confirm each invariant, ADR/requirement link, scope, tool/rule, severity, command, gate stage and exception policy. Prefer existing tooling; do not mandate a new framework or treat a static pattern check as proof of runtime architecture.
   Use the [security guardrails guide](./references/security-guardrails.md) to agree separate controls for authored-code vulnerabilities (SAST) and resolved direct/transitive dependency vulnerabilities (SCA). Ask about rigor, tool/rule/advisory sources, scan scope and schedule, severity/confidence gates, advisory freshness, triage/remediation, exceptions and privacy. Recommend strict controls for production work but obtain confirmation; neither ordinary lint nor architecture checks substitute for vulnerability scanning.
   Ask for the team's internal repository practice before proposing a new one. Recommend a dedicated branch per plan task, small validated slices, and a task completion commit containing its verified code, tests, related documentation, and evidence before starting the next task. Allow intermediate checkpoints if team policy permits; do not imply exactly one commit per task or force squashing. Confirm cadence, branch naming/base, review/PR and merge strategy, message conventions, post-integration gates, and whether commits need per-operation approval or are authorized by an explicit standing policy. The user may replace the recommendation with their internal practice; record that choice.
5. Show a concrete proposed policy with each check's scope, threshold or severity, command, gate stage, owner, and exception process. Mark unavailable tools/commands as proposed and unverified. Ask the user to confirm; do not infer acceptance from the recommended profile.
6. Save the approved policy and link it from the contributor entry point and document map. Record deliberate deviations and unresolved choices. Coordinate test/coverage policy with `establish-testing-standards` rather than assigning coverage numbers here.
7. Validate links and policy/configuration consistency. Report which guardrails are only documented and which are already configured and observed passing. Tool installation, config changes, CI/hook enforcement, and remediation require an explicitly scoped implementation task; do not claim Markdown enables enforcement.

## Done when

Supplied standards are faithfully saved, or the user's chosen rigor is translated into approved, measurable guardrails with clear enforcement status and exceptions.
