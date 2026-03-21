---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: search-and-read-surface-redesign
source: agent
status: active
---
# Session Note

## Summary

Implemented the search/read surface redesign so search defaults to compact recall hits, full document bodies are opt-in, and chooser guidance recommends the search-then-read flow.

## Actions

- Changed the search result contract to return compact hits by default without full document bodies or absolute paths.
- Added opt-in includeBody support through core search, CLI search-documents, and the MCP search_documents parser/schema.
- Updated MCP tool descriptions and choose_workflow guidance to distinguish recall-oriented search from explicit full-document retrieval via read_document.
- Added and updated core, CLI, and MCP tests covering compact search hits, opt-in body retrieval, and the search -> read guidance path.

## Follow-up

- Update the work-item evidence with the new session-note and verification-result locators.
- Close the search-and-read-surface-redesign work-item now that implementation and verification are recorded.
