---
date: 2026-03-15
project: project-memory
topic: repository-documentation-information-architecture
source: user
status: active
---
# Decision

## Context

A documentation rewrite session exposed recurring failure modes in the tool-repository docs: the same core concepts were repeated across README, usage, and architecture; audience boundaries were unclear; roadmap ideas leaked into onboarding copy; workflow guides drifted toward command catalogs instead of document-model explanations; and diagrams were most useful only when they reduced cognitive load rather than restating prose. The team wants stable guidance so future documentation changes do not reintroduce those problems.

## Decision

Structure the tool-repository documentation around three explicit audiences and one shared concept layer. README is the entrypoint for new users and owns only core concepts, onboarding, and current product surfaces. docs/usage.md is the practical guide for working with the managed document model and should explain workflows in terms of document responsibilities and system operations, using examples or diagrams only when they clarify the model. docs/architecture.md is the contributor-facing system model and should focus on boundaries, retrieval behavior, core layering, and implementation constraints. Core product concepts such as repo split, MCP-first workflow, and the CLI's secondary role must be stated once in README and referenced elsewhere only when needed for local clarity.

## Consequences

- Future documentation reviews can reject repeated restatement of the same core concepts across multiple files as a structural defect rather than a wording preference.
- README should avoid roadmap or speculative future UX statements and describe only the current product and onboarding path.
- Usage documentation should prefer model-level lifecycle explanations and concrete migration or workflow examples over long command catalogs.
- Architecture documentation should target contributors and explain system shape, retrieval constraints, and surface layering rather than re-running end-user onboarding.
- Examples and diagrams become optional explanatory tools rather than mandatory ornamentation; they should stay only when they materially reduce ambiguity or cognitive load.
