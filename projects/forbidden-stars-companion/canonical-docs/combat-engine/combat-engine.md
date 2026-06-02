---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.115Z
project: forbidden-stars-companion
topic: combat-engine
registry_scope: combat-engine
source: agent
status: active
---
# Canonical Doc

## Summary

Боевая подсистема приложения моделирует contested-area combat по Rules Reference: dice, three execution rounds, temporary combat tokens, morale-based resolution и routed state.

## Guidance

- Модель боя должна следовать официальной структуре из Rules Reference: preparation, три execution rounds и resolution.
- Во время preparation каждая сторона получает dice по суммарному combat value unrouted units, затем тянет пять combat cards и при желании вводит reinforcement tokens.
- Во время execution каждая сторона разыгрывает до одной карты за раунд; played cards остаются faceup до конца боя, а combat tokens очищаются в конце каждого execution round.
- Во время assess damage offence и defence считаются по dice, combat tokens и faceup combat cards; damage не переносится между execution rounds.
- Во время resolution победитель определяется по morale, в которую входят dice morale, morale unrouted units, bastion morale и faceup cards; защитник выигрывает ничью.
- Если defending side в начале боя не имеет unrouted units или bastion, attacker выигрывает немедленно без preparation и execution.
- Bastion участвует в бою как источник combat, health и morale, но не является unit, не routится и не retreat’ит.
- Чистая доменная реализация боя должна жить в `src/combat`, а store/UI должны только использовать этот слой.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/forbidden_stars_faq_1.1.pdf
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/types.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/calculations.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/combat/actions.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/combatStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/CombatPage.tsx
