---
date: 2026-06-20
recorded_at: 2026-06-20T15:10:29.628Z
project: agent-harness
topic: guided-ops-protocol
source: agent
status: active
---
# Runbook

## Purpose

Provide a repeatable safe protocol for guiding a human through infrastructure work on a remote resource.

## Procedure

- Start in observation mode and gather the current state before proposing changes.
- Interpret the observed state and explain the immediate risk or goal in plain language.
- Propose exactly one safe next action at a time and wait for the result before continuing.
- After each step, verify the result before proposing the next action.
- If a step increases risk or introduces ambiguity, pause and ask for confirmation or more evidence before proceeding.
- Keep change steps, rollback ideas, and verification steps explicit throughout the session.

## Verification

- A guided session does not skip directly from initial request to a long destructive command list.
- Each step has an explicit verification checkpoint before the next change.
- The protocol distinguishes observation, change, and rollback concerns clearly.
