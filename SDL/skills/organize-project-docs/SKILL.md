---
name: organize-project-docs
description: "Set up a project's Markdown documentation structure with the user. Use when deciding where specs, architecture, coding/testing guides, roadmaps, task trackers, test catalogs, acceptance runbooks, or phase documents belong, or when adapting an existing documentation layout."
---

# Organize project documentation

Agree on document locations and responsibilities before creating workflow artifacts. Offer the explicit layout in the bundled reference as an option, not a requirement. The location of installed skills is separate from the location of project documentation.

## Procedure

1. Inspect the project's existing Markdown files, README links, instructions, and documentation conventions. Identify existing authoritative documents, active phases, ownership, and naming conflicts. Do not move, overwrite, or duplicate them.
2. Present what already exists and ask the user to choose:
   - Keep and map the existing structure.
   - Use the [suggested structure and document roles](./references/document-structure.md).
   - Use a custom location and naming scheme.
   Ask where the documentation root, specification directory, developer guides, and phase records should live, and which documents should be created now. Offer root `README.md` and `CONTRIBUTING.md` plus `docs/` as defaults, not assumed decisions. Use a structured question tool when available; otherwise ask in chat and wait.
3. Show the proposed paths and explain each document's authority. Distinguish product requirements, design rationale, process policy, planned work, actual task evidence, scenario definitions, and executed acceptance results. Resolve conflicts with the user before writing.
   Ask for existing architecture, coding, and testing documents before drafting their contents. Route intake to `establish-architecture`, `establish-coding-standards`, and `establish-testing-standards` when available; otherwise ask for sources, preserve their meaning, and obtain user decisions before drafting missing standards. Offer an ADR location for missing architecture decisions, not invented accepted architecture.
4. Ask where to record the agreed role-to-path map: an existing documentation index is preferred; a new index such as `docs/README.md` is optional and requires agreement. Use the [map template](./assets/document-map.md) as a starting point, adapting it to the chosen location. Mark absent documents as planned or not applicable rather than linking to nonexistent files.
5. Create or update only approved artifacts, using the role outlines in the reference. Populate them with known content and visible open questions; do not generate empty copies of every suggested file or invent decisions, approvals, commands, or test evidence. Ask separately before moving existing files or changing established authorities.
6. Link the agreed map from the project README or another approved discovery entry point. Use relative links and stable IDs. If agent routing is requested, follow that harness's conventions and link to guides rather than duplicating their policies; do not assume Markdown instructions enforce behavior.
7. Check local links, headings, role coverage, and naming consistency. Summarize created, reused, planned, and intentionally omitted documents, the confirmed map location, and any unresolved choices.

## Standalone and downstream use

All workflow skills should resolve document roles through the agreed index and existing README links. When no map exists, apply this discovery and user-choice procedure before choosing new paths. Do not ask again for already confirmed paths unless they conflict or no longer fit.

## Done when

The user has confirmed the layout and creation scope, document roles have unambiguous destinations, and approved files are discoverable without broken links or duplicate sources of truth.
