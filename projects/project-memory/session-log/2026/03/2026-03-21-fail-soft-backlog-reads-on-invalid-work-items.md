---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: fail-soft-backlog-reads-on-invalid-work-items
source: agent
status: active
---
# Session Note

## Summary

Implemented fail-soft mass-read handling for invalid work-item documents so backlog-facing reads return usable results plus explicit diagnostics instead of aborting on the first invalid done item.

## Actions

- Added invalid-document diagnostics to bounded-read and list-documents result types.
- Introduced a shared mass-read helper that skips invalid work-item documents while preserving strict direct-read behavior.
- Updated planning backlog/topic and list-documents aggregation paths to surface skipped invalid work-item diagnostics.
- Added Bug #1 regression coverage in core and MCP tests and created tests/KNOWN_BUGS.md for the repository test root.
- Ran the full npm test suite after the retrieval and test changes.

## Follow-up

- Consider whether search_documents should adopt the same diagnostic pattern for invalid work-item skips instead of remaining strict.
