---
date: 2026-07-24
recorded_at: 2026-07-24T20:23:19.665Z
project: vpn-reality
topic: huawei-karing-emui-battery-fix
source: user
status: active
---
# Verification Result

## Scope

Huawei Android device with Karing intermittently disconnecting while other devices on the same relay-first contour remain stable

## Steps

- Compared symptom against current project memory and excluded the previously fixed microsoft-based REALITY legacy path because the device was already using the current single active link.
- User adjusted Huawei/EMUI power-saving and app launch restrictions for Karing on the affected device.
- User re-tested the connection after changing those Huawei battery settings.

## Result

Confirmed client-side fix. The intermittent Karing disconnect on the Huawei device stopped after relaxing Huawei/EMUI energy management settings for Karing, which distinguishes this case from the earlier server-side REALITY handshake incident that affected multiple devices at once.
