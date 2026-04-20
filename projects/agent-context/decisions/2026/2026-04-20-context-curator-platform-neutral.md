---
date: 2026-04-20
recorded_at: 2026-04-20T13:06:42.488Z
project: agent-context
topic: context-curator-platform-neutral
source: agent
status: active
---
# Decision

## Context

The project aims to reduce startup context cost for AI-assisted work on a large frontend codebase. One discussed mechanism is a narrow helper role, context-curator, that can read the sidecar knowledge layer and return a short routing summary. This helper may need to exist on different agent platforms such as Claude, Codex, and Cursor, so a vendor-specific design would create avoidable lock-in and duplicate documentation patterns.

## Decision

Define context-curator first as a platform-neutral role with a stable input/output contract, and treat Claude, Codex, Cursor, or other platform-specific implementations as adapters around that contract.

## Consequences

- The sidecar documentation can stay portable across agent platforms instead of encoding one vendor workflow as the default truth.
- Platform-specific automation can be added later without rewriting the conceptual model of curation.
- The core contract should stay focused on minimal inputs and a compressed routing output rather than tool-specific behaviors.
- The project may later maintain multiple platform adapters while preserving one shared curation model.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
