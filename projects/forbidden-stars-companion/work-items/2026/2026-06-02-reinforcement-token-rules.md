---
date: 2026-06-02
recorded_at: 2026-06-02T14:08:16.855Z
project: forbidden-stars-companion
topic: reinforcement-token-rules
source: agent
status: active
work_item_state: open
---
# Work Item

## Summary

Привести reinforcement tokens к официальным правилам.

## Outcome

Reinforcement tokens ограничены числом plastic units в бою, не дают dice, но корректно считаются как tier-0 units нужного типа для requisites и других card interactions.

## Provenance

- ad-hoc: Выделено по итогам аудита репозитория, project-memory и официальных rule sources 2026-06-02

## Dependencies

- none

## Context

- canonical-doc:forbidden-stars-companion:combat-engine:combat-engine
- canonical-doc:forbidden-stars-companion:combat-effects:combat-effects
- canonical-doc:forbidden-stars-companion:rules-sources:rules-sources
- session-note:forbidden-stars-companion:2026-06-02:initial-project-memory-fill

## Verification

- Проверить limit reinforcement tokens относительно числа plastic units в combat.
- Проверить, что reinforcement не увеличивают dice count.
- Проверить, что reinforcement учитываются в unit requisites там, где это допускают правила.
- Проверить поведение reinforcement отдельно для world combat и void combat.

## Evidence

- none
