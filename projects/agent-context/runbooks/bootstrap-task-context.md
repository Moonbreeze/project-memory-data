---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.869Z
project: agent-context
topic: bootstrap-task-context
source: agent
status: active
---
# Runbook

## Purpose

Start a task with minimal context usage by reading only the bounded project-memory surfaces needed before opening code.

## Procedure

- Read `project-memory` cold-start context first to confirm the project purpose, stable guidance, and bounded startup surface.
- Read `read_planning_backlog` when choosing among ready work items, or `read_planning_topic_entry` when a concrete work-item is already selected.
- If the task still needs current truth or rationale, read one bounded `read_topic_entry` or `read_rationale_entry` package rather than scanning broadly.
- Inspect only the cited repository paths and their immediate adjacent dependencies first.
- Widen the search only if the cited paths do not explain the needed change or expose the responsible module boundary.

## Verification

- A new task can be started after reading bounded project-memory context instead of broad repository scans.
- The first code inspection step is limited to the files named by the selected bounded context package.
- The process identifies where to start, what nearby files to inspect, and what to verify after the change.
