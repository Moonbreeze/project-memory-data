---
date: 2026-03-15
project: project-memory
topic: expand-managed-document-archive-coverage
source: agent
status: active
---
# Session Note

## Summary

Implemented expanded archive coverage across core, MCP, tests, and public docs for managed document types that previously required manual archival handling.

## Actions

- Extended archiveDocument so session notes and verification results still move into archives/ while provider notes, decisions, runbooks, and canonical docs archive in place by switching to archived status.
- Added MCP archive_document support and test coverage for core, CLI, and MCP flows, including explicit rejection of work-item paths through the generic archive helper.
- Updated README and architecture docs to explain user-facing archive behavior and contributor-facing rationale for status-based archive semantics.

## Follow-up

- none
