# Static analysis and architecture guardrails

Turn the engineer's intended code structure into explicit, testable constraints. Tool names are candidates, not required dependencies or claims of current compatibility. Check the actual stack, versions, existing tools, and capabilities before proposing implementation.

## Interview and rule selection

Ask the engineer:

1. What must remain structurally true? Request architecture documents and ADRs, allowed dependency directions, layer/package boundaries, public entry points, ownership rules, and prohibited dependencies or APIs.
2. Which analyzers, rule sets, architecture frameworks, or custom checks already exist? Which conventions should be retained?
3. Which constraints must block integration, which are advisory, and which require manual review? What scope, legacy baseline, and exceptions are acceptable?
4. May checks run locally and in CI? Are network access, remote rule downloads, telemetry, or hosted analysis prohibited? Prefer local approved rules and execution; do not send private code to external services.

Only confirmed constraints become policy. Do not infer the architecture from directory names alone. Record each guardrail with a stable ID and a link to the requirement or ADR it enforces.

## Match the mechanism to the constraint

| Mechanism | Appropriate uses | Limits and candidate tools |
| --- | --- | --- |
| Compiler, type checker, language analyzer | Type/interface contracts, invalid calls, selected correctness diagnostics | Use the stack's existing analyzer first; does not by itself enforce architectural dependency direction |
| Semgrep or equivalent rule-based analyzer | Prohibited APIs, recognizable source patterns, mandated boundary wrappers and project-specific conventions | Validate language/edition capabilities; pattern matches do not prove complete call graphs, runtime behavior, or absence of bypasses |
| Dependency/architecture framework | Layer direction, forbidden imports/references, cycles, package boundaries, internal API access | Candidates include Import Linter for Python, ArchUnit for Java, NetArchTest or ArchUnitNET for .NET, and dependency-cruiser for JS/TS; verify fit and current configuration support for the project tech stack |
| Existing custom architecture suite | Organization-specific invariants already represented in executable checks | Reuse and inspect it before adding another framework |
| Minimal custom structural tests | Narrow rules not supported by existing tools, such as project-specific module ownership or dependency constraints | Prefer AST/symbol/dependency-graph analysis using existing parsers over broad regex; specify treatment of aliases, re-exports, dynamic loading, generated code and test code |
| Manual review plus behavioral tests | Architectural intent not reliably observable statically, runtime wiring and dynamic boundaries | Record this as a deliberate limitation, not automated enforcement |

Prefer the simplest existing mechanism that covers the agreed constraint. A custom framework is not the default: use an established tool or small tests first. Architecture tests supplement, not replace, unit/integration/acceptance evidence.

## Example constraints to offer, not impose

- Domain logic must not import persistence, transport, or UI implementation modules.
- Cross-layer dependencies must follow an explicit allowed graph; prohibited cycles fail the check.
- External I/O, credential access, and privileged operations must pass through approved boundary modules.
- Consumers must use public package interfaces rather than internal implementation modules.
- Database access belongs to approved adapters; deterministic logic remains separate from I/O.
- Cross-cutting conventions must use shared helpers rather than unapproved duplicate implementations.

Discuss which examples fit the architecture; some require multiple mechanisms or manual review. A file-location rule alone cannot prove semantic separation or safe runtime behavior.

## Guardrail record

`ID | invariant | requirement/ADR | scope | mechanism and rule/config path | tool/version | severity | command | blocking stage | owner | exceptions | enforcement evidence`

Ask where to store rules and tests. Offer paths such as `.semgrep/`, `tests/architecture/`, and the framework's conventional config file only when applicable and approved. Link architecture intent from the architecture/ADR documents, operational commands from the coding/testing guides, and rule evidence from the tracker. Avoid duplicating the rule text across authorities.

## Implement and validate only when authorized

1. Create a scoped implementation task for approved rules, dependencies, configuration and CI changes. Confirm local commands, target file inclusion, rule discovery, exit behavior, and exclusions. Do not claim a rule is enforced just because its file exists.
2. For every custom rule or structural assertion, test a known violation that must fail and a compliant example that must pass, plus relevant aliases/bypasses and scope boundaries. Use isolated fixtures rather than inserting violations into real product code. Record an observed failure for the intended violation, followed by passing checks on compliant code.
3. Verify that a missing rule file, broken analyzer, parser error, or unsupported target is surfaced and blocks the required gate rather than appearing as a clean scan. Confirm checks actually discover the intended files and rules.
4. Run the analyzer or architecture selector against the real project, then validate CI wiring when within scope. Report discovered violations, limitations and unverified environments explicitly; zero findings with no analyzed targets is not success.
5. Baseline legacy violations only with approval: record exact scope and remediation, block new violations where supported, and prohibit broad suppressions. Exceptions require a rule ID, owner, rationale and removal/review condition. Changing architecture requires an explicit decision and corresponding rule/test update.

Distinguish proposed, documented, configured, locally verified and CI-verified status. A passing static check establishes only the properties that its validated rules can detect.
