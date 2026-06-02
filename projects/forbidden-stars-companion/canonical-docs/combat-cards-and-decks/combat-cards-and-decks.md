---
date: 2026-06-02
recorded_at: 2026-06-02T11:42:59.232Z
project: forbidden-stars-companion
topic: combat-cards-and-decks
registry_scope: combat-cards-and-decks
source: agent
status: active
---
# Canonical Doc

## Summary

Приложение хранит и использует faction-specific combat decks по официальной схеме: стартовая колода из 10 карт, замена пар базовых карт на пары upgrade-карт и draw-5 per combat.

## Guidance

- У каждой фракции стартовая боевая колода состоит из десяти карт: пять уникальных базовых карт в двух копиях.
- При покупке combat upgrade игрок удаляет две копии любой карты из своей боевой колоды и добавляет две копии купленного апгрейда.
- Состояние боевой колоды игрока является частью прикладной сессии и должно отслеживаться приложением как practical companion-функция.
- Во время боя каждая сторона тянет пять карт из своей текущей боевой колоды и потенциально разыгрывает до трёх из них, по одной на execution round.
- Played combat cards не сбрасываются между execution rounds; они остаются в игре до конца боя и продолжают давать свои edge icons, если не были принудительно сброшены эффектом.
- В конце боя сыгранные карты возвращаются в боевую колоду; текущее приложение моделирует deck composition и play history, но не полный скрытый hand-management между устройствами.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/Forbidden_Stars_Database.pdf
- file:/home/moonbreeze/forbidden-stars-companion/src/stores/sessionStore.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/data/combatCards.ts
- file:/home/moonbreeze/forbidden-stars-companion/src/pages/CombatPage.tsx
