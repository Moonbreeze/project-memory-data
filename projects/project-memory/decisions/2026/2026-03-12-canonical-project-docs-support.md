---
date: 2026-03-12
project: project-memory
topic: canonical-project-docs-support
source: user
status: active
---
# Decision

## Context

A real consumer project wants to stop exposing private project documentation in the tool repository and instead treat project-memory as the canonical home for project docs. The current project-memory model is optimized for decisions, runbooks, provider notes, session notes, and verification results, but it does not provide a first-class canonical document type or an update workflow for one living project document per topic. The current ai-inst project-memory rules module also explains how to use project-memory, but it does not tell agents that a full documentation move into project-memory must be declared explicitly in project-specific rules rather than assumed by default.

## Decision

Extend project-memory with first-class support for canonical project documentation rather than overloading decisions or runbooks for that role. Add a dedicated document type and update workflow for canonical project docs, keep repository-local docs optional and project-policy-driven, and update the ai-inst project-memory rules module with a short conditional note: if a project wants project-memory to be the source of truth for project documentation, that policy must be stated explicitly in project-specific rules.

## Consequences

- Project-memory will need a new canonical-document path, template, validation profile, and write tool instead of relying only on the current note and runbook primitives.
- Projects will be able to keep only minimal bootstrap or stub docs in the repository once their project-specific rules explicitly declare project-memory as the canonical documentation store.
- Agents should not infer that repo docs may be removed simply because the project-memory module is enabled; the policy must be explicit at the project level.
- The ai-inst project-memory module should remain generic and should add only a conditional clarification, not a universal rule that every project must move docs into memory.
