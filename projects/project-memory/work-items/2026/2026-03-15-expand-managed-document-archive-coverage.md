---
date: 2026-03-15
recorded_at: 2026-03-15T00:00:00.000Z
project: project-memory
topic: expand-managed-document-archive-coverage
source: agent
status: archived
work_item_state: done
---
# Work Item

## Summary

Expand archive coverage so managed document types beyond session-note, verification-result, and work-item can be archived through supported project-memory operations.

## Outcome

Project-memory provides explicit, validated archive semantics and user-facing archive operations for the remaining managed document types, so cleanup and lifecycle transitions no longer depend on manual file edits or ad-hoc repository moves.

## Provenance

- ad-hoc: Audit of misused runbooks showed that archive support is currently uneven: session-note and verification-result have explicit archive flows, work-items have a dedicated archive operation, but runbook, decision, canonical-doc, and provider-note still require manual status edits or manual file moves.

## Dependencies

- none

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Document the current archive behavior and identify which managed document types still lack supported archive operations.
- Define archive semantics per document type, including whether archival is a status-only transition, a path move, or a type-specific lifecycle operation.
- Implement the required core and CLI or MCP archive flows for the missing document types without weakening existing validation rules.
- Add automated coverage for the new archive paths and verify that unsupported archive attempts still fail clearly when semantics are intentionally disallowed.

## Evidence

- session-note:project-memory:2026-03-15:expand-managed-document-archive-coverage
- verification-result:project-memory:2026-03-15:expand-managed-document-archive-coverage
