---
date: 2026-03-15
project: project-memory
topic: cleanup-runbooks-misused-for-session-context
source: agent
status: active
---
# Session Note

## Summary

Completed a taxonomy cleanup pass over project-memory runbooks after archive support was available for generic managed documents.

## Actions

- Audited every active project-memory runbook and classified them as model baselines, policy baselines, or transient planning or discovery artifacts rather than repeatable operational procedures.
- Archived all active project-memory runbooks through archive_document because none remained aligned with the runbook role after canonical docs, decisions, and work-item flows became first-class.
- Updated the document-model canonical guidance to state explicitly that runbooks are reserved for repeatable procedures and that baseline model or policy guidance belongs in canonical docs or decisions.

## Follow-up

- none
