---
date: 2026-06-25
recorded_at: 2026-06-25T18:23:38.954Z
project: vpn-reality
topic: clients
registry_scope: client-setup
source: agent
status: active
---
# Canonical Doc

## Summary

Клиентские устройства получают relay-first профиль через Yandex relay. Для split routing проект по-прежнему опирается на Karing + sing-box + TUN, но базовая клиентская REALITY-маскировка обновлена на `www.cloudflare.com`, а старые microsoft-based ссылки считаются битым legacy.

## Guidance

- Новый базовый профиль для устройств использует публичный endpoint Yandex relay `178.154.193.39:443`, а не прямой DE IP. Клиентские share-ссылки должны использовать `sni=www.cloudflare.com`; старые microsoft-based ссылки (`sni=www.microsoft.com`) больше не считать рабочими.
- При перевыдаче профиля клиентам брать актуальные live REALITY параметры именно из `relay-public` на relay: текущие `pbk` и `sid` не восстанавливать по старым сообщениям или устаревшим runbook-шаблонам после ротаций/восстановлений.
- Android: если устройству нужен split routing, проект использует Karing + sing-box + TUN, а не Hiddify-Next. Но при массовом отказе нескольких устройств одновременно сначала исключать серверный REALITY/relay-side сбой, а не списывать симптом на Karing.
- Android: Hiddify-Next допустим только как упрощённый клиент без custom split routing, если устройство не требует direct-исключений для российских сервисов.
- Windows: Karing + sing-box + TUN остаётся основным стеком. Для полного захвата CLI/desktop трафика Karing должен быть запущен `Run as administrator`, а `TUN Mode` должен быть реально поднят, не только включён в UI.
- Для split routing используется одна и та же логика Karing: private/local traffic остаётся direct, а custom diversion group `ru-blocked` с действием `Current Selected` использует remote rule-set'ы runetfreedom. На Windows возможны process-based direct exceptions; на Android доступны package-id based exceptions, если позже понадобится выводить отдельные приложения из VPN.
- Проверять клиентский выход нужно командами `curl -4 https://api4.ipify.org` и `curl https://api64.ipify.org`, где это возможно; ожидаемый результат — IPv4 `147.45.196.137` и IPv6 DE-exit. На Android, где CLI-проверка неудобна, минимумом считаются `ya.ru` с российским IP и домен из `ru-blocked`, который открывается через туннель.
- Если после обновления клиентского профиля трафик не идёт и в `Karing`/`v2rayNG` виден `EOF`, сначала проверять relay-side `REALITY` handshake и backhaul, а уже потом DNS/routing и client-side diversion settings.
- Старые share-ссылки на `147.45.196.137:443` считаются устаревшими для новых устройств, а старые relay-first ссылки на `www.microsoft.com` считаются broken legacy после инцидента 2026-06-25.

## References

- runbook:vpn-reality:add-device
- runbook:vpn-reality:yandex-relay-setup
- verification-result:vpn-reality:2026-04-12:stage3-yandex-cloud-relay
- verification-result:vpn-reality:2026-04-12:windows-karing-tun-routing
- verification-result:vpn-reality:2026-06-25:relay-public-cloudflare-mask-recovery
- decision:vpn-reality:2026-04-12:windows-karing-tun-over-system-proxy
- decision:vpn-reality:2026-04-12:android-karing-over-hiddify-for-split-routing
- decision:vpn-reality:2026-04-11:geoip-ru-blackhole
- decision:vpn-reality:2026-06-25:cloudflare-mask-over-microsoft-for-reality
- https://github.com/KaringX/karing
- https://github.com/hiddify/hiddify-app
