---
date: 2026-04-05
recorded_at: 2026-04-05T12:57:49.631Z
project: project-memory
topic: separate-runtime-tests-from-safe-suite
source: agent
status: active
---
# Verification Result

## Scope

Test-suite separation for safe vs runtime-dependent Web lifecycle coverage

## Steps

- Ran `npm test` after separating runtime-only tests to confirm the default safe suite no longer includes local-port-binding cases and succeeds in the sandbox.
- Ran `npm run test:runtime` outside the sandbox to confirm the isolated core, MCP, and CLI Web lifecycle tests still pass when local port binding is allowed.
- Confirmed that `npm run test:all` is now representable as the explicit combination of the safe suite and the runtime-only suite.

## Result

Pass. The default safe suite completed successfully in the sandbox with 8 passing test files and no failures, while the isolated runtime suite passed outside the sandbox with the separated core, MCP, and CLI Web lifecycle tests all green.
