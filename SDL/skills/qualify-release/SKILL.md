---
name: qualify-release
description: "Qualify a software release with an executable acceptance runbook and supported-environment matrix. Use when validating installed workflows, certifying compatibility, recording release evidence, or deciding whether a release is ready."
---

# Qualify a release

A runbook is a plan until it has actually been executed; acceptance and compatibility claims need independent evidence.

## Procedure

Before writing, resolve acceptance-runbook and qualification-record paths through the agreed documentation map or existing project links. If locations are not agreed, ask whether to retain the current layout, use `docs/ACCEPTANCE-RUNBOOK.md` with separate procedure and execution-record sections, or choose custom paths; use `organize-project-docs` if available. Reuse confirmed paths and apply `maintain-project-docs` to affected authorities and cross-links.

1. Inspect the approved release contract, implementation tracker, test catalog, known limitations, package or revision, and release policies. Identify prerequisites, supported platforms and versions, and approvals. Do not assume feature-complete means qualified.
2. Write or update a reproducible operator runbook using the installed deliverable where applicable. Include environment setup, isolated fixtures, permissions, commands, expected outputs and independently observed state, failure/refusal and recovery checks, cleanup, and safe handling of secrets. Specify timeout and external-resource requirements.
3. Trace each acceptance scenario and supported environment to the relevant requirement and test. Include realistic end-to-end workflows and safety invariants, not just process exit codes. Define the evidence and release gates required by the owner.
4. Run each required scenario on each claimed environment using the actual release candidate. Record package/revision, tool and platform versions, commands, outputs or retained artifact locations, timestamps where useful, and actual pass/fail/blocked outcomes. Redact secrets.
5. Investigate failures and missing environments; keep them visible. Fix defects or seek explicit owner approval for a scope/support change, then update the contract, tests, runbook, and claims. Do not present an unrun variant, a unit test, or a procedure alone as certification.
6. Repeat affected checks on the final candidate after fixes. Report results separately for every supported environment and provide a release recommendation, outstanding risks, and required approvals. Perform commits, tags, publishing, or deployment only when authorized.

## Qualification record

`candidate | requirement/scenario | platform/version | command | expected | actual | pass/fail/blocked | evidence | limitations`

Keep the runbook instructions separate from the record of actual execution, and link both to the candidate revision.

## Done when

All required scenarios and claimed environments have recorded passing evidence on the final candidate, and the owner has made the required release decision. Otherwise report the precise unqualified scope.
