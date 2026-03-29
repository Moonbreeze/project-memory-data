---
date: 2026-03-29
recorded_at: 2026-03-29T06:20:04.378Z
project: project-memory
topic: web-search-route-and-collapsible-control-pattern
source: agent
status: active
---
# Decision

## Context

The baseline read-only Web interface decision established the Web UI as a read-only projection and explicitly left search for a later decision. Subsequent implementation work added a sticky timeline shell, explicit URL-driven filter controls, default project selection, semantic previews, and a mobile accordion pattern, but those refinements were still captured only in work-item and session-note history rather than in durable stable guidance. At the same time, shared-core search already exists with latest-first ordering and compact excerpts, but its contract does not include a `status` filter or a relevance-ranking layer. The Web UI therefore needs an explicit decision for how search should be exposed without silently inventing new shared-core semantics, and it needs a reusable collapsible-control pattern so search and future demand-driven controls do not duplicate one-off toggle markup.

## Decision

Expose Web search as a dedicated read-only `/search` route rather than as a permanently expanded form inside the timeline shell. The first Web search implementation must remain a thin wrapper over the existing shared-core `searchDocuments` behavior, using `q`, `project`, `type`, and `limit` as the shareable URL contract and preserving latest-first ordering and shared-core excerpt behavior. Do not introduce a Web-only `status` filter, body-in-URL contract, highlighting layer, or independent relevance-ranking semantics in v1. The timeline view should surface search as a compact on-demand entry point, while the `/search` page should show a visible summary of the active query scope and collapse the search form by default after a query has been executed. Generalize the existing timeline accordion pattern into a narrow reusable Web collapsible-control primitive with explicit display modes for `mobile-only` and `always` behavior instead of copying ad hoc toggle markup for each new control surface.

## Consequences

- Web search stays aligned with the existing shared-core query semantics instead of creating a divergent Web-only search model.
- The Web UI gains a shareable dedicated search route without giving search permanent visual weight in the timeline browsing shell.
- The approved search UX still leaves room for later decisions about status-aware search, highlighting, or relevance ranking once the shared core evolves.
- Future Web controls can reuse one collapsible-control primitive rather than re-embedding checkbox-toggle markup and CSS in each view.
- Recent Web UI refinements now have a stable decision-level anchor that can be referenced by canonical guidance and implementation work-items.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Added a dedicated Web UI stable-guidance decision for on-demand search routing and reusable collapsible controls, to be reflected in the new `web-ui` canonical scope rather than by rewriting the older baseline decision.
