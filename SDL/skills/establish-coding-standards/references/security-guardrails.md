# Security analysis guardrails

Agree with the engineer on vulnerability-analysis controls for both authored code and dependencies. These are policy choices for subsequent implementation, not a vulnerability assessment or proof of a secure product. Existing organizational requirements remain authoritative.

## Ask before choosing controls

- Which existing security policy, threat model, analyzers and advisory sources apply? Who owns triage and risk acceptance?
- Which rigor profile is appropriate: essential, strict, high-assurance or custom? Define controls individually rather than relying on a profile name.
- Which languages, source directories, generated/vendor code, direct/transitive dependencies, development/build/runtime dependencies, platforms and shipped artifacts are in scope?
- Which severities and confidence levels block a change, integration or release? How are existing findings, unknown severity, disputed results and unavailable fixes handled?
- When should checks run: locally, on source/dependency changes, on every PR, before release, and periodically for newly published advisories?
- Must execution remain local/offline? Which advisory downloads are permitted? Dependency inventories and package names can also be sensitive; confirm before using remote services, uploading reports or enabling telemetry.

## Two distinct analysis surfaces

| Surface | Purpose | Candidate mechanisms | Required limits to document |
| --- | --- | --- | --- |
| Authored code: static application security testing (SAST) | Detect insecure source patterns and supported data-flow issues | Semgrep security rules, language-specific security analyzers, or an organization's existing approved scanner | Language/edition support, rule scope, confidence, target discovery, dynamic behavior and analysis gaps; general lint/type checks alone do not establish security analysis |
| Dependencies: software composition analysis (SCA) | Match resolved component versions against vulnerability advisories | Existing ecosystem audit tools, OSV-compatible scanners, approved SCA tools, artifact or SBOM analysis where applicable | Direct/transitive coverage, exact lockfile/resolved graph, build/dev/runtime scope, platform differences, advisory freshness, private packages and unrecognized components |

Verify actual tool capabilities and version support before proposing commands or installation. An SBOM is an inventory, not by itself a vulnerability scan. SCA cannot establish absence of unknown vulnerabilities, and SAST is not a substitute for dependency analysis. Neither replaces risk-driven behavioral testing or expert review.

## Profiles to offer for confirmation

| Profile | Suggested controls |
| --- | --- |
| Essential | Approved SAST and dependency scans at agreed checkpoints; explicit scope, triage owner and severity gates; visible gaps and exceptions |
| Strict (recommended) | SAST on PRs and resolved direct/transitive dependency scans on dependency changes and before release; recurring dependency scans for new advisories; propose blocking high/critical findings pending triage or explicit time-bounded risk acceptance |
| High-assurance | Strict plus broader supported data-flow/custom rules, shipped artifact/SBOM coverage, and risk-based independent review of critical paths |
| Custom | Exact tool, scope, schedule, severity/confidence gates and remediation policy selected by the organization |

The strict blocking threshold is a proposal, not automatic approval. Agree separately how severity/confidence taxonomies map between tools, what blocks while triage is pending, and whether lower-severity findings create tracked remediation obligations. New-finding-only gates require an approved, recorded baseline; existing findings must remain visible and subject to release policy.

## Record enforceable decisions

For each control record:

`ID | SAST/SCA | tool/version and rules/advisory source | scope and exclusions | command | schedule | gate and threshold | triage/remediation owner | exception policy | evidence/status`

Include remediation targets and escalation, evidence retention/access, and advisory-update/freshness policy. A scan error, unsupported lockfile/language, missing credentials/rules, empty target set or stale/unavailable advisory source must be explicit; define when it blocks instead of treating it as a clean scan.

For findings, retain the rule/advisory identifier, affected source location or resolved package/version and dependency path, severity, confidence where available, applicability/reachability evidence or unknown status, disposition, owner and next action. Do not equate lack of reachability evidence with safety or suppress findings merely because no patch exists.

Exceptions require a specific finding/scope, rationale, risk approver, compensating controls if any, expiry/review condition, and tracked remediation. False-positive dispositions require evidence. Never silently weaken rules, omit dependencies, or accept an advisory finding on the engineer's behalf.

## Implementation handoff

Once approved, create a scoped task to configure tools, required manifests/lockfiles, rule files, schedules and CI gates. Reuse existing tools before adding dependencies. Validate scan discovery and failure behavior with safe isolated fixtures or tool-provided test facilities, not exploitable examples in real product code. Record actual scanned revisions, dependency inventory, rule/advisory versions and outcomes; rerun affected checks after remediation.

Keep documented, configured, locally verified and CI-verified status separate. Tool/config changes and remediation require authorization; drafting this policy does not install a scanner or establish that a scan passed.
