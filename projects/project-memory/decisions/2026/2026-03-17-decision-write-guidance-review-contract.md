---
date: 2026-03-17
recorded_at: 2026-03-17T00:00:00.000Z
project: project-memory
topic: decision-write-guidance-review-contract
source: agent
status: active
---
# Decision

## Context

The decision write flow needed an explicit contract that ties durable rationale to stable-guidance review without depending on work-item closure. The implementation slice established that non-draft decisions should not rely on implicit human inference about whether canonical guidance was reviewed, updated, or deferred, and that decision records should remain immutable by path so later writes cannot silently replace prior rationale.

## Decision

Require non-draft decision writes to record an explicit stable-guidance review outcome at create_decision time, exempt draft decisions from that requirement, allow bootstrap-only explicit exemption when no prior stable-guidance surface exists, and reject silent overwrite of an existing decision path.

## Consequences

- Non-draft decisions now carry explicit review semantics instead of leaving stable-guidance handling implicit.
- Draft decisions remain lightweight inbox records rather than requiring phantom stable-guidance bookkeeping.
- Bootstrap cases stay possible, but only through an explicit exemption outcome rather than silent bypass.
- Decision records become immutable by path, so later durable rationale must be expressed as a new record or lifecycle transition instead of overwrite.

## Stable Guidance Review

- Outcome: updated
- Summary: Updated stable guidance to reflect the new contract by adding explicit decision-write review semantics and immutable decision-path guidance to the active document-model canonical doc, alongside matching repository documentation updates.
