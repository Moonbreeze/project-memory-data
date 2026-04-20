---
date: 2026-04-20
recorded_at: 2026-04-20T13:06:36.038Z
project: agent-context
topic: request-curated-context
source: agent
status: active
---
# Runbook

## Purpose

Request a minimal routing summary from a context-curator for a concrete change without forcing the main agent to scan the repository broadly.

## Procedure

- Provide a short task statement that names the intended change and, if known, the affected product area.
- Include any explicit starting files or directories when they are already known from the request or previous work.
- Ask for a compressed response in task-routing form rather than a broad architectural explanation.
- Use the returned summary to inspect the named files first and widen the search only if the route does not explain the change.
- If the task reveals a new stable path for similar changes, capture that route in the sidecar routing documents after the work is done.

## Verification

- The returned summary contains Start here, Also inspect, Pitfalls, and Verify sections or their equivalent.
- The first code-reading step is limited to the files named in the curated response.
- The curation request can be expressed without relying on a platform-specific agent feature.
