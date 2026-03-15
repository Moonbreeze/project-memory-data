---
date: 2026-03-15
project: project-memory
topic: documentation-and-mcp-surface-synchronization
source: user
status: active
---
# Decision

## Context

A documentation review showed that the public repository docs can define a coherent operating model for humans while the MCP tool catalog still exposes a weaker or less specific model to external tool-using agents. External consumers may have access only to MCP tool names, descriptions, and schemas rather than repository-local instructions or managed project records. That makes it possible for documentation and MCP descriptions to drift even when each side is internally consistent. The project needs an explicit rule for how those surfaces should evolve together.

## Decision

Treat public documentation and MCP tool descriptions as two synchronized projections of the same operating model. Public docs may explain the model in more depth for humans, but MCP tool descriptions must still communicate the same document-role semantics, bounded-read startup pattern, managed-surface boundaries, and lifecycle expectations that materially affect tool choice by external agents. Significant changes to public repository documentation, especially README and docs/usage.md, must trigger an explicit review of whether MCP tool descriptions still reflect the same operational model.

## Consequences

- Documentation changes can no longer be treated as complete if they alter workflow guidance or document semantics without checking the MCP tool surface.
- MCP tool descriptions are not just API labels; they are part of the product's external behavioral contract for tool-using agents.
- The project should prefer one shared operating model expressed through different surfaces rather than letting human-facing docs and machine-facing tool descriptions evolve independently.
- Docs-first versus MCP-first sequencing is less important than preventing semantic drift between the two surfaces.
- Future reviews of public documentation should include a synchronization check against MCP descriptions whenever they touch document roles, startup flow, validation boundaries, or lifecycle guidance.
