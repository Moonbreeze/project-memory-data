---
date: 2026-04-12
recorded_at: 2026-04-12T15:06:11.041Z
project: vpn-reality
topic: stage3-yandex-cloud-relay
source: agent
status: active
---
# Session Note

## Summary

Завершена миграция на relay-first схему через Yandex Cloud: публичный клиентский вход перенесён на Yandex VPS, DE оставлен только как backhaul/exit. В процессе были разведены конфликты по порту 443 с MTProto, выдан capability Xray для bind на low port, настроен DE inbound `8443` только для IP relay и подтверждён клиентский выход через DE по IPv4 и IPv6.

## Actions

- Подтверждён существующий work-item `stage3-yandex-cloud-relay` из backlog и выбран как текущий execution slice.
- На Yandex VPS подготовлен Xray relay с публичным inbound на `443/tcp` и backhaul outbound на DE `147.45.196.137:8443`.
- На DE добавлен отдельный backhaul inbound `relay-backhaul` на `8443/tcp`, а firewall rule с общим `8443/tcp Anywhere` удалена в пользу allow только с `178.154.193.39`.
- На Yandex устранён конфликт `MTProto vs Reality` на `IP:443` переносом MTProto с 443 на другой порт.
- Исправлен запуск Xray на `443/tcp` через `setcap cap_net_bind_service=+ep` после ошибки `bind: permission denied`.
- На клиенте Karing/TUN подтверждён выход через DE с помощью `api4.ipify.org` и `api64.ipify.org`.
- В project-memory обновлены canonical docs topology/security/clients, добавлены runbook `yandex-relay-setup` и `add-client-relay`, а также provider note `yandex-cloud`.

## Follow-up

- Выключить старый прямой inbound на DE, если он ещё оставлен включённым как временный fallback.
- При необходимости обновить/суперсидировать старый runbook `add-client`, который всё ещё описывает прямой DE endpoint.
- Оценить, нужен ли отдельный formal decision, фиксирующий relay-first как primary production path вместо прямого DE entry.
