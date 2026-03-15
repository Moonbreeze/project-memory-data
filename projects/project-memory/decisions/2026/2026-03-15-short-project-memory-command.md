---
date: 2026-03-15
project: project-memory
topic: short-project-memory-command
source: user
status: draft
---
# Decision

## Context

The current local CLI entrypoints are wrapper scripts such as ./scripts/run-cli.sh <command> ..., which are accurate but too low-level and visually heavy for first-contact documentation and normal human use. Documentation now treats MCP as the primary interactive workflow, but there is still a need for a shorter human-facing command surface for local CLI operations. The desired change is to improve discoverability and ergonomics without turning CLI into the primary workflow or changing the repository split and document model.

## Decision

Add a short top-level command named project-memory as the intended human-facing CLI entrypoint for local operations. This command should provide the same underlying managed-document and bounded-read capabilities as the current wrapper-based CLI surface while preserving MCP as the primary interactive workflow. The current wrapper scripts may remain as implementation details or fallback entrypoints, but documentation and onboarding should be able to present project-memory ... as the concise local command form.

## Consequences

- First-contact documentation can use shorter and clearer local command examples without implying that wrapper scripts are the intended long-term UX.
- MCP remains the primary interactive workflow for agent-assisted work; the short command improves local ergonomics but does not change the interaction model.
- Implementation details remain open: package bin, generated wrapper, or another lightweight launcher should be evaluated separately.
- Installer behavior must be evaluated carefully so the new command does not require unnecessarily invasive global environment changes.
- The short command must preserve the existing validation, bounded-read behavior, and repository-root selection model rather than introducing a parallel CLI semantics.
