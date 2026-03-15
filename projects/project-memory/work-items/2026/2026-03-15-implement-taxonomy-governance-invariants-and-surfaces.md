---
date: 2026-03-15
project: project-memory
topic: implement-taxonomy-governance-invariants-and-surfaces
source: user
status: active
work_item_state: open
---
# Work Item

## Summary

Implement taxonomy governance invariants in shared core logic and expose the resulting behavior coherently through CLI and MCP so taxonomy enforcement does not remain only in agent guidance.

## Outcome

Project-memory enforces taxonomy registry invariants in shared core logic, supports the required bootstrap and validation behavior across CLI and MCP, and keeps human-choice taxonomy flows as procedure-backed operations rather than hidden heuristics.

## Provenance

- ad-hoc: Follow-up implementation work after recording taxonomy registry authority and enforcement decisions plus taxonomy meta-runbooks.

## Dependencies

- none

## Context

- decision:project-memory:2026-03-15:taxonomy-registry-authority-model
- decision:project-memory:2026-03-15:taxonomy-governance-enforcement-and-surfaces

## Verification

- Extract machine-enforceable taxonomy invariants from the new decisions and meta-runbooks, write tests for those invariants first, and then implement the supporting code so behavior is proven through executable contract rather than prose only.
- Cover bootstrap creation of the reserved taxonomy registry, registry-backed canonical-doc validation, and rejection of implicit registered topic or scope creation in automated tests.
- Add audit-oriented coverage for duplicate authority detection, unknown scope usage, and retired-topic misuse where the behavior is intended to be machine-detectable.
- Keep human-choice taxonomy operations such as ambiguous seeding or conflict-resolution judgment as explicit procedure-backed flows with fixtures or targeted examples rather than claiming full automation through tests alone.
- Expose implemented first-class taxonomy behaviors consistently through shared core logic, CLI commands, and MCP tools so MCP orchestration does not become semantically stronger than CLI.
- Evaluate whether the implementation establishes stable current-truth guidance that should be captured in a canonical doc; if so, create or update the canonical guidance rather than leaving the model distributed only across decisions, runbooks, and code.

## Evidence

- none
