---
date: 2026-03-14
project: project-memory
topic: read-only-web-interface
source: user
status: active
---
# Decision

## Context

Project-memory documents are currently accessible only through MCP tools or direct filesystem access. A lightweight web interface for browsing project documentation and viewing a timeline of decisions, session notes, and other document types would make the knowledge base accessible to humans without terminal tooling. However, the document model is actively evolving: canonical docs and work-items are not yet implemented, and building a UI on top of an unstable schema would lead to rework.

## Decision

Implement a read-only web interface for browsing project-memory documents with a timeline view. This work must not begin until canonical-doc and work-item document types are implemented and their lifecycles are stable. The interface must remain read-only — the source of truth stays in the filesystem, and all writes go through MCP tools or CLI.

## Consequences

- Web interface implementation is explicitly blocked until canonical-doc and work-item support is complete and lifecycle-stable.
- First version scope is strictly read-only: timeline view, filtering by project and document type, markdown rendering. No editing, no write operations.
- Source of truth remains in markdown files with frontmatter — the web layer is a projection, not a separate data store.
- Scope creep toward editing, search, or graph visualization should be evaluated as separate decisions after the read-only baseline is delivered.
- The static or server-side implementation should reuse the existing TypeScript codebase and markdown parsing already present in project-memory.
