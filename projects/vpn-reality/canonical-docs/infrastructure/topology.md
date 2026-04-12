---
date: 2026-04-12
recorded_at: 2026-04-12T15:02:59.054Z
project: vpn-reality
topic: topology
registry_scope: infrastructure
source: agent
status: active
---
# Canonical Doc

## Summary

Текущая топология VPN: публичный клиентский вход теперь на RU-relay в Yandex Cloud, а DE VPS выступает только backhaul/exit-узлом. Клиенты подключаются к Yandex IP по VLESS Reality на 443, relay уводит трафик на DE inbound на 8443, а финальный внешний IP остаётся немецким по IPv4 и IPv6.

## Guidance

- RU-relay: Yandex Cloud VPS с публичным IPv4 `178.154.193.39`. На relay поднят standalone `xray`, публичный inbound `relay-public` слушает `0.0.0.0:443`, протокол `VLESS`, transport `TCP`, security `Reality`, flow `xtls-rprx-vision`.
- Клиентский endpoint проекта теперь `178.154.193.39:443`. Share-ссылки для устройств должны указывать именно Yandex IP, а не DE-exit. Актуальные Reality client params для relay: `sni=www.microsoft.com`, `fp=chrome`, `pbk=zF486Nys3ZwxCtLW83cmwsXWvugaeP3cYk4rcYP9sgw`, `sid=d155a5e6a588d95b`, `spx=%2F`, `flow=xtls-rprx-vision`.
- DE-exit остаётся хостом `147.45.196.137` / `2a0f:cdc6:500:758::2` и теперь выполняет только роль backhaul/exit. На нём добавлен отдельный inbound `relay-backhaul` на `8443/tcp` с `VLESS + Reality + Vision`; relay подключается только к нему.
- Firewall boundary на DE: `8443/tcp` разрешён только с IP relay `178.154.193.39`. Общий allow `8443/tcp Anywhere` удалён. Если IPv6 backhaul не используется, публичный `8443/tcp (v6)` держать закрытым.
- Старый прямой inbound `reality-main` на DE больше не является primary client path. При полной миграции клиентов его можно выключить; operational truth проекта теперь строится вокруг relay-first схемы `client -> Yandex -> DE -> internet`.
- Проверка топологии должна использовать raw IP echo endpoints, а не `ifconfig.me` главной страницей: `curl -4 https://api4.ipify.org` должен возвращать `147.45.196.137`, а `curl https://api64.ipify.org` — IPv6 DE-exit. `ifconfig.me` может путать IPv4/IPv6 observed address и не годится как единственный oracle.
- Порт `443/tcp` на Yandex relay был освобождён под Reality; если на той же VM крутится MTProto или другой сервис, его нужно переносить на отдельный порт или отдельный IP до включения relay.

## References

- runbook:vpn-reality:yandex-relay-setup
- provider-note:vpn-reality:yandex-cloud
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- decision:vpn-reality:security:geoip-ru-blackhole
- https://habr.com/ru/articles/1021160/
