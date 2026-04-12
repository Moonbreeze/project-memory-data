---
date: 2026-04-12
recorded_at: 2026-04-12T10:51:00.853Z
project: vpn-reality
topic: windows-karing-tun-over-system-proxy
source: agent
status: active
---
# Decision

## Context

Decision 2026-04-11 windows-system-proxy-over-tun выбирал v2rayN System Proxy как временный workaround, потому что sing-box не умел читать runetfreedom geosite.dat, а совместимых .srs rule-set'ов тогда не было в рабочем контуре. В рамках work-item unify-windows-hiddify-next исследование и живая валидация закрыли этот блокер: runetfreedom публикует sing-box-совместимые remote .srs rule-set'ы, Karing на Windows успешно поднимает TUN, а split routing подтверждён на реальном трафике. Пользователь также явно отделил Telegram Desktop от этого контура: Telegram использует отдельный MTProto и не должен быть verification-target для VPN TUN.

## Decision

На Windows проект использует Karing + sing-box + TUN как основной клиентский стек вместо v2rayN + Xray + System Proxy. Split routing строится через custom diversion groups и remote .srs rule-set'ы runetfreedom. Telegram Desktop не входит в обязательный VPN-контур и при наличии отдельного MTProto может быть принудительно выведен в Direct process-based правилом. Decision windows-system-proxy-over-tun от 2026-04-11 суперсидирован этим решением.

## Consequences

- Плюс: весь системный трафик приложений без поддержки system proxy может идти через VPN благодаря TUN.
- Плюс: routing теперь опирается на sing-box native .srs rule-set'ы, без локальной подмены geosite.dat и без привязки к xray-core.
- Плюс: схема для пользователя и друзей унифицируется вокруг одного Windows-клиента и файловой/clipboard-доставки профиля.
- Плюс: Telegram больше не смешивается с VPN verification; его можно держать на отдельном MTProto-контуре.
- Минус: Karing на Windows для TUN требует запуска от администратора.
- Минус: правила и UX завязаны на Karing custom diversion; при смене клиента потребуется новая валидация и, возможно, новый decision.

## Stable Guidance Review

- Outcome: updated
- Summary: Reviewed current stable guidance and updated the stable guidance in the same change slice.
