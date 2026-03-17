---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: project-memory
topic: implement-decision-write-guidance-review-contract
source: agent
status: active
---
# Session Note

## Summary

Implemented the decision-side stable-guidance review contract, decision-path immutability, and matching repository documentation updates.

## Actions

- Updated the core decision write path to require explicit stable-guidance review outcome for non-draft decisions and to reject silent overwrite of an existing decision path.
- Extended CLI and MCP create-decision parsing and schemas for the new review contract inputs.
- Updated the decision template and automated coverage for allowed and rejected decision-write scenarios.
- Revised `docs/usage.md` and `docs/architecture.md` to document the new decision review contract and immutability rule.

## Follow-up

- Apply the new decision-write contract in future managed decision updates and use the explicit bootstrap exemption only when no prior stable-guidance surface exists.
- Revisit the broader `strengthen-decision-and-canonical-doc-process` umbrella item if more process guardrails are still needed beyond the implemented write contract.
