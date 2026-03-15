---
date: 2026-03-14
project: project-memory
topic: system-overview
registry_scope: system
source: agent
status: active
---
# Canonical Doc

## Summary

Project Memory is a two-repository system: this tool repo provides CLI, MCP, validation, bounded reads, and managed write flows, while a separate external memory repo stores the project-scoped Markdown documents as the source of truth.

## Guidance

- Keep the tool repository and the external memory repository separate; the code lives here, while managed project documents live under PROJECT_MEMORY_ROOT.
- Treat the external memory repository as the source of truth for managed documents and this repository as the toolchain that validates, reads, and writes them.
- Use the same core behavior through either the local CLI or the MCP server; both are just interfaces over shared core logic.
- Keep repository-local documentation self-contained for users and contributors of the tool repo rather than relying on private project-memory data for onboarding.
- Preserve project-scoped commit discipline, bounded reads, and deterministic same-project defaults as part of the public tool contract.

## References

- decision: split
- decision: project-scoped-doc-commit-messages
- decision: filesystem-persistence-with-future-index
- runbook: project-scoped-doc-commit-protocol
