---
name: establish-architecture
description: "Collect and document a project's architecture with the user. Use when importing an existing architecture document, formatting and saving architectural guidance, or eliciting missing architecture decisions as Architecture Decision Records (ADRs)."
---

# Establish architecture with the user

Capture the user's architecture, not an architecture invented on their behalf. This is intake and documentation; `analyze-architecture` performs subsequent gap and design analysis.

## Procedure

1. Inspect existing project instructions and documentation links. Resolve architecture and decision-record destinations through the agreed document map. If missing, ask about locations with `organize-project-docs` or offer `docs/ARCHITECTURE.md` and `docs/adr/` explicitly as proposed defaults. Do not write to unconfirmed locations.
2. Ask whether the user has architecture documents, diagrams, decision records, or notes. Request accessible file paths or supplied content and ask whether the scope is formatting-only or also substantive review. Use a structured question tool when available; otherwise ask in chat and wait. Do not send private documents to external services.
3. If supplied, read the sources and preserve their meaning, constraints, terminology, decision status, and provenance. Normalize headings, tables, links, and Markdown layout into the agreed architecture location. Preserve referenced diagrams or ask how to retain them; disclose unreadable or inaccessible portions. Ask before changing decisions or splitting/moving existing records. Formatting alone must not invent missing decisions, rationale, or approval.
4. If absent or incomplete, explain ADRs and ask the user to collect architecture decisions using the [ADR template](./assets/adr-template.md). Offer to interview them and draft one record per consequential decision. Ask about context, constraints, alternatives, chosen option, rationale, consequences, and status. Cover applicable system boundaries, stack, data ownership/storage, interfaces, deployment, security, failure/recovery, concurrency, and compatibility. Do not force irrelevant topics or turn unknowns into accepted decisions.
5. Assign stable ADR IDs using existing conventions; offer `ADR-0001` / `0001-short-title.md` if none exist. Keep unanswered choices proposed or unresolved. Ask the user to review and confirm acceptance; a draft is not an approved architecture.
6. Save approved documentation at the agreed paths. The architecture overview should summarize context, components/flows, key invariants and constraints, and link to ADRs and requirements. Supersede accepted decisions with new linked records rather than silently rewriting history. Do not create empty records for every possible topic.
   Ask which invariants should become executable guardrails, such as layer direction, package boundaries, forbidden dependencies and cycles. Record the intended dependency graph and link approved constraints to ADRs. Hand tool/rule selection to `establish-coding-standards` when available; distinguish static enforcement, behavioral verification and manual review. Do not install tools or invent structural restrictions as part of formatting-only intake.
7. Update the agreed document map and entry-point links with `maintain-project-docs` or equivalent direct updates. Check links and consistency with the supplied sources. Report what was imported, reformatted, proposed, approved, and still missing. Route substantive analysis to `analyze-architecture` only if requested or needed by the delivery task.

## Done when

Existing architecture has been faithfully formatted and saved, or missing decisions have been collected into reviewable ADRs with honest statuses. Unresolved decisions and approval gaps remain visible.
