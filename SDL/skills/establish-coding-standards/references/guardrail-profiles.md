# Coding guardrail profiles

These are options to discuss, not policy until approved. Existing stronger project constraints remain in force unless their owner explicitly changes them. Security, credential protection, truthful reporting, and respect for user changes are not optional at any level.

| Area | Essential | Strict (recommended) | High-assurance |
| --- | --- | --- | --- |
| Formatting and lint | Consistent formatter; correctness/error lint blocks changed code | Format and agreed lint rules block integration across the agreed scope | Strict plus additional approved domain-specific analysis |
| Static analysis and typing | Available compiler/analyzer checks; type public boundaries where supported | Strict analyzer/type mode where supported; no new unexplained diagnostics | Strict plus deeper analysis of critical flows and invariants |
| Structural guardrails | Identify and document engineer-approved boundaries; automate selected rules where practical | Approved Semgrep/equivalent and architecture checks block boundary violations, with tested rules and visible limitations | Strict plus risk-based custom rules, bypass cases and broader dependency-graph validation where warranted |
| Source and dependency security | Agree SAST/SCA tools, scope, checkpoint scans, triage and severity gates | PR source scans, dependency-change/release and recurring advisory scans; propose blocking high/critical findings pending triage or explicit risk acceptance | Strict plus broader supported analysis, artifact inventory coverage and risk-based independent review |
| Suppressions | Specific, justified, reviewable; no blanket ignore | Document owner, reason, scope and removal condition | Time-bounded exceptions with explicit risk acceptance |
| Design and complexity | Existing patterns, focused changes, clear errors | Small cohesive slices, explicit invariants, reviewed complexity limits | Critical-boundary design review and independently verified invariants |
| Workflow | Relevant automated regression checks | Observed test-first slices where applicable; regressions and quality gates | Strict plus risk-based fault/concurrency/compatibility verification |
| Integration | Named completion checks | Required checks on the integrated revision; known failures visible | Strict plus independent critical-change review and retained release evidence |

Profile names alone are insufficient. Ask the team to specify exact analyzer severities, numeric complexity limits if wanted, scope (changed code or whole project), and when each check blocks work.

For legacy violations, record the actual baseline and remediation plan only with approval. Do not silently exclude files, weaken analysis, or count unrelated existing failures as passes. For generated/vendor code, agree and document exclusions and ownership rather than assuming them.

## Recommended repository workflow

Ask for existing internal practice first. If none is provided, offer this policy for confirmation, independently of the chosen guardrail profile:

1. Start each dependency-ready plan task from the team's agreed integration baseline on a dedicated task branch.
2. Work in small validated slices. Intermediate checkpoints are allowed under team policy, but do not accumulate unrelated tasks in an uncommitted worktree.
3. When the task's implementation and required pre-integration checks are complete, commit its intended code, tests, related documentation, and evidence together as a cohesive completion checkpoint before starting the next task. Reference the task ID in the commit message. This is a recommended commit at each task boundary, not a requirement for exactly one commit per task.
4. Follow the approved review/PR and integration strategy. Record the task and integration revisions; run required post-integration checks on the actual integrated revision before marking DONE. Ready-to-commit, committed, integrated, and DONE are distinct states.
5. If blocked or partial, report that state. Any checkpoint commit must be clearly labeled as partial and authorized; it does not imply completion.

The user may choose a different cadence, branching model, or review/merge process as internal practice. Record the confirmed policy in the coding guide rather than imposing these defaults. Confirm commit authorization (per operation or explicit standing policy) separately from implementation approval; push, merge, tag, and release permissions must also be explicit. Preserve unrelated work and never stage it merely to obtain a clean tree.

## Policy record outline

- Status, owner, approval, applicable language/runtime, and source documents
- Chosen profile and per-area overrides
- Code conventions: naming, interfaces, errors, dependencies, comments, compatibility
- Checks: tool/rule, severity/threshold, scope, command, gate stage
- Structural invariants: requirement/ADR links, analyzer or architecture-test mechanism, rule fixtures, target discovery, limitations and enforcement status
- Security analysis: separate SAST/SCA scope, direct/transitive and dev/build/runtime coverage, scan/advisory schedule, severity/confidence gates, triage/remediation, risk exceptions, privacy and enforcement evidence
- Review, small-slice workflow, integration and post-integration validation
- Repository practice: commit cadence, task ID convention, branching, review/merge strategy, operation permissions, and task/integration revision evidence
- Exceptions: rationale, approver, expiry/removal condition
- Existing debt, remediation, and documented-versus-enforced status
