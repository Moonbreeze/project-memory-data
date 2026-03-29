---
date: 2026-03-29
recorded_at: 2026-03-29T06:20:29.276Z
project: project-memory
topic: read-only-web-ui-guidance
registry_scope: web-ui
source: agent
status: active
---
# Canonical Doc

## Summary

The read-only Web UI is a human-facing projection over shared-core reads with a latest-first timeline entrypoint, explicit URL-driven controls, compact browsing context, on-demand search, and reusable collapsible-control guidance for future Web surfaces.

## Guidance

- Keep the Web UI as a read-only projection over the shared core and `PROJECT_MEMORY_ROOT`; the filesystem remains the source of truth and Web routes must not invent a parallel write path or hidden state model.
- Treat the timeline as the default Web browsing entrypoint and inherit shared-core latest-first chronology rather than redefining ordering semantics inside the Web layer.
- Allow the base timeline view to default to the most recent project while preserving an explicit `All projects` option and keeping project, type, and status controls synchronized with shareable query parameters.
- Use the sticky browsing shell to keep current scope, controls, and context visible without turning the timeline into a dense form-first screen.
- Present semantic previews above metadata in timeline rows so the page supports quick scanning before exact-document navigation, while leaving metadata as secondary browsing context.
- Expose search as an on-demand dedicated `/search` route instead of a permanently expanded timeline form, and preserve return navigation through the same normalized `from`-style URL flow used elsewhere in the Web UI.
- Keep the initial Web search implementation as a thin wrapper over shared-core `searchDocuments`, with `q`, `project`, `type`, and `limit` as the shareable route contract and without adding Web-only `status`, highlighting, body-in-URL, or independent relevance-ranking semantics.
- When a search query has already been executed, keep the current query scope visible in the page shell and collapse the search form by default so search remains available without permanently consuming vertical space.
- Prefer a reusable Web collapsible-control primitive for demand-driven controls such as timeline filters on mobile and search controls across viewports; the primitive should support explicit `mobile-only` and `always` display modes instead of encoding one control's layout assumptions into every future panel.

## References

- decision: read-only-web-interface
- decision: document-timeline-and-latest-first-query-defaults
- decision: web-search-route-and-collapsible-control-pattern
- canonical-doc: document-model
- canonical-doc: bounded-read-model
