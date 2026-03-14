---
date: 2026-03-12
project: project-memory
topic: mcp-protocol-and-install-guard-cleanup
source: agent
status: active
---
# Session Note

## Summary

Tightened MCP protocol handling and install path validation, then closed the remaining cleanup tail with stable tests and documentation updates.

## Actions

- Restricted MCP initialize negotiation to the supported protocol version and returned structured JSON-RPC error codes for invalid requests, unknown methods, and invalid params.
- Validated install --memory-root so the memory repository must remain external to and non-overlapping with the tool repository.
- Removed the test-only PROJECT_MEMORY_TOOL_ROOT runtime path and moved install test overrides to explicit CLI context wiring.
- Extracted MCP stdio framing helpers into a dedicated module and added coverage for framed initialize exchange, unsupported protocol versions, JSON-RPC error codes, and invalid install roots.
- Validated the final state with npm test and npx tsc --noEmit.

## Follow-up

- Review the remaining working-tree diff as one final pre-commit pass.
- Create a commit once the current change set is approved.
- Optionally add a dedicated integration test for multi-request framed stdio sessions if the runtime lifecycle is revisited again.
