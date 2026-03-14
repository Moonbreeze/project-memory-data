---
date: 2026-03-14
project: project-memory
topic: list-documents-closure
source: agent
status: active
---
# Session Note

## Summary

Closed the list_documents follow-up by switching list output to metadata-only by default, adding explicit includeBody support plus filter/sort options, and introducing a transparent backlog preset for active decisions.

## Actions

- Changed list_documents to return metadata-only results by default and require explicit includeBody for full Markdown bodies.
- Added list_documents query controls for status, excludeStatuses, sort, order, and preset, with backlog expanding to the current active decision view.
- Updated CLI, MCP schemas, README, and automated coverage to reflect the new list_documents contract and backlog preset behavior.
- Validated the change with npm test and npx tsc --noEmit.

## Follow-up

- Handle canonical project-document support in a separate session rather than extending the current list_documents closure work.
- When canonical-doc support starts, review whether additional list_documents presets or document types are needed beyond the current decision backlog view.
