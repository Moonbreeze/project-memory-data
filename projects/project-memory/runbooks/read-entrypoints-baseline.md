---
date: 2026-03-14
project: project-memory
topic: read-entrypoints-baseline
source: agent
status: active
---
# Runbook

## Purpose

Define the first baseline read workflows for agents so project-memory can reduce context cost and retrieval time instead of acting only as a write-side archive.

## Procedure

- Cold start entrypoint: begin with a narrow project summary view, then read only the active decisions, canonical docs, and open work items needed for the current request. Avoid broad scans of session history unless the task is explicitly historical.
- Topic lookup entrypoint: resolve the requested topic through the future topic and scope registry, open the authoritative canonical document for that scope, and then expand only to linked decisions or verification evidence when the current truth alone is insufficient.
- Why lookup entrypoint: start from the current canonical doc or topic scope, follow links to the governing active decision, and walk supersession history only until the current rationale is clear.
- Work planning entrypoint: list the current executable backlog from work items, then read only the linked decisions, canonical docs, or recent session notes needed to choose the next slice of work.
- Change execution entrypoint: before editing, read the governing canonical doc, the linked active decision, and any open work item for that scope; only then expand to recent execution notes or tests relevant to the concrete change.
- Verification or audit entrypoint: start from the work item, decision, or topic under review, then load the smallest set of verification results and session notes that prove what changed and how it was checked.
- Cross-project impact entrypoint: stay within the current project by default, and follow explicit cross-project mappings only when the current topic registry or linked documents indicate a real dependency or instructional impact.
- General read policy: prefer read narrow, expand on demand. Entry points should resolve to a minimal authoritative set first and only then widen into history, evidence, or adjacent projects.

## Verification

- The read model covers startup, current truth lookup, rationale lookup, planning, execution, verification, and cross-project impact analysis.
- Each entrypoint starts from a bounded authoritative source instead of from a full project scan.
- The baseline read policy supports future specialized list, search, and lookup helpers without requiring them to exist yet.
- Cross-project reading remains explicit and exceptional rather than becoming the default context expansion path.
