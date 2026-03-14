---
date: 2026-03-14
project: project-memory
topic: taxonomy-registry-session-2
source: agent
status: active
---
# Session Note

## Summary

Implemented minimal canonical-doc support in the project-memory tool repo using the Session 1 taxonomy-registry baseline without expanding the taxonomy model.

## Actions

- Added managed document type `canonical-doc` with path/layout rules under `projects/<project>/canonical-docs/<registry_scope>/<topic>.md`.
- Added canonical-doc template, core upsert semantics, frontmatter support for `registry_scope`, and validation requiring declared scope metadata for canonical docs.
- Extended list/read/search and commit-scope handling to include canonical docs, including `docs(canonical)` commit messages.
- Added CLI `upsert-canonical-doc`, MCP `upsert_canonical_doc`, bootstrap/install directory support, and tests across core, CLI, and MCP layers.
- Updated README and MEMORY_POLICY to reflect canonical docs and the new canonical commit scope.

## Follow-up

- Session 3 can extend canonical-doc structure and registry linkage beyond the minimal `registry_scope` boundary if needed.
- If taxonomy registry becomes a first-class managed document type later, migrate canonical-doc linkage from baseline assumptions to explicit registry reads.
- Decide whether canonical docs need richer body sections or stricter cross-project mapping validation in a later session.
