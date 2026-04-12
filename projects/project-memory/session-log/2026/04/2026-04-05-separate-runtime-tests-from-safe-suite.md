---
date: 2026-04-05
recorded_at: 2026-04-05T12:57:49.542Z
project: project-memory
topic: separate-runtime-tests-from-safe-suite
source: agent
status: active
---
# Session Note

## Summary

Separated local-port-dependent Web runtime tests from the default safe test suite so sandbox runs stop failing on environment restrictions.

## Actions

- Confirmed that the previously failing Web-related suites were green outside the sandbox and that the failures were caused by restricted local port binding rather than by code regressions.
- Split Web runtime lifecycle coverage into dedicated runtime-only test files for core, CLI, and MCP flows.
- Added shared test-support helpers for free-port allocation and CLI/MCP test harness parsing to avoid duplicating split-specific utilities.
- Updated package scripts so `npm test` runs the safe suite by default, while `test:runtime` and `test:all` provide explicit runtime-dependent and full execution paths.
- Verified that the safe suite passes in the sandbox and that the runtime-only suite passes when run outside the sandbox.

## Follow-up

- Archive or otherwise finalize the completed implement-web-tests work-item in a later maintenance slice if it no longer needs to stay visible in active planning.
