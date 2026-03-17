---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: project-memory
topic: search-and-read-surface-redesign
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Redesign the query surface so search_documents is a recall-oriented entrypoint by default, read_document remains the explicit full-retrieval surface, and choose_workflow steers agents toward the intended two-step search-then-read pattern.

## Outcome

The project has a tracked implementation slice for separating keyword recall from full document retrieval, reducing default search payload size, clarifying MCP tool descriptions, and updating choose_workflow guidance so agents use search_documents to find candidates and read_document to open specific documents.

## Provenance

- ad-hoc: Planned from discussion about TOON, search payload semantics, and clearer recall versus retrieval boundaries for MCP tools.

## Dependencies

- none

## Context

- none

## Verification

- Verify CLI and MCP search outputs support a concise default shape with excerpt-centered hits and an opt-in path for full body retrieval.
- Verify read_document remains the explicit full-document retrieval surface after the redesign.
- Verify MCP tool descriptions for search_documents and read_document clearly distinguish recall from retrieval semantics.
- Verify choose_workflow guidance explicitly recommends the search -> read pattern when keyword recall is followed by opening a concrete document.

## Evidence

- none
