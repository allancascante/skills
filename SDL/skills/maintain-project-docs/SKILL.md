---
name: maintain-project-docs
description: "Maintain coherent Markdown project documentation throughout development. Use when updating specs, design decisions, coding/testing guides, roadmaps, implementation trackers, test catalogs, acceptance evidence, README claims, or next-phase records after changes."
---

# Maintain project documentation

Keep the project's Markdown files useful as a connected record of contract, process, plan, and evidence, not a collection of duplicated summaries.

## Procedure

1. Locate the agreed document map and follow existing README/guide links. If a necessary destination is not agreed, ask the user whether to reuse the existing layout, use the bundle's explicit documentation structure, or choose custom paths before creating files. Use `organize-project-docs` if available; otherwise perform this discovery and choice directly. Do not invent a new documentation tree.
2. Identify the change and its affected authorities:
   - Requirements, scope, support, or compatibility: owner-approved contract, design decisions, affected roadmap/tasks/scenarios, and public claims.
   - Component boundaries or invariants: architecture and relevant phase analysis, then affected scenarios.
   - Engineering/testing policy or commands: contributor/coding/testing guides; verify against actual configuration.
   - Task start or progress: tracker status, selected exact test matrix, dependencies, and remaining work.
   - Validation or integration: tracker evidence and revisions, independent test-layer states, catalog evidence links, and outstanding blockers.
   - Qualification: runbook procedure and separate execution results; update README support claims only as evidence warrants.
   - New phase: separately identified contract, analysis, tracker and catalog; link from entry points and preserve prior records.
3. Read affected sections and update the smallest coherent set. Reuse stable requirement/task/scenario IDs and relative links. Keep each detailed fact in its authoritative location and link summaries to it; do not copy raw output across multiple documents.
4. Preserve distinctions between proposed, approved, planned, implemented, tested, integrated, and qualified. Record actual commands, results, environment versions, revision identifiers, failures, and gaps. Never invent approvals or historical red runs, erase unresolved failures, or upgrade task status from weaker evidence.
5. Ask the owner about material scope/support changes and conflicting authorities. Do not rename/move documents or rewrite prior phase evidence without permission. Keep unrelated work intact.
6. Check relative links and anchors, unchanged ID references, task dependencies/status consistency, command/configuration accuracy, and capability/support claims. Mark future documents as planned rather than making broken links. Run documentation-specific checks if available; Markdown-only updates do not need unrelated application tests unless project policy requires them.
7. Report which authorities changed, what checks actually ran, any inconsistencies left unresolved, and the next required decision.

## Done when

The documents agree about scope and status, evidence remains traceable, agreed paths are respected, and readers can distinguish what is intended from what actually passed.
