# Getting started: watch the skills in action

**Author: [Allan Cascante](https://github.com/allancascante)**

Try the skills in a small, disposable project before adopting them in production. This walkthrough uses a command-line task tracker to demonstrate clarification, planning, test-driven implementation, and release qualification.

## Before you start

- Clone this repository and note its absolute path.
- Use an agent harness that can read project files. Editing and command execution are needed for the agent to implement and validate the demo itself.
- Replace `/path/to/skills` in every prompt below with the absolute path to this repository.
- If the harness cannot access files outside the project, copy complete skill directories into a supported discovery location and adjust the prompts to those paths. See the [installation guide](../README.md#use-in-any-project).
- If the harness cannot execute commands, run the checks yourself and supply their actual output. Missing capabilities must be reported, not treated as passing checks.

Direct file-reading prompts let you test the workflow without relying on automatic skill discovery. Test native discovery separately once the process works.

## 1. Create a disposable project

On macOS or Linux, run:

```sh
mkdir ~/skill-process-demo
cd ~/skill-process-demo
git init
```

Choose another directory name if it already exists; do not reuse an important project. On other platforms, create an empty folder and initialize Git using the equivalent commands.

Open the new folder in your coding-agent harness and start a fresh conversation.

## 2. Supply a deliberately incomplete specification

Paste this prompt:

```text
I want to test a specification-led delivery process in this disposable project.

Read /path/to/skills/SDL/skills/clarify-supplied-spec/SKILL.md
and follow its procedure. Read linked references or other skill files as needed.

Draft specification:
Build a small command-line task tracker.
Users can add tasks, list tasks, and mark tasks complete.
Tasks should persist between runs.
Invalid commands should produce useful errors.
Use a stack already installed on this machine, confirming the choice with me.

Start by reviewing this specification and asking clarification questions.
Do not implement code yet.
Ask before choosing documentation locations.
Do not commit, use external services, or install dependencies without permission.
```

**What you should see:** questions about missing decisions, such as task IDs, storage location, completed-task visibility, and error behavior. The agent should not immediately build the application.

Answer the questions and review the recorded interpretation. Actual user answers should remain distinguishable from agent assumptions, and unresolved questions should remain visible.

## 3. Establish the project and plan delivery

After reviewing the clarification register, send:

```text
Continue with these skills, loading each SKILL.md from
/path/to/skills/SDL/skills/<skill-name>/SKILL.md:

1. organize-project-docs
2. establish-architecture
3. establish-coding-standards
4. establish-testing-standards
5. define-project-contract
6. analyze-architecture
7. plan-delivery
8. design-test-catalog

Keep this proportional to a tiny demonstration project.
Reuse existing documents rather than duplicating them.
Ask for decisions and approvals where required, and wait for my answers.
Refine delivery planning and test planning together when needed.
Stop before implementation so I can review the contract, plan, and test catalog.
The earlier restrictions on commits, external services, and dependency
installation still apply.
```

This is a sequence of interactive steps, not authorization to skip questions or approvals. If your harness cannot load several skills in one request, request them individually using the same entry-point pattern.

**What you should see:**

- An agreed document map rather than an imposed folder structure.
- Explicit requirements and acceptance expectations.
- A small architecture with honest decision/approval status.
- Coding and testing standards you have confirmed.
- Dependency-ordered tasks with measurable completion criteria.
- A test catalog connecting requirements, scenarios, and verification.

Review these artifacts before authorizing implementation. Documented standards do not mean enforcement tools have been installed or checks have run.

## 4. Watch one test-driven implementation cycle

Once you approve the relevant artifacts, send:

```text
Read /path/to/skills/SDL/skills/implement-tested-slice/SKILL.md
and use it for the smallest eligible task.

Show the selected scenario and test first.
Run it and record the expected failure, implement the minimum solution,
then rerun the relevant tests and refactor if needed.
The initial test should fail for the missing behavior, not an unrelated
environment or dependency problem.

Read /path/to/skills/SDL/skills/maintain-project-docs/SKILL.md
and use it to keep the agreed artifacts current.

Stop after this slice and report actual commands, results, and remaining work.
Do not commit, merge, use external services, or install dependencies
without permission.
```

**What you should see:** a meaningful failing test, an implementation, and a passing test, with actual command output or recorded results. The agent should preserve relevant behavior and report any required checks it could not run.

A passing slice is not necessarily a completed task: more slices, review, integration, or post-integration validation may still be required.

## 5. Finish the tasks and check integration

Review each slice, then authorize the next eligible slice until the agreed scope is implemented. Request:

```text
Read /path/to/skills/SDL/skills/integrate-and-report/SKILL.md
and follow it under our approved repository policy.

Check task completion against the contract and test catalog.
Run the required integration and post-integration checks where applicable.
Report completed, partial, blocked, and remaining work with actual evidence.
Ask before any commit or merge; do not treat this prompt as permission.
If integration requires an operation I have not authorized, report that
gate as pending rather than marking it complete.
```

**What you should see:** evidence-based status, not a blanket claim that everything is done because unit tests passed.

## 6. Qualify the demo through its real entry point

Once the CLI is usable, send:

```text
Read /path/to/skills/SDL/skills/qualify-release/SKILL.md
and follow its procedure.

Validate the CLI through its actual installed or packaged entry point,
not only unit tests. Use the delivery method agreed in the contract.
Ask before installation or other operations that require authorization.

Verify add, list, completion, persistence between separate processes,
and invalid-command behavior.
Record actual commands, results, candidate revision or worktree state,
and the environment tested.
Report any untested environments and qualification gaps explicitly.
Do not publish, tag, commit, or claim unsupported compatibility.
```

**What you should see:** a reproducible acceptance runbook and executed evidence for the agreed deliverable. The result should distinguish tested behavior from untested environments and unresolved release gates.

## How to judge the trial

The workflow is behaving as intended when the agent:

- Asks about ambiguities before inventing requirements.
- Gets approval for document locations, standards, and material decisions.
- Reuses project conventions and preserves existing changes.
- Connects requirements to scenarios, tasks, tests, and evidence.
- Demonstrates a real failing-test-to-passing-test implementation cycle.
- Reports actual checks and failures without hiding missing tools or environments.
- Distinguishes planned, implemented, verified, integrated, and release-qualified work.
- Stops at permission or approval gates rather than treating a skill as blanket authorization.

This is a manual smoke test of the workflow, not an automated certification of skill quality or harness compatibility. If a stage goes off track, keep the prompt, observed behavior, and relevant output so you can reproduce and improve it.

For the full skill catalog, see the [SDL skill catalog](../README.md#workflow-and-skill-catalog). For detailed workflow rules and handoffs, see the [SDL guide](../README.md), or return to the [repository overview](../../README.md).
