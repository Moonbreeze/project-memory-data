---
date: 2026-06-21
recorded_at: 2026-06-21T12:01:42.870Z
project: agent-context
topic: request-curated-context
source: agent
status: active
---
# Runbook

## Purpose

Request a minimal routing summary from a context-curator using bounded project-memory context for a concrete change.

## Procedure

- Provide a short task statement that names the intended change and the target project slug or equivalent context handle.
- Include any explicit starting files or directories when they are already known from the request or previous work.
- Ask for a compressed response in task-routing form rather than a broad architectural explanation.
- Have the curator read bounded project-memory surfaces first and inspect named code paths only after that route is established.
- If the task reveals new project-specific stable guidance, update project-memory; if it reveals a reusable generic pattern, update the authoring materials in agent-context.

## Verification

- The returned summary contains Start here, Also inspect, Pitfalls, and Verify sections or their equivalent.
- The first code-reading step is limited to the files named in the curated response.
- The curation request can be expressed without relying on a platform-specific agent feature.
