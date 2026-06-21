---
date: 2026-06-21
recorded_at: 2026-06-21T12:00:55.420Z
project: agent-context
topic: authoring-repo-project-memory-split
source: agent
status: active
---
# Decision

## Context

Current agent-context records still describe the repository as a sidecar runtime knowledge layer for external projects, with local START/ENTRYPOINTS/RECIPES-style documents acting as the main bootstrap surface. The target architecture has since become clearer: agent-context should be the authoring repository for harness behavior materials, opencode and ai-inst should deliver runtime behavior, and project-specific truth for a target repository should live in project-memory rather than in sidecar Markdown files near the code repository.

## Decision

Treat agent-context as an authoring repository for bounded-agent workflow design and Markdown source materials that can be extracted into ai-inst modules and skills. Treat opencode configuration plus ai-inst modules and skills as the runtime behavior layer of the harness. Treat project-memory as the authoritative project-specific knowledge layer used at runtime for bounded bootstrap, planning, rationale, verification, and evidence on a target repository.

## Consequences

- Target repositories do not need to adopt repo-local sidecar bootstrap documents as the primary runtime source of truth.
- Harness startup for a target repository should read bounded context from project-memory rather than assuming START.md or ENTRYPOINTS.md exist in that repository.
- Markdown files in agent-context should be authored as behavior-design and extraction inputs, not as a parallel canonical knowledge base for unrelated projects.
- Reusable routing patterns may still be designed in agent-context, but project-specific routing and current truth should be stored in project-memory.
- Existing sidecar-oriented canonical docs and work-items need to be rewritten to reflect the split between authoring repo, behavior layer, and project-memory data layer.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Reviewed current stable guidance and updated the canonical docs and work-items in the same change slice.
