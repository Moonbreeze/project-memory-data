---
date: 2026-06-25
recorded_at: 2026-06-25T18:23:38.894Z
project: vpn-reality
topic: topology
registry_scope: infrastructure
source: agent
status: active
---
# Canonical Doc

## Summary

Текущая топология VPN: публичный клиентский вход расположен на RU-relay в Yandex Cloud, DE VPS остаётся только backhaul/exit-узлом, а базовая REALITY-маскировка для relay-first схемы переведена с `www.microsoft.com` на `www.cloudflare.com` после восстановления сломавшегося handshake-контра.

## Guidance

- RU-relay: Yandex Cloud VPS с публичным IPv4 `178.154.193.39`. На relay поднят standalone `xray`, публичный inbound `relay-public` слушает `0.0.0.0:443`, протокол `VLESS`, transport `TCP`, security `Reality`, flow `xtls-rprx-vision`.
- Клиентский endpoint проекта остаётся `178.154.193.39:443`, но базовая REALITY-маскировка для relay-first схемы теперь `www.cloudflare.com`, а не `www.microsoft.com`. При генерации клиентских профилей и relay-public inbound использовать только cloudflare-based `sni/serverNames` и актуальные live `pbk`/`sid` из relay-public.
- DE-exit остаётся хостом `147.45.196.137` / `2a0f:cdc6:500:758::2` и выполняет только роль backhaul/exit. На нём поднят отдельный inbound `8443/tcp` с `VLESS + Reality + Vision`; backhaul mask host для него также синхронизирован на `www.cloudflare.com`, а relay outbound `de-backhaul.serverName` должен совпадать с этим значением.
- Firewall boundary на DE: `8443/tcp` разрешён только с IP relay `178.154.193.39`. Общий allow `8443/tcp Anywhere` удалён. Если IPv6 backhaul не используется, публичный `8443/tcp (v6)` держать закрытым.
- Старый прямой inbound `reality-main` на DE больше не является primary client path. Operational truth проекта строится вокруг relay-first схемы `client -> Yandex -> DE -> internet`.
- Проверка топологии должна использовать raw IP echo endpoints, а не `ifconfig.me` главной страницей: `curl -4 https://api4.ipify.org` должен возвращать `147.45.196.137`, а `curl https://api64.ipify.org` — IPv6 DE-exit. `ifconfig.me` не использовать как единственный oracle.
- Если relay-first трафик снова падает одновременно на нескольких устройствах без серверной ротации UUID, первым делом проверять REALITY handshake/logs и актуальность mask host на обоих уровнях (`relay-public` и `DE:8443`), а не начинать с клиентского routing.

## References

- runbook:vpn-reality:yandex-relay-setup
- provider-note:vpn-reality:yandex-cloud
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- verification-result:vpn-reality:2026-06-25:relay-public-cloudflare-mask-recovery
- decision:vpn-reality:2026-06-25:cloudflare-mask-over-microsoft-for-reality
- decision:vpn-reality:security:geoip-ru-blackhole
- https://habr.com/ru/articles/1021160/
