# Reusable software delivery skills

**Author: [Allan Cascante](https://github.com/allancascante)**

This bundle provides a specification-led, test-driven software delivery workflow. It is independent of programming language, product domain, and agent harness.

New here? Follow the [getting-started walkthrough](./skills/GETTING-STARTED.md) to watch the process in a disposable project, or return to the [repository overview](../README.md).

## What is a skill?

A skill is a directory containing a `SKILL.md` entry point with a name, description, and procedure. Some skills also include `assets/` templates or `references/` guides that the agent reads when needed.

These are instructions, not an executable application or a harness-specific plugin. No package installation or build is required to use the bundle. Running a project's tests, analyzers, or release checks still requires that project's own tools and environment.

## Use in any project

### 1. Get the collection

Clone this repository into a location of your choice, outside the target project:

```sh
git clone https://github.com/allancascante/skills.git
```

In the examples below, replace `/path/to/skills` with the absolute path to this repository. The source skill directories are under `SDL/skills/` relative to the repository root.

### 2. Choose how your harness loads instructions

| Harness capability | How to use this collection |
| --- | --- |
| Native Agent Skills support | Copy complete skill directories into a documented discovery location, then use the harness's skill selection or invocation mechanism. |
| File access, but no native skill support | Ask the agent to read the desired `SKILL.md` directly and follow it, loading linked templates and references as needed. |
| Chat-only, with no repository file access | Supply the desired `SKILL.md` content and any linked material it needs in the conversation. Supply project context and run checks yourself when the agent cannot. |

This makes the instructions portable across harnesses; it does **not** mean every harness automatically discovers skills or provides the same capabilities. File access, editing, command execution, user questions, and nested skill invocation depend on the host. A prompt alone cannot grant missing tools or permissions.

### 3. Install for native discovery, if supported

Check your harness's current documentation for its supported locations. Common conventions include:

- `.agents/skills/` for harnesses that recognize this project-level location.
- `.github/skills/` for GitHub Copilot environments that support it.
- `.claude/skills/` for Claude Code environments that support it.
- A documented user-level skills directory, such as `~/.agents/skills/`, if your harness supports personal skills across projects.

These are alternatives, not directories you need to create together. The nested `SDL/skills/` source location is not necessarily discovered automatically.

For example, **if your harness supports `.agents/skills/`**, first inspect the destination for same-name files or skill directories. If there are no conflicts, run the following from the target project's root to copy all 14 skills:

```sh
mkdir -p .agents/skills
cp -R /path/to/skills/SDL/skills/. .agents/skills/
```

This also copies the getting-started Markdown guide, which is not itself a skill. Its navigation links refer to this repository's layout; use the walkthrough here for the complete documentation. This example uses a POSIX-style shell; use the equivalent directory-copy operation on other platforms.

To install only one skill instead, use:

```sh
mkdir -p .agents/skills
cp -R /path/to/skills/SDL/skills/establish-architecture .agents/skills/
```

Copy the **whole skill directory**, including any `assets/` and `references/`, not just its entry point. Keep directory names unchanged. Do not overwrite or merge existing skill copies without reviewing the differences. Reload or start a new agent session if your harness requires it.

Project-local copies can be shared through the project's repository according to team policy. Personal installations avoid copying into every project, but are only available where the harness supports them. Copies do not update automatically; review upstream changes before replacing installed versions. No harness-specific plugin is required by these files.

### 4. Request a skill explicitly

Use plain language unless your harness documents a specific command syntax:

```text
Use clarify-supplied-spec to review docs/draft-spec.md.
Ask me about ambiguities, record my answers, and do not implement code yet.
```

```text
Use implement-tested-slice for the next eligible task in our delivery tracker.
Follow our approved standards and test catalog, preserve existing changes,
and report the actual validation commands and results.
```

For a harness without native discovery, use an explicit file-reading prompt:

```text
Read /path/to/skills/SDL/skills/establish-architecture/SKILL.md and follow
its procedure for this project. Read its linked templates when needed.
Start by inspecting our existing architecture documents and asking what
is missing. Ask before writing files or changing architectural decisions.
```

If another skill is needed but unavailable, load its entry point explicitly or perform the equivalent steps with the user. Do not assume that naming a skill automatically invokes it.

## Workflow and skill catalog

| Stage | Skill | Purpose and main outcome |
| --- | --- | --- |
| First step | [clarify-supplied-spec](./skills/clarify-supplied-spec/SKILL.md) | Review a supplied specification, question unknowns and contradictions, and record user responses and requirement decisions. |
| Setup | [organize-project-docs](./skills/organize-project-docs/SKILL.md) | Agree on a Markdown layout and authoritative document map while preserving existing conventions. |
| Setup | [establish-architecture](./skills/establish-architecture/SKILL.md) | Import existing architecture faithfully or capture missing decisions as reviewable ADRs. |
| Setup | [establish-coding-standards](./skills/establish-coding-standards/SKILL.md) | Confirm coding rigor, analysis/security/architecture guardrails, and repository/review practices. |
| Setup | [establish-testing-standards](./skills/establish-testing-standards/SKILL.md) | Approve coverage floors, test layers, requirement-based scenarios, and critical-path gates. |
| 1 | [define-project-contract](./skills/define-project-contract/SKILL.md) | Turn an idea or draft into reviewed scope, behavioral requirements, and an acceptance contract. |
| 2 | [analyze-architecture](./skills/analyze-architecture/SKILL.md) | Evaluate requirements against the existing system: feasibility, design alternatives, gaps, invariants, compatibility, risks, and dependencies. |
| 3 | [plan-delivery](./skills/plan-delivery/SKILL.md) | Build a dependency-ordered tracker with measurable completion criteria, blockers, and next-ready work. |
| 4 | [design-test-catalog](./skills/design-test-catalog/SKILL.md) | Connect requirements to scenarios, tests, fixtures, environments, and reproducible verification commands. |
| 5 | [implement-tested-slice](./skills/implement-tested-slice/SKILL.md) | Implement eligible work in small red-green-refactor slices with real test and coverage evidence. |
| 6 | [integrate-and-report](./skills/integrate-and-report/SKILL.md) | Verify integration under project policy and report honest status, post-integration results, and next eligible work. |
| 7 | [qualify-release](./skills/qualify-release/SKILL.md) | Execute an acceptance runbook against installed deliverables and claimed environments, recording release and compatibility evidence. |
| Across releases | [evolve-project-phase](./skills/evolve-project-phase/SKILL.md) | Prepare the next phase against the accepted baseline, preserving history and making compatibility changes explicit. |
| Throughout | [maintain-project-docs](./skills/maintain-project-docs/SKILL.md) | Keep contracts, decisions, guides, trackers, catalogs, README claims, and evidence consistent as work changes. |

These are independently usable skills, not a mandatory pipeline. A skill should inspect existing artifacts and reuse them rather than overwrite them. When a detailed spec is supplied, begin with `clarify-supplied-spec`; resolve only the document-location questions needed to save its results, then continue with relevant setup and contract finalization. Test planning and delivery planning inform each other and may be refined iteratively. For an existing project, enter at the relevant stage. Return to the appropriate earlier stage when a decision or contract changes.

## Choosing a starting point

- **You have a detailed specification:** start with `clarify-supplied-spec`, resolving only the document-location questions needed to save its results. Then finalize the relevant setup and contract.
- **You have an idea but no specification:** use `define-project-contract` to establish scope and acceptance expectations; agree on document locations before writing.
- **You are joining an existing project:** inspect its instructions and artifacts first, then select the skill that addresses the current gap. Do not recreate approved documentation unnecessarily.
- **You are ready to implement:** use the approved contract, architecture, plan, and test catalog to select an eligible task for `implement-tested-slice`, then use `integrate-and-report`.
- **You are preparing a release:** use `qualify-release`; passing unit tests alone does not establish installed-system behavior or compatibility.
- **You are starting the next phase:** use `clarify-supplied-spec` for the newly supplied spec and `evolve-project-phase` to ground planning in the prior accepted baseline.

## First step: supplied specification review

`clarify-supplied-spec` reads the supplied spec, identifies ambiguities, contradictions and missing decisions, and asks focused clarification questions. It saves actual user responses, separates them from agent interpretations, and links confirmed amendments back to requirements. Open questions retain owners, next actions, and blocking stages. The owner reviews the consolidated interpretation before handoff to `define-project-contract`; the interview itself does not authorize implementation.

Call it again for each newly supplied phase, release, or substantial spec revision. For subsequent phases it compares the new spec with the prior accepted contract, implementation baseline, limitations, and answers, and uses a separate phase-specific clarification register. Prior records are retained; changed requirements and compatibility questions require fresh confirmation.

## Markdown documentation workflow

Start with `organize-project-docs` to ask the user whether to keep existing files, adopt the following layout, or select custom paths. Paths are relative to the target project root:

```text
README.md
CONTRIBUTING.md
docs/
  README.md
  ARCHITECTURE.md
  CODING.md
  TESTING.md
  IMPLEMENTATION.md
  IMPLEMENTATION-TASKS.md
  TEST-CATALOG.md
  ACCEPTANCE-RUNBOOK.md
  adr/
    0001-decision-title.md
  specs/
    SPECIFICATION.md
    SPECIFICATION-CLARIFICATIONS.md
    PHASE2-SPECIFICATION.md
    PHASE2-SPECIFICATION-CLARIFICATIONS.md
  PHASE2-ANALYSIS.md
  PHASE2-IMPLEMENTATION-TASKS.md
  PHASE2-TEST-CATALOG.md
tests/
  unit/
  integration/
  acceptance/
```

`docs/README.md` records the agreed document map. Create ADR files only for actual decisions. Create `PHASE2-*` files only when a second phase is needed; use `PHASE3-*`, and so on for later phases. The test directories separate evidence layers; use equivalent native conventions if the project already has them. This is a proposed layout requiring user confirmation, not permission to overwrite or scaffold every file.

The skill explains the role and update triggers of each file, asks which files to create, and records the agreed role-to-path map in a user-approved index. It does not force the layout or create every file. See its [structure reference](./skills/organize-project-docs/references/document-structure.md) and [map template](./skills/organize-project-docs/assets/document-map.md).

All delivery skills resolve their document destinations through that map or existing project links before writing. Use `maintain-project-docs` to keep affected authorities, cross-links, statuses, and evidence consistent as work progresses. These two skills are independently usable; install them alongside the delivery skills for the full documentation workflow.

## Architecture and standards intake

The three `establish-*` skills ask for existing documents first. They can format and save supplied material without changing its meaning; substantive changes require confirmation. If documents are missing, they interview the user rather than inventing approved policy:

- `establish-architecture` collects decisions as ADRs with context, alternatives, rationale, consequences, and honest approval status.
- `establish-coding-standards` offers essential, strict, high-assurance, and custom guardrail profiles covering formatting, lint, typing/static analysis, review, and integration.
- `establish-testing-standards` recommends a 100% unit statement/branch coverage target, explicit 99% aggregate floors for each, and 100% changed-code coverage; integration evidence for every applicable requirement-matrix scenario; and acceptance evidence for agreed happy and critical paths. The user must confirm or customize these choices.

The 99% floor is a recommended policy, not evidence of achieved coverage. Documentation does not install enforcement. Tool/configuration changes remain separately authorized work.

## Executable structural guardrails

Coding-standards intake also asks which architecture invariants the engineer wants preserved: layer direction, package/API boundaries, forbidden dependencies, cycles, and controlled I/O boundaries. It offers Semgrep or equivalent rules, stack-specific architecture/dependency analyzers, existing custom suites, or minimal custom tests according to fit.

The [structural guardrails guide](./skills/establish-coding-standards/references/structural-guardrails.md) covers tool selection, ADR-to-rule traceability, approved rule/test locations, violating and compliant fixtures, analyzer failures, target discovery, legacy baselines, exceptions, and CI gates. Tools and invariants require confirmation; custom tooling is not the default. Architecture checks supplement behavioral testing and do not prove properties beyond their actual analysis.

## Source and dependency security controls

Coding-standards intake asks the engineer to choose the rigor of authored-code vulnerability analysis (SAST) and dependency vulnerability analysis (SCA), including resolved direct/transitive dependencies. The [security guardrails guide](./skills/establish-coding-standards/references/security-guardrails.md) covers tool selection, scope, scan schedules, advisory freshness, severity/confidence gates, triage, remediation, privacy and time-bounded risk exceptions.

Strict controls are recommended for production work, but the engineer must confirm the policy and blocking thresholds. Documented controls are not installed scanners or evidence of a clean scan.

## Repository practice

`establish-coding-standards` asks for the team's internal repository policy. Its recommended default is a dedicated branch per plan task and a completion commit after each task's implementation and pre-integration validation, including related tests, documentation, and evidence, before starting the next task. Intermediate commits are allowed; this does not mandate exactly one commit per task.

The user can choose another cadence, branching model, or review/merge strategy. Record the agreed practice and operation permissions in the coding guide. A task commit alone does not mean DONE: required review, integration, and post-integration validation must still pass.

## Adaptation and guardrails

- Agree on acceptance, quality, coverage, platform, branching, and approval policies for each project. Recommended profiles and thresholds require explicit confirmation; do not silently replace existing standards.
- Prefer evidence from actual commands, actual environments, and independently observed state. Planned checks, passing unit tests, and an accepted specification are not proof of installed-system behavior or release readiness.
- Preserve existing user changes. Do not commit, merge, tag, change support claims, use external services, or make destructive changes without the applicable authorization. Ask the owner about material scope tradeoffs; record approved decisions.
- Stop and surface blockers, unexpected failures, insufficient permissions, or missing environments. Do not hide failures by narrowing tests or quietly downgrading requirements.
- Use the project's own tools, naming, policies, and documentation. These skills describe the process, not a mandated stack.
- If the harness cannot ask structured questions, ask in chat and wait. If it cannot run a required check, report the limitation and request operator evidence rather than claiming success.

## Evidence and limits

These skills guide a workflow; they do not prove that a check ran, a project is complete, or a release is certified. Record actual commands, results, candidate revisions, and environments in the agreed project artifacts. Installed-system checks and compatibility qualification must match the product's real boundaries and supported environments.

Review generated changes and evidence. These skills do not guarantee correctness, security, or certification.

## Author and license

Created by **[Allan Cascante](https://github.com/allancascante)** and distributed under the [MIT License](../LICENSE).
