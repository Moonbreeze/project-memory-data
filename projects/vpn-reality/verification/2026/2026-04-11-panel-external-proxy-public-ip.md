---
date: 2026-04-11
recorded_at: 2026-04-11T17:43:01.885Z
project: vpn-reality
topic: panel-external-proxy-public-ip
source: agent
status: active
---
# Verification Result

## Scope

Проверка, что настройка External Proxy entry в inbound reality-main (3x-ui 2.8.11) заставляет панель подставлять публичный IP 147.45.196.137 в генерируемые vless:// share-ссылки вместо 127.0.0.1, сохраняя при этом все Reality-параметры inbound.

## Steps

- Открыта панель 3x-ui через SSH local port forward на 127.0.0.1:29486.
- Inbounds → reality-main → Edit: в секции External Proxy добавлен новый entry с Forced Expose IP = 147.45.196.137, Port = 443, Remark = public-ipv4.
- Форма сохранена без изменения других полей (Port, Protocol, Security, SNI/Dest/xTLS Vision/Short IDs/Public Key, Clients и их UUID).
- В списке клиентов inbound'а скопирован URL для клиента phone-android (UUID 4f26c1dc-2b1d-456f-95d7-57dea285c246).

## Result

Successful. Скопированная ссылка: `vless://4f26c1dc-2b1d-456f-95d7-57dea285c246@147.45.196.137:443?type=tcp&encryption=none&security=reality&pbk=9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8&fp=chrome&sni=www.microsoft.com&sid=444a941e4b8f&spx=%2F&flow=xtls-rprx-vision#reality-main-phone-android-public-ipv4`. Хост 147.45.196.137, порт 443, UUID совпадает с canonical-doc infrastructure/topology. Все 9 Reality-параметров на месте и не изменились: type=tcp, encryption=none, security=reality, pbk=9hE2DLpR6caqCS8FRZ9N4n2fsPTXcDuhVsuvXoGyAw8, fp=chrome, sni=www.microsoft.com, sid=444a941e4b8f, spx=%2F, flow=xtls-rprx-vision. Фрагмент после `#` получил суффикс `-public-ipv4` из remark entry — ожидаемый side-effect 3x-ui, косметический, на работу не влияет. Проверка клиентского curl ifconfig.me после импорта обновлённой ссылки не проводилась в рамках этого слайса.
