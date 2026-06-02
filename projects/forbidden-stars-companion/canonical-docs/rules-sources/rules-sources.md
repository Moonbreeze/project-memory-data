---
date: 2026-06-02
recorded_at: 2026-06-02T11:41:09.817Z
project: forbidden-stars-companion
topic: rules-sources
registry_scope: rules-sources
source: agent
status: active
---
# Canonical Doc

## Summary

Канонический приоритет источников по игре: Rules Reference, затем FAQ/Errata, затем Database; код проекта подчинён этим источникам и может отставать от них.

## Guidance

- Основным источником правил является PDF `Forbidden Stars - Rules Reference.pdf`; его определения, последовательности фаз и ограничения считаются базовой истиной по механике игры.
- PDF `forbidden_stars_faq_1.1.pdf` используется как слой errata и официальных уточнений поверх Rules Reference; при расхождении FAQ имеет больший вес для конкретного вопроса.
- PDF `Forbidden_Stars_Database.pdf` используется как справочник по статическим данным фракций, юнитов, карт и апгрейдов.
- Код репозитория является источником истины только о текущей реализации companion-приложения, но не о первичных правилах самой настольной игры.
- Если реализованная логика приложения расходится с rulebook/FAQ, канонические документы должны описывать правило по PDF и отдельно отмечать ограничение текущей реализации.
- Шаблонный README репозитория не использовать как содержательный источник по продукту или правилам.

## References

- pdf:/home/moonbreeze/Forbidden Stars - Rules Reference.pdf
- pdf:/home/moonbreeze/forbidden_stars_faq_1.1.pdf
- pdf:/home/moonbreeze/Forbidden_Stars_Database.pdf
- file:/home/moonbreeze/forbidden-stars-companion/README.md
