---
date: 2026-03-16
project: project-memory
topic: implement-taxonomy-governance-invariants-and-surfaces
source: agent
status: active
---
# Session Note

## Summary

Implemented shared taxonomy governance invariants, bootstrapped registry behavior, exposed CLI/MCP taxonomy surfaces, verified the behavior through tests, and tightened the general project-documentation confirmation rule in ai-inst.

## Actions

- Added shared taxonomy registry, bootstrap, write-validation, and audit behavior in core.
- Integrated taxonomy governance behavior into bootstrap, install, canonical-doc writes, CLI commands, and MCP tools.
- Added and updated automated tests for taxonomy bootstrap, validation, audit behavior, and new CLI/MCP surfaces.
- Refactored duplicated `isRecord` checks into shared primitives and aligned taxonomy imports with the documents barrel.
- Updated the general ai-inst documentation-workflow module so managed-document edits require a document-by-document concrete change plan before confirmation.

## Follow-up

- Implement `make-taxonomy-audit-alias-aware` to align alias handling between audit behavior and the taxonomy authority model.
- Execute `taxonomy-registry-alignment-follow-up` as the first real-world validation pass over the project-memory corpus.
- Use `strengthen-decision-and-canonical-doc-process` to define when accepted and implemented decisions should trigger canonical-guidance review.
