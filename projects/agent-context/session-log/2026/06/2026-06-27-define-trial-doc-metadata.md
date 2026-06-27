---
date: 2026-06-27
recorded_at: 2026-06-27T10:38:14.533Z
project: agent-context
topic: define-trial-doc-metadata
source: agent
status: active
---
# Session Note

## Summary

Added a shared frontmatter convention for authoring-source documents and applied it to the key source docs used by this repository.

## Actions

- Created `AUTHORING_METADATA.md` to define the shared authoring frontmatter fields and allowed values.
- Added authoring frontmatter to `CURATION_CONTRACT.md` and `RUNBOOKS/WORK_ITEM_ORCHESTRATION.md`.
- Updated `README.md` to document the new authoring-metadata convention and its scope.
- Left `instructions.local.md` unchanged because it is a direct runtime fragment whose delivery path should not receive frontmatter.

## Follow-up

- Apply the shared authoring frontmatter to future durable authoring-source Markdown files as they are added or revised.
