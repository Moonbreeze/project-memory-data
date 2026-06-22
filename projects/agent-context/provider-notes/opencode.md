---
date: 2026-06-22
recorded_at: 2026-06-22T13:39:58.906Z
project: agent-context
topic: opencode
source: agent
status: active
---
# Provider Note

## Overview

Opencode subagent spawn has a meaningful fixed cost because runtime bootstrap context, including system/agent instructions and tool definitions, is replicated into each fresh subagent context.

## Constraints

- Long system or agent prompts multiply across spawned subagents and can erase any expected token savings from delegation.
- Permission rules can restrict behavior but do not guarantee that the runtime will omit the corresponding tool definitions from subagent context.
- experimental.primary_tools is the preferred first lever for keeping heavy tools on the primary agent only.
- Opencode configuration changes require an application restart before the new behavior takes effect.

## Guidance

- Use an orchestrator-first policy: let the primary agent perform small, local edits directly.
- Keep subagents read-only by default and reserve write-capable subagents for isolated larger execution slices.
- Keep subagent prompts short and role-specific: role, boundaries, allowed actions, and required result format only.
- Prefer path-and-range handoff over inline file bodies when the subagent can reread the source of truth locally.
- Keep heavy tools such as edit, bash, task, question, and todowrite on the primary/orchestrator when possible.
- Treat delegation as worthwhile only when it clearly improves search breadth, parallelism, context isolation, or specialized review quality.
