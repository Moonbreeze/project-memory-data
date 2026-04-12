---
date: 2026-04-12
recorded_at: 2026-04-12T15:13:46.189Z
project: vpn-reality
topic: android-karing-over-hiddify-for-split-routing
source: agent
status: active
---
# Decision

## Context

Work-item android-split-routing требует той же модели маршрутизации, что уже подтверждена на Windows: российские локально доступные сервисы идут direct, а внешний и ru-blocked трафик — через final VPN route. Текущая canonical guidance всё ещё рекомендует Hiddify-Next на Android, но он не даёт проекту нужного уровня custom routing / remote rule-set управления для этого сценария. В то же время Karing уже выбран и подтверждён на Windows как sing-box клиент с TUN и custom diversion groups, а его Android-ветка поддерживает те же базовые routing primitives. Для поддержки друзей и собственных устройств проекту нужен один фактически работающий стек split routing, а не отдельный Android backlog вокруг клиента с урезанным routing UX.

## Decision

Для Android-сценариев, где нужен split routing, проект использует Karing + sing-box + TUN вместо Hiddify-Next. Hiddify-Next допускается только как упрощённый клиент без custom split routing, если устройству не нужны direct-исключения для российских сервисов. Android routing модель выравнивается с Windows: импорт relay-first VLESS Reality профиля в Karing, direct для private/local traffic, custom diversion group ru-blocked с действием Current Selected, проверка через ya.ru и домен из ru-blocked.

## Consequences

- Плюс: Windows и Android сходятся на одном клиентском семействе и одном типе rule-set'ов runetfreedom.
- Плюс: проект перестаёт зависеть от Android backlog в Hiddify и получает реальный путь к split routing на мобильных устройствах.
- Плюс: install/runbook можно унифицировать вокруг Karing import from clipboard/file и TUN-based проверки.
- Минус: Android-пользователю придётся ставить не тот клиент, который ранее считался основным в canonical docs.
- Минус: work-item android-split-routing нельзя считать закрытым до живой валидации на реальном Android-устройстве: отсюда нужен отдельный verification-result после ручной проверки.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
