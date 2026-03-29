---
date: 2026-03-29
recorded_at: 2026-03-29T08:38:34.659Z
project: project-memory
topic: web-server-lifecycle-design-discussion
source: agent
status: active
---
# Session Note

## Summary

Evaluated the proposal for global Web links and Web-server lifecycle management, separated acceptable shared-core design goals from risky assumptions such as automatic public-IP truth and MCP-coupled runtime behavior, and opened a dedicated work-item for the resulting design slice.

## Actions

- Reviewed the existing local read-only Web shell, MCP stdio runtime, and related Web guidance to ground the evaluation in the current architecture.
- Evaluated the proposal to add global link generation and Web-server lifecycle support, rejecting automatic public-IP discovery as configuration truth and keeping bind configuration separate from public URL semantics.
- Defined a planning direction based on shared core lifecycle operations for start, stop, status, singleton behavior keyed by PROJECT_MEMORY_ROOT, and local/public link generation for CLI and MCP.
- Created a dedicated work-item to track the design of Web-server lifecycle management and public link generation as a separate executable slice.

## Follow-up

- Design the shared core API for Web-server start, stop, status, and link generation.
- Define the singleton runtime state model, including idempotent startup and stale-process recovery.
- Specify thin CLI and MCP adapters, including CLI-only prompting for missing public URL configuration.
