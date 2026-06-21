---
date: 2026-06-21
recorded_at: 2026-06-21T19:13:50.265Z
project: agent-context
topic: no-target-repo-harness-traces
source: agent
status: active
---
# Session Note

## Summary

Aligned the authoring repo and planning model with a rule that the harness should not leave durable harness-specific traces inside target repositories by default.

## Actions

- Removed the local scaffold direction from the authoring repo and rewrote the context-curator adapter recipe toward behavior-layer delivery.
- Read the active canonical docs and decision records to confirm that sidecar runtime knowledge had already been rejected but a stronger no-traces rule was not yet explicit.
- Reviewed active work-items against the proposed rule and identified the scaffold adapter item as the primary conflict to replace.

## Follow-up

- Record the durable decision and canonical update for the no-target-repo-traces rule.
- Continue future curator-delivery work through ai-inst/opencode behavior surfaces rather than target-repository scaffold paths.
