---
date: 2026-03-15
project: project-memory
topic: resolve-taxonomy-conflicts-and-cleanup
source: user
status: active
---
# Runbook

## Purpose

Resolve duplicate scopes, stale aliases, overlapping authority boundaries, invalid registry entries, and ambiguous historical residue discovered during taxonomy audits.

## Procedure

- Collect current audit findings and group them by conflict type such as duplicate active authority, unknown scope usage, stale aliasing, overlapping boundaries, lifecycle mismatches, or unresolved migration residue.
- Prioritize conflicts that block active canonical-document validation or leave multiple active authority surfaces for the same semantic area.
- For each conflict, choose an explicit resolution path such as rename, split, merge, boundary change, retirement, alias cleanup, or migration clarification rather than applying ad hoc edits.
- Apply the selected taxonomy changes in the registry first, then update dependent canonical documents and references so authority surfaces match the repaired registry state.
- Re-run taxonomy audit after cleanup and keep unresolved ambiguities visible if they still require human judgment.
- Record enough rationale for each cleanup so future audits can distinguish intentional modeling changes from drift or accidental repair.

## Verification

- Confirm every conflict has an explicit chosen resolution or remains visibly unresolved for follow-up.
- Confirm deprecated labels were removed or demoted to aliases intentionally rather than left in ambiguous active use.
- Confirm repaired canonical documents now match the registry state.
- Confirm the post-cleanup registry passes taxonomy audit or clearly reports the remaining unresolved cases.
