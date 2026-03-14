---
date: 2026-03-14
project: project-memory
topic: document-model-refinements-follow-up
source: agent
status: active
---
# Session Note

## Summary

Extended the document-model baseline with explicit decisions for topic and scope registry plus work-item provenance, and added operational runbooks for read entrypoints and authority or archive policy. These refinements sharpen the upcoming canonical-doc and work-item design without changing the earlier direction.

## Actions

- Recorded that topic categorization should be treated as a first-class information layer backed first by a canonical registry document rather than by informal tags alone.
- Recorded that future work items may originate ad hoc as long as they carry minimal provenance instead of requiring a pre-existing decision or session note.
- Added a baseline read-entrypoint runbook covering cold start, topic lookup, rationale lookup, work planning, change execution, verification lookup, and bounded cross-project impact reads.
- Added a policy runbook covering authoritative scope ownership, conflict resolution, partial migration, work-item archival, canonical-doc supersession versus archival, and cross-project authority boundaries.

## Follow-up

- Translate the new registry decision into concrete canonical-doc requirements for the first taxonomy registry artifact.
- Decide how the future work-item schema should encode origin metadata and close-state transitions.
- Use the read-entrypoint baseline to define the first specialized list, search, or lookup operations needed beyond the current backlog preset.
