---
date: 2026-03-12
project: project-memory
topic: implementation-plan
source: agent
status: active
---
# Runbook

## Purpose

Track the current implementation plan for project-memory after native MCP compatibility was fixed and the first post-registration cleanup pass was completed.

## Procedure

- Treat the split between the publishable tool repository and the private memory repository as the primary remaining implementation track.
- Keep PROJECT_MEMORY_ROOT as the only supported selector for the external memory repository and remove stale assumptions or artifacts that suggest co-located private data.
- Maintain the narrow standard MCP surface based on initialize, tools/list, and tools/call; do not reintroduce legacy direct-method compatibility paths.
- Keep install output client-specific: Codex and Claude snippets plus local wrapper env files, without reviving the legacy generic .mcp.json artifact.
- Remove build-only or debug-only repository artifacts when they are no longer part of the supported runtime path, starting with the unused dist build path if verification stays green.
- Continue validating every cleanup step with npm test and npx tsc --noEmit before moving to the next one.

## Verification

- Native Codex MCP access can list, search, read, and write project-memory documents without CLI fallback.
- Repository documentation describes only the current installation and runtime path.
- The tool repository no longer carries unnecessary debug or legacy MCP artifacts.
- The supported runtime path is clear and consistent across scripts, install output, and tests.
- Automated verification remains green after each cleanup pass.
