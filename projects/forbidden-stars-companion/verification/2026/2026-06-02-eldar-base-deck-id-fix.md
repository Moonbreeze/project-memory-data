---
date: 2026-06-02
recorded_at: 2026-06-02T14:22:51.589Z
project: forbidden-stars-companion
topic: eldar-base-deck-id-fix
source: agent
status: active
---
# Verification Result

## Scope

Eldar starter combat deck ID and upgrade replacement flow

## Steps

- Запущен npm run build в корне проекта.
- Собран временный verify entry через локальный esbuild с импортом sessionStore и combatCardsById.
- В runtime-сценарии вызван startSession для единственного игрока Eldar и проверена валидность всех стартовых card IDs через combatCardsById.
- В том же сценарии вызван purchaseCombatUpgrade(0, 'eld-fire-dragon', 'eld-command-autarch') и проверена корректная замена двух копий базовой карты на две копии upgrade-карты при сохранении длины колоды 10.

## Result

Проверка пройдена: npm run build завершился успешно; локальный runtime-check через временный esbuild bundle подтвердил, что стартовая Eldar deck содержит 10 валидных card IDs, каждая карта находится через combatCardsById, и purchaseCombatUpgrade корректно заменяет две копии eld-command-autarch на две копии eld-fire-dragon без битых ссылок.
