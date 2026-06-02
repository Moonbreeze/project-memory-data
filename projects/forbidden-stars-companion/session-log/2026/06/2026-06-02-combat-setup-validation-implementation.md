---
date: 2026-06-02
recorded_at: 2026-06-02T14:50:13.697Z
project: forbidden-stars-companion
topic: combat-setup-validation-implementation
source: agent
status: active
---
# Session Note

## Summary

Внедрена rule-aware валидация setup боя с доменным валидатором, UI-ограничениями и обработкой special case пустой защиты.

## Actions

- Добавлен чистый доменный валидатор `src/combat/validation.ts` для проверки factions, состава юнитов, лимитов копий и лимита в пять attacking units.
- `CombatSetup` на `src/pages/CombatPage.tsx` подключён к валидатору: старт боя блокируется при ошибках, UI показывает issue messages и отключает недопустимое добавление атакующих юнитов и лишних копий.
- Для special case, когда у защитника нет units и bastion, setup теперь явно сообщает о мгновенной победе атакующего и переводит бой сразу к итогам.
- Добавлены тесты `src/combat/validation.test.ts`, затем выполнены combat tests и production build без ошибок.

## Follow-up

- Отдельный work-item `combat-resolution-rules` всё ещё нужен, чтобы вернуть фазу preparation и полное rule-accurate прохождение setup→execution→resolution.
- Если в combat UI позже появится выбор `world`/`void`, setup-валидатор стоит расширить проверкой типа участвующих юнитов.
