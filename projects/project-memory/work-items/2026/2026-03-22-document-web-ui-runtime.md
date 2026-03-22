---
date: 2026-03-22
recorded_at: 2026-03-22T00:00:00.000Z
project: project-memory
topic: document-web-ui-runtime
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Document how to run and reason about the read-only Web UI in the tool repository.

## Outcome

Repository-local documentation explains how to start the Web UI, which environment variables it requires, what the baseline scope includes, which Web features are explicitly deferred, and how the Web layer relates to the external memory repository as the source of truth.

## Provenance

- decision:project-memory:2026-03-14:read-only-web-interface

## Dependencies

- work-item:project-memory:2026-03-22:implement-web-tests

## Context

- canonical-doc:project-memory:document-model:document-model
- canonical-doc:project-memory:reads:bounded-read-model

## Verification

- Update repository-local documentation with the Web UI startup path and required environment variables.
- Explain that the external memory repository remains the source of truth and that the Web layer is read-only.
- Document local runtime assumptions and any host or port configuration.
- Record deferred follow-up features including search, composed reading view, and graph view.
- Keep the repository-local docs aligned with the managed decision and canonical-doc guidance already recorded in project-memory.

## Evidence

- none
