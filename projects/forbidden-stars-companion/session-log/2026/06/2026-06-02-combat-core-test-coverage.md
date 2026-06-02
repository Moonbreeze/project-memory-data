---
date: 2026-06-02
recorded_at: 2026-06-02T14:42:25.520Z
project: forbidden-stars-companion
topic: combat-core-test-coverage
source: agent
status: active
---
# Session Note

## Summary

В проект добавлен базовый unit-test harness для combat core и покрыты тестами calculations, actions, requisiteCheck и детерминированные ветви effect executor.

## Actions

- Перевёл work item `combat-core-test-coverage` в in-progress и изучил `src/combat` вместе с текущей build/lint конфигурацией.
- Перевёл внутренние imports в `src/combat` и `src/data` на явные `.ts` specifiers, чтобы native `node --experimental-strip-types --test` мог загружать модули без внешнего test framework.
- Добавил `test` script в `package.json`, подключил `node` types в `tsconfig.app.json` и создал общий `src/combat/testHarness.ts` для сборки reproducible combat fixtures.
- Добавил unit tests для `src/combat/calculations.ts`, `src/combat/actions.ts`, `src/combat/analysis/requisiteCheck.ts` и `src/combat/effects/executor.ts`, покрыв dice/totals, rout/rally, requisites, conditional/scaling effects, pending inputs и deterministic rerolls.
- Исправил существующий lint issue в `src/stores/combatStore.ts`, где параметр `resolveBranchChoice` объявлялся, но не использовался.

## Follow-up

- Если coverage понадобится расширять дальше, следующими кандидатами являются `src/combat/analysis/analyzer.ts` и более сложные/manual branches в effect executor.
- Если проект захочет richer reporting, можно позже добавить coverage metrics или перейти на Vitest, но для текущего core native node test runner уже достаточен.
