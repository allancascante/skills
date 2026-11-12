# Testing baseline and rigor choices

## Recommended strict baseline

Offer this to the user; do not apply it without agreement:

- **Unit:** aim for 100% statement and branch coverage of in-scope production code, with explicit aggregate gating floors of at least **99% statements and 99% branches**, measured separately on unit tests alone. Recommend **100% changed-code statement and branch coverage**. Show actual values and missing lines/arcs; 99% is not 100%. Define coverage scope and changed-code comparison method before claiming compliance.
- **Integration:** **100% of applicable approved scenario variants** in the requirement-traceable test matrix must have executed, passing real-dependency evidence for each required environment. A test count or line-coverage percentage is not scenario coverage. Record inapplicable scenarios with approved rationale; missing, blocked, skipped, or failing scenarios do not pass.
- **Acceptance:** execute the installed product at the user's boundary for **all agreed happy paths and critical paths**: for example authorization/refusal, destructive actions, rollback/recovery, data integrity, and other risk-ranked flows. For a CLI use an installed executable subprocess, not only an in-process runner; for other products use the equivalent real interface. Confirm path and testing tool selection with the user.
- **Structure:** separate unit, integration, and acceptance responsibilities and results; reuse the project's native layout. Link requirements, scenario IDs, concrete selectors, candidate revisions, and environments.
- **Evidence:** observed meaningful red/green where applicable, actual outputs/state, isolated fixtures, reproducible commands, and visible failures. Gate integration/release on the agreed checks; validate the integrated candidate under project policy.

The proposed 99% aggregate floor requires user confirmation; it is not evidence of achieved coverage. Keep the aspirational target, enforced floor, and measured result distinct.

## Rigor choices

| Profile | Unit coverage choice | Integration and acceptance | Appropriate discussion |
| --- | --- | --- | --- |
| Essential | User must choose explicit statement/branch/changed-code floors; no silent numeric default | Requirement-linked boundary scenarios and happy/critical paths remain identified; any deferred scope is explicit | Early-stage constraints, cost, risks, and a plan to raise rigor |
| Strict (recommended) | 100% target; 99% aggregate statements and branches; 100% changed-code | All applicable matrix scenarios; all agreed happy and critical paths on required environments | Production delivery with near-total unit coverage and traceable behavior |
| High-assurance | Strict floors or explicitly stronger agreed floors | Strict plus risk-based fault injection, concurrency/recovery, compatibility and independent observations | Critical systems; add mutation/property tests or other techniques where justified |
| Custom | Exact per-metric floors, scope, and exceptions chosen by owner | Exact scenario/path/environment gates chosen by owner | Existing organizational policies or domain-specific obligations |

Lower cost or coverage never permits fabricated results, unsafe fixtures, ignored failures, or unsupported release claims.

## Measurement and traceability

- Unit statement percentage: covered executable statements / all in-scope executable statements.
- Unit branch percentage: covered branch outcomes / all measurable in-scope branch outcomes. If the stack cannot measure branches, report that gap and agree an alternative explicitly; do not call statement-only coverage branch coverage.
- Changed-code coverage: define baseline/diff and treatment of new functions and edited decisions; inspect executable lines and all relevant outgoing branch outcomes, not only changed text lines.
- Integration scenario percentage per required environment: applicable scenario variants with passing evidence / all applicable approved scenario variants. Report the numerator/denominator and non-applicable decisions; do not shrink scope silently.
- Acceptance path percentage per required environment: agreed paths with passing end-to-end evidence / all agreed paths. Paths not executed remain unverified.

Record scenario rows as:

`requirement ID | scenario ID/variant | risk | layer applicability/rationale | setup/environment | assertions and negative paths | selectors | status | revision/evidence`

Keep metric units separate. An aggregate line/branch score cannot establish coverage of requirements, integration scenarios, or acceptance paths.
