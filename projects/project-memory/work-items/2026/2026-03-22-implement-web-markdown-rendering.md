---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: implement-web-markdown-rendering
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Add safe Markdown rendering for managed document bodies in the Web UI.

## Outcome

The Web layer has a dedicated, safe Markdown-to-HTML rendering path for managed document bodies that can be reused by exact document and composed reading views.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:implement-web-document-view

## Context

- canonical-doc:project-memory:document-model:document-model

## Verification

- Add a dedicated Markdown rendering path for managed document bodies rather than treating body text as raw HTML.
- Preserve common Markdown structures needed by repository documents, including headings, lists, links, and code blocks.
- Avoid executing raw HTML or script content unless a later decision explicitly allows it.
- Reuse the same renderer for exact document and composed reading views.
- Document any deliberate renderer limitations needed for the first implementation.

## Evidence

- none
