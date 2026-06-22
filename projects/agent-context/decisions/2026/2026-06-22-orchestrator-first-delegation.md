---
date: 2026-06-22
recorded_at: 2026-06-22T13:40:23.910Z
project: agent-context
topic: orchestrator-first-delegation
source: agent
status: active
---
# Decision

## Context

The current stable guidance for agent-context defines bounded startup, task routing, and platform-neutral curation, but it does not yet make delegation economics explicit. In opencode, each spawned subagent carries a fixed bootstrap cost because system/bootstrap prompt content and tool definitions are repeated in the fresh context. Passing full file bodies into a subagent usually duplicates later reads and inflates the handoff. The harness therefore needs an explicit policy for when the orchestrator should work directly, when delegation is justified, and what the minimal subagent handoff should contain.

## Decision

Adopt an orchestrator-first delegation policy. The orchestrator should perform small, local, clearly bounded tasks directly instead of spawning a subagent by default. Subagents should be used only when delegation is expected to outperform local execution through wider search, parallelism, stronger context isolation, or a distinct read-only helper role. Subagents are read-only by default. When delegation is used, the handoff must stay minimal: task statement, success criteria, known starting paths, explicit constraints, and expected result format. File contents should not be passed by default when the subagent can reread the source locally; prefer path and line-range references, with short inline snippets allowed only as narrow exceptions such as external logs or non-workspace text.

## Consequences

- Small and local tasks should complete in the orchestrator without unnecessary subagent spawn overhead.
- Runtime integrations need an explicit tool partition between primary/orchestrator and subagent roles.
- Platform-specific guidance for opencode should capture system-prompt and tool-surface cost as provider-specific operating constraints.
- Task-routing guidance should allow local orchestrator execution as a valid routing outcome instead of assuming delegation.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Updated task-routing guidance and added an opencode provider note in the same change slice to reflect the new delegation policy.
