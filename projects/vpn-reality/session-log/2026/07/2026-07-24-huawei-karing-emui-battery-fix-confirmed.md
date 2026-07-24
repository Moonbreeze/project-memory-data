---
date: 2026-07-24
recorded_at: 2026-07-24T20:23:19.744Z
project: vpn-reality
topic: huawei-karing-emui-battery-fix-confirmed
source: user
status: active
---
# Session Note

## Summary

User confirmed that the Huawei-only Karing disconnect issue was resolved by changing energy-saving settings on the device. This narrows the incident to Huawei/EMUI client behavior rather than relay-first server state, because other devices stayed healthy and the affected phone was already using the current active link.

## Actions

- Confirmed with the user that the Huawei device was connecting with the current single active profile rather than an older Microsoft-based link.
- Recorded the successful resolution as a Huawei/EMUI client-side fix rather than a server-side REALITY regression.
- Prepared stable guidance updates so future device onboarding and troubleshooting mention Huawei battery and app-launch restrictions for Karing.

## Follow-up

- When another Huawei/EMUI device shows periodic Karing reconnects or a flashing connect button, first check battery optimization, manual app launch permissions, and Always-on VPN before debugging relay-side REALITY.
- If a future Huawei still disconnects after these settings, capture the exact Karing error text and whether the failure happens only in background or also in foreground.
