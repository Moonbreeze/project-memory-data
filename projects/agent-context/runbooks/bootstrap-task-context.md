---
date: 2026-04-20
recorded_at: 2026-04-20T12:58:09.095Z
project: agent-context
topic: bootstrap-task-context
source: agent
status: active
---
# Runbook

## Purpose

Enter a new task with minimal context usage by reading only the smallest stable routing surface before opening code.

## Procedure

- Read the project start document first to confirm the project purpose, trust model, and the recommended reading order.
- Open the task-routing index or entrypoints document that matches the change type instead of scanning the repository broadly.
- Read at most one relevant area or recipe document before inspecting code.
- Open only the cited start files and their immediately adjacent dependencies first.
- Widen the search only if the cited files do not explain the needed change or expose the responsible module boundary.

## Verification

- A new task can be started after reading only the start document plus one routing document.
- The first code inspection step is limited to the files named by the routing layer rather than a broad repository scan.
- The process identifies where to start, what nearby files to inspect, and what to verify after the change.
