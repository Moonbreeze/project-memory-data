---
date: 2026-03-15
project: project-memory
topic: align-mcp-tool-descriptions-with-documentation-model
source: agent
status: active
---
# Session Note

## Summary

Aligned the MCP tool catalog with the documented operating model and added a fallback workflow chooser for external agents that only see the MCP surface.

## Actions

- Expanded MCP tool descriptions so the catalog now explains document-role semantics, bounded-read startup choices, same-project planning scope, managed-surface boundaries, and the normal documentation lifecycle.
- Clarified the work-item dual-axis model in the MCP schema by distinguishing document visibility status from execution progress workItemState.
- Added the read-only choose_workflow MCP tool to recommend the right bounded read or next lifecycle step when an agent is unsure which tool to call.
- Adjusted topic-entry notes so exact-topic work items are explicitly redirected toward planning-topic-entry instead of looking like missing exact matches.
- Ran the full automated test suite after the MCP surface and chooser changes.

## Follow-up

- Watch whether external MCP consumers still need stronger structured routing hints beyond the fallback chooser tool.
