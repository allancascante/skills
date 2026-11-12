# Suggested Markdown structure and responsibilities

Offer this explicit layout to the user before creating documents. Paths are relative to the target project root; the user may retain existing conventions or choose custom paths. This is not permission to scaffold every file.

```text
README.md
CONTRIBUTING.md
docs/
  README.md                         # Optional agreed document map
  ARCHITECTURE.md
  adr/
    0001-decision-title.md          # One file per actual decision
  CODING.md
  TESTING.md
  IMPLEMENTATION.md
  IMPLEMENTATION-TASKS.md
  TEST-CATALOG.md
  ACCEPTANCE-RUNBOOK.md
  specs/
    SPECIFICATION.md
    SPECIFICATION-CLARIFICATIONS.md
    PHASE2-SPECIFICATION.md          # Only when a next phase exists
    PHASE2-SPECIFICATION-CLARIFICATIONS.md
  PHASE2-ANALYSIS.md                 # Only when a next phase exists
  PHASE2-IMPLEMENTATION-TASKS.md
  PHASE2-TEST-CATALOG.md
tests/
  unit/
  integration/
  acceptance/
```

`docs/README.md` is the proposed document map; confirm its creation or reuse an existing index. Create phase records only when needed: `PHASE2-*` for the second phase, `PHASE3-*` for the third, and so on. ADR numbers are stable, sequential IDs; replace `decision-title` with a descriptive slug. Test directories separate unit, integration, and acceptance evidence; reuse equivalent native conventions where appropriate. A small project may combine document roles in clearly identified sections, provided the map names the authoritative section for each role.

## Roles, contents, and update triggers

| Document role | Suggested path | Contents and authority | Update when |
| --- | --- | --- | --- |
| Project entry point | `README.md` | Purpose, current implemented capabilities, quick start, known qualification limits, links to guides and active phase | User-visible behavior, commands, current phase, or support evidence changes |
| Contributor entry point | `CONTRIBUTING.md` | Conventions, safe-change expectations, development commands, completion criteria, routing to detailed guides | Team workflow or tooling changes |
| Product contract | `docs/specs/SPECIFICATION.md` | Goals, non-goals, stable requirement IDs, workflows, interfaces, failure behavior, compatibility, accepted decisions and approval status | Owner approves requirements or scope changes |
| Specification clarifications | `docs/specs/SPECIFICATION-CLARIFICATIONS.md` | Source-linked unknowns, questions, actual user responses, separate interpretations, confirmed amendments, open/deferred decisions and blocking stages | Spec intake, user answers, follow-up decisions or source revisions |
| Architecture | `docs/ARCHITECTURE.md` | Boundaries, data/control flows, invariants, dependencies, compatibility and safety constraints | Design boundaries or invariants change |
| Architecture decisions | `docs/adr/0001-<decision-title>.md` | Context, alternatives, decision, rationale, consequences, status, owner and requirement links | A consequential decision is proposed, approved or superseded |
| Coding workflow | `docs/CODING.md` | Scenario-first planning, slice size policy, red-green-refactor, quality gates, branch/integration procedure and evidence rules | Engineering workflow changes |
| Testing policy | `docs/TESTING.md` | Test-layer responsibilities, commands, fixtures, isolation, external-resource safety, coverage measurement, environment prerequisites | Test infrastructure or validation policy changes |
| Roadmap | `docs/IMPLEMENTATION.md` | Milestones, dependency order, scope, release/acceptance gates, deferred work | Delivery sequencing or milestone scope changes |
| Task tracker | `docs/IMPLEMENTATION-TASKS.md` | Task IDs, dependencies, status, exact selected scenarios, red/green evidence, commands/results, revisions, blockers, remaining work | Before starting a task, after validation, on blockers, and after integration |
| Test catalog | `docs/TEST-CATALOG.md` | Requirement-to-scenario mapping, variants, prerequisites, assertions, unit/integration/acceptance selectors and evidence links | Requirements, scenarios, test identities, or execution evidence changes |
| Acceptance runbook | `docs/ACCEPTANCE-RUNBOOK.md` | Reproducible installed-system workflow, safe setup, commands/expected state, refusal/recovery, cleanup; separate actual execution records per candidate/environment | Acceptance workflow or qualification evidence changes |
| Phase analysis | `docs/PHASE2-ANALYSIS.md` | Prior-baseline gap analysis, alternatives, decisions/rationale, compatibility, risks, unresolved questions | Phase planning decisions or assumptions change |
| Phase contract | `docs/specs/PHASE2-SPECIFICATION.md` | Next-phase requirements and compatibility contract, separately approved | Next-phase scope changes |
| Phase clarifications | `docs/specs/PHASE2-SPECIFICATION-CLARIFICATIONS.md` | Next-phase specification questions, responses and amendment history | Next-phase intake or clarification decisions |
| Phase tracker/catalog | `docs/PHASE2-IMPLEMENTATION-TASKS.md`, `docs/PHASE2-TEST-CATALOG.md` | New-phase tasks, scenario mappings, evidence and blockers | Next-phase work progresses |

## Minimal record outlines

- **Contract:** status/authority; context; goals/non-goals; requirement IDs and observable behavior; errors and safety; compatibility; decisions/open questions.
- **Analysis/architecture:** baseline; requirement gaps; flows and invariants; alternatives/decisions; risks; dependencies; verification implications.
- **Guides:** applicability; prerequisites; agreed policies; actual project commands; exceptions/approvals; links to detailed sources.
- **Roadmap:** milestones; requirement scope; dependency graph; acceptance gates; exclusions and deferred work.
- **Tracker:** task ID/status; requirements/dependencies; slices; exact scenario/test matrix; evidence by layer; branch/revisions; blockers and next action.
- **Catalog:** scenario ID; requirement/task; given/when/then; variants/negative assertions; environment/isolation; executable selectors or explicit gaps; execution evidence links.
- **Runbook:** candidate/prerequisites; safe setup; ordered commands and expected observations; negative/recovery checks; cleanup; separately labeled actual results and retained evidence.

## Authority rules

Accepted requirements do not prove implementation. Planned tests do not prove execution. Unit evidence does not establish integration or installed-system acceptance. A runbook is a procedure until execution is recorded.

Keep detailed evidence in the tracker or an agreed execution-record section; link to it from catalogs and summaries rather than copying logs everywhere. Preserve earlier phase baselines, failures, and qualification limitations. Proposed policy or undecided quality floors must stay visibly proposed.
