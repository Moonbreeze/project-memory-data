---
date: 2026-03-14
project: project-memory
topic: taxonomy-registry-baseline
source: agent
status: archived
---
# Runbook

## Purpose

Define the first managed taxonomy registry artifact for project-memory so topic categorization and authority boundaries are explicit before canonical-doc support is implemented.

## Procedure

- Create one registry document per project as the authoritative taxonomy baseline.
- Treat each registry entry as a topic record, not as a canonical knowledge article.
- Require each entry to contain the topic slug, authoritative scope slug, short scope description, authority location, migration status, aliases, related topics, and explicit cross-project mappings.
- Authority location must distinguish whether the current source of truth lives in project-memory, in repository docs, or is intentionally split during migration.
- Scope ownership must be unique within the project. If two entries appear to claim the same authoritative scope, treat that as a modeling error and resolve it before adding canonical docs.
- Aliases are lookup aids only. They must not create additional authority boundaries.
- Related topics connect nearby concepts inside the same project, but they do not imply authority inheritance.
- Cross-project mappings must name the target project and target topic or scope explicitly. They are references only and do not widen default reads.
- Migration status should be tracked explicitly so partial migration is visible. The initial baseline should support at least repo-doc-authoritative, project-memory-authoritative, split-migration, and planned.
- When canonical-doc support arrives, each authoritative canonical doc must point back to one declared registry scope instead of inventing its own authority boundary.

## Verification

- The registry defines topic and scope as first-class managed data rather than informal tags.
- Authority ownership is explicit enough to detect overlap before canonical-doc writes exist.
- Partial migration can be represented without forcing an all-at-once move into project-memory.
- Cross-project relationships remain explicit and bounded.
- Session 2 can reuse the registry schema directly when canonical-doc support is implemented.
