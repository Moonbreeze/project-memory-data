---
date: 2026-03-15
project: project-memory
topic: compact-mcp-write-tool-results
source: agent
status: active
work_item_state: done
---
# Work Item

## Summary

Reduce unnecessary context bloat from MCP write and archive tool results by returning compact payloads by default.

## Outcome

Mutating MCP tools return compact structured results by default, with full document bodies available only through explicit read flows or opt-in behavior, and the text content no longer mirrors large payloads unnecessarily.

## Provenance

- ad-hoc: Audit of MCP result handling showed that mutating tools currently return full changed documents, including body, and also duplicate the payload as JSON text content, which can waste agent context.

## Dependencies

- none

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Define the default compact result shape for mutating MCP tools such as append, record, create, upsert, close, and archive operations.
- Preserve compatibility for MCP clients that rely on structured payloads, or document any intentional contract change clearly.
- Ensure full document bodies remain available through read_document or an explicit opt-in path instead of every write response.
- Add automated coverage showing that write and archive tool responses no longer include unnecessary full-body payloads by default.

## Evidence

- session-note:project-memory:2026-03-15:compact-mcp-write-tool-results
- verification-result:project-memory:2026-03-15:compact-mcp-write-tool-results
