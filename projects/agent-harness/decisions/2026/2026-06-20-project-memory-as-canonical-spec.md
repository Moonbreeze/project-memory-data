---
date: 2026-06-20
recorded_at: 2026-06-20T15:09:17.052Z
project: agent-harness
topic: project-memory-as-canonical-spec
source: agent
status: active
---
# Decision

## Context

The harness needs a durable specification surface for architecture, interaction rules, and operating guidance. Keeping the canonical prose in repository docs would duplicate authority and create drift between runtime artifacts and the actual intended model.

## Decision

Use project-memory as the canonical specification and rationale surface for agent-harness, while keeping the repository focused on executable runtime artifacts, scenarios, and examples.

## Consequences

- Canonical architecture and workflow guidance lives in project-memory instead of repository docs.
- The repository remains smaller and closer to execution concerns.
- Repository examples and scenarios can change without becoming the durable authority surface.
- Future changes to stable guidance should update project-memory first, then adjust runtime artifacts as needed.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: This decision establishes the stable authority boundary for the project.
