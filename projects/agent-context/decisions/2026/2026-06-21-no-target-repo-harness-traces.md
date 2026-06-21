---
date: 2026-06-21
recorded_at: 2026-06-21T19:14:03.050Z
project: agent-context
topic: no-target-repo-harness-traces
source: agent
status: active
---
# Decision

## Context

After rejecting the sidecar runtime model, the project still needed an explicit rule for whether the harness may deliver its own behavior through repo-local artifacts in a target repository. Recent discussion and a rejected scaffold direction showed that leaving adapter prompts, routing docs, scaffold files, or similar harness-owned artifacts in a target repository would recreate a parallel runtime surface and blur the separation between authoring materials, runtime behavior, and project-specific truth.

## Decision

By default, the harness must not require, create, or maintain harness-specific durable artifacts inside a target repository. Harness behavior is delivered through ai-inst/opencode or equivalent behavior-layer tooling, while project-specific truth remains in project-memory. Repo-local changes inside a target repository are allowed only when they are part of the user’s actual task or when the user explicitly requests a repository-local integration.

## Consequences

- Bootstrap, routing, adapter, scaffold, and similar harness-owned documents are not part of the default target-repository runtime path.
- Behavior delivery shifts toward ai-inst/opencode and other behavior-layer integration surfaces instead of file scaffolds copied into working repositories.
- Target-repository edits remain allowed for the user’s task itself, but they should not be introduced as hidden harness prerequisites.
- Active work-items, recipes, and future integration plans must avoid target-repository harness artifact paths by default.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Added the explicit no-target-repo-traces rule and updated the documentation-model canonical doc plus affected work-items in the same change slice.
