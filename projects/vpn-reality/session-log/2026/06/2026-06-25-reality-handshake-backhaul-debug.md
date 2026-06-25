---
date: 2026-06-25
recorded_at: 2026-06-25T18:23:38.712Z
project: vpn-reality
topic: reality-handshake-backhaul-debug
source: agent
status: active
---
# Session Note

## Summary

Диагностирован массовый отказ relay-first контура: старый REALITY handshake на `www.microsoft.com` перестал проходить для `relay-public`, затем отдельно локализован EOF на backhaul `relay -> DE:8443`; восстановление достигнуто после перевода и public inbound, и DE backhaul mask host на `www.cloudflare.com` и синхронизации relay `de-backhaul.serverName`.

## Actions

- Проверен relay: `xray` валиден, `443/tcp` слушает, TCP до relay и до DE:8443 проходит.
- С помощью debug-логов и tcpdump локализован отказ старого `relay-public` на этапе REALITY handshake до VLESS auth.
- Поднят временный inbound `relay-test` на relay с новой REALITY-парой и mask host `www.cloudflare.com`; подтверждено, что public-side handshake и VLESS inbound работают.
- Через tcpdump на DE подтверждено, что relay доставляет payload на `8443`, а проблема находится в backhaul inbound application layer.
- Сопоставлены relay `de-backhaul` и DE inbound `8443`; UUID, flow, security, serverName, shortId и public/private key pair совпали.
- Через 3x-ui на DE inbound `8443` переведен с `www.microsoft.com` на `www.cloudflare.com`, затем relay `de-backhaul.serverName` синхронизирован с `www.cloudflare.com`.
- После синхронизации mask host подтверждено восстановление подключения и трафика.

## Follow-up

- Убрать временный inbound `relay-test` и связанные routing rules на relay после подтверждения, что основной `relay-public` уже переведен на `www.cloudflare.com`.
- Перевыдать клиентские share-ссылки с новым `sni=www.cloudflare.com` и актуальными `relay-public` REALITY параметрами.
- Обновить runbook-инструкции `add-client`, `add-client-relay`, `install-guide` и `yandex-relay-setup`, если они еще содержат `www.microsoft.com` и старые relay-public параметры.
