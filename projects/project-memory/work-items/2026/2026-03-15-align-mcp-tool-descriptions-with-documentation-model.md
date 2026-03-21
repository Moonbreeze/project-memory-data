---
date: 2026-03-15
recorded_at: 2026-03-15T00:00:00.000Z
project: project-memory
topic: align-mcp-tool-descriptions-with-documentation-model
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Align MCP tool descriptions with the documented project-memory operating model for external tool-using agents.

## Outcome

An external MCP consumer that sees only the tool catalog and tool descriptions can infer the same document-role semantics, bounded-read startup pattern, and managed-surface boundaries that are currently explained in repo docs.

## Provenance

- ad-hoc: Documentation review found that external MCP consumers only see tool descriptions, and those descriptions currently under-express the document model and bounded-read workflow explained in the public and managed docs.

## Dependencies

- none

## Context

- none

## Verification

- Audit MCP tool descriptions against README, docs/usage.md, docs/architecture.md, and the managed documentation strategy records.
- Add machine-facing guidance for when to use work-item, session-note, decision, verification-result, canonical-doc, runbook, and provider-note.
- Make the query surface communicate bounded-reads-first behavior instead of presenting list/search as equally suitable startup paths.
- Clarify managed path-model and validation boundaries so tool users understand why unmanaged files are invisible or rejected.
- Explain lifecycle expectations around work-item opening, evidence recording, durable decision capture, canonical guidance updates, and work-item closure where that guidance materially affects tool choice.
- Verify that an external MCP consumer with no AGENTS.md or CLAUDE.md context can still recover the intended operating model from tool descriptions alone.

## Evidence

- session-note:project-memory:2026-03-15:align-mcp-tool-descriptions-with-documentation-model
- verification-result:project-memory:2026-03-15:align-mcp-tool-descriptions-with-documentation-model
