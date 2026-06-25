---
date: 2026-06-25
recorded_at: 2026-06-25T18:23:53.037Z
project: vpn-reality
topic: cloudflare-mask-over-microsoft-for-reality
source: agent
status: active
---
# Decision

## Context

Несколько клиентов одновременно потеряли доступ через relay-first профиль без изменений в локальных клиентах и серверных UUID. Диагностика на 2026-06-25 показала, что старый public inbound `relay-public` на relay перестал завершать REALITY handshake при маскировке под `www.microsoft.com`, а после временного перехода public-side тестового inbound на `www.cloudflare.com` handshake и VLESS auth снова заработали. Отдельно было подтверждено, что backhaul `relay -> DE:8443` имеет корректно совпадающие UUID/key/short-id параметры, но DE inbound `8443` с той же microsoft-маскировкой рвал соединение с EOF до восстановления. После перевода DE backhaul inbound и relay outbound `de-backhaul.serverName` на `www.cloudflare.com` relay-first контур восстановился.

## Decision

Базовой REALITY-маскировкой проекта для обоих уровней relay-first схемы становится `www.cloudflare.com` вместо `www.microsoft.com`. Это касается и публичного relay inbound `relay-public` на Yandex relay, и backhaul inbound `8443` на DE плюс соответствующего relay outbound `de-backhaul.serverName`. При последующих ротациях share-ссылок клиентам выдаются только профили с `sni=www.cloudflare.com` и актуальными `relay-public` REALITY параметрами.

## Consequences

- Плюс: восстановлен массово сломавшийся relay-first доступ без смены клиентского стека и без пересборки всей топологии.
- Плюс: диагностика показала, что проблема была не в UUID/key mismatch и не в Karing, а в выбранной microsoft-маскировке на обоих REALITY уровнях.
- Минус: все старые клиентские share-ссылки с `sni=www.microsoft.com` считаются устаревшими и требуют перевыдачи.
- Минус: runbook-ы и canonical docs, которые явно фиксировали `www.microsoft.com`, должны быть синхронно обновлены, иначе проект снова получит документный drift при следующей настройке устройства.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
- Note: Updated canonical guidance for topology and clients in the same documentation slice.
