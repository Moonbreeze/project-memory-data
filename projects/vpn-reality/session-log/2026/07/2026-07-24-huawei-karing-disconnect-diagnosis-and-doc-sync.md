---
date: 2026-07-24
recorded_at: 2026-07-24T18:19:46.451Z
project: vpn-reality
topic: huawei-karing-disconnect-diagnosis-and-doc-sync
source: agent
status: active
---
# Session Note

## Summary

Reviewed project memory after a Huawei/Karing intermittent disconnect report and found active onboarding/runbook drift: canonical guidance had already moved relay-first REALITY masking to Cloudflare, while several user-facing runbooks still carried Microsoft-based legacy parameters. Synced the active docs to Cloudflare-based guidance and isolated Huawei as the remaining likely client-side suspect when other devices are stable.

## Actions

- Read current authoritative docs, historical recovery decision, and verification for the 2026-06-25 REALITY handshake incident.
- Confirmed canonical guidance says relay-first client profiles must use `sni=www.cloudflare.com` and live `relay-public` parameters.
- Updated active runbooks `add-client`, `add-client-relay`, `install-guide`, and `yandex-relay-setup` to remove Microsoft-based provisioning drift and require live Cloudflare-based relay parameters.
- Updated active canonical doc `security-model` so stable guidance no longer states Microsoft-based masking as current truth.
- Checked external Karing/Huawei references; Huawei background process killing and battery restrictions remain a plausible device-only cause if the same profile works elsewhere.

## Follow-up

- On the affected Huawei, verify the imported profile is a Cloudflare-based relay-first link rather than an old Microsoft-based one.
- If the profile is current and other devices stay stable, disable Huawei battery/app-launch restrictions for Karing, enable Android Always-on VPN for Karing, and retest foreground/background behavior.
- If disconnects continue after client-side fixes, capture the exact Karing error text or server-side log timing for one Huawei reconnect attempt to separate client kill from REALITY handshake failure.
