---
date: 2026-03-15
project: project-memory
topic: compact-mcp-write-tool-results
source: agent
status: active
---
# Session Note

## Summary

Implemented compact MCP write/archive result shaping to reduce context bloat from managed document mutations.

## Actions

- Added per-tool MCP result modes so mutating tools can return compact document payloads without affecting read/list behavior.
- Removed default document body payloads and full JSON mirroring from mutating MCP tool responses, replacing them with short summaries plus compact structured content.
- Added MCP server coverage for append, close, archive-work-item, and archive-document compact result behavior.
- Committed the code changes in the tool repository as ff993c9 (feat(mcp): compact write tool results).

## Follow-up

- Consider an explicit opt-in path if any MCP client later needs full write-result document bodies without a separate read_document call.
