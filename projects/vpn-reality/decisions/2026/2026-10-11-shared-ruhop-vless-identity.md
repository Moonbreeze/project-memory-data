---
date: 2026-10-11
recorded_at: 2026-10-11T21:24:08.735Z
project: vpn-reality
topic: shared-ruhop-vless-identity
source: agent
status: active
---
# Decision

## Context

Новый VDSina relay обслуживает небольшую доверенную группу, для которой пользователь не считает необходимыми индивидуальный отзыв профилей и per-device attribution. Первоначальный тестовый client UUID уже успешно используется, поэтому его ротация создала бы ненужную миграцию рабочих клиентов.

## Decision

Сохранить один существующий VLESS client UUID для всех доверенных пользователей нового relay и использовать постоянную серверную метку `ruhop-shared`. UUID не записывается в project-memory. Telegram продолжает использовать один существующий общий MTProto secret, поскольку mtg v2 в этой схеме также имеет single-secret модель.

## Consequences

- Одновременное использование одного VLESS UUID несколькими клиентами поддерживается и не требует отдельных server entries.
- Индивидуальная атрибуция и выборочный отзыв одного клиента невозможны.
- При утечке общего VLESS профиля необходимо ротировать UUID и перевыпустить профиль всем пользователям.
- Переименование email/label не меняет UUID и не ломает ранее импортированные ссылки; fragment в ссылке является только пользовательским именем.
- MTProto secret остаётся только на DE и не копируется в relay config или project-memory.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Canonical topology обновляется в этой же сессии: per-device UUID заменяется на shared `ruhop-shared` с явными последствиями.
