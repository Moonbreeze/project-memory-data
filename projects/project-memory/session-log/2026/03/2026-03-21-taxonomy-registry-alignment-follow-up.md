---
date: 2026-03-21
recorded_at: 2026-03-21T00:00:00.000Z
project: project-memory
topic: taxonomy-registry-alignment-follow-up
source: user
status: active
---
# Session Note

## Summary

Validated the live taxonomy registry for `project-memory`, fixed the duplicate-authority conflict on scope `system` by separating repository-documentation into its own scope, confirmed the audit passes, and checked repo-local docs against the current canonical guidance.

## Actions

- Read the active taxonomy registry and confirmed the reserved registry surface already existed for `project-memory`.
- Ran a taxonomy audit, identified the duplicate-authority error on scope `system`, and inspected the conflicting canonical docs.
- Updated the taxonomy registry entries so `system-overview` remains the authority for scope `system` and `repository-documentation-strategy` now owns a dedicated `repository-documentation` scope.
- Created the new active `repository-documentation-strategy` canonical doc under `canonical-docs/repository-documentation/` and archived the older conflicting `system`-scoped copy.
- Re-ran the taxonomy audit and confirmed the project now passes with no findings.
- Reviewed `README.md`, `docs/usage.md`, and `docs/architecture.md` against the canonical repository-documentation guidance and found no substantial repo-doc changes necessary in this slice.
- Recorded a separate backlog item for the MCP/agent UX defect where allowed taxonomy migration enum values were not surfaced clearly to the agent-facing tool contract or validation errors.

## Follow-up

- Implement the separate work item `surface-taxonomy-migration-enums-and-actionable-validation-errors` so enum-constrained tool inputs are discoverable without source inspection.
- Optionally commit the resulting project-memory document updates once this execution slice is fully wrapped.
