---
date: 2026-10-11
recorded_at: 2026-10-11T20:39:56.688Z
project: vpn-reality
topic: topology
registry_scope: infrastructure
source: agent
status: active
---
# Canonical Doc

## Summary

Primary operational topology uses the VDSina Moscow RU relay 138.16.175.166 for VLESS Reality and Telegram MTProto, with the existing DE host 147.45.196.137 as backhaul/exit. Temporary direct-DE and former Yandex relay access remain pending explicit cleanup.

## Guidance

- Primary VPN path is client -> VDSina relay 138.16.175.166:443 -> Xray VLESS Reality Vision -> DE 147.45.196.137:8443 -> internet. Trusted users share the existing VLESS UUID under server label `ruhop-shared`; DE backhaul credentials must never be used as client credentials.
- The shared VLESS identity supports concurrent clients but provides no per-client attribution or selective revocation. If the profile leaks, rotate the UUID and redistribute it to every user; the UUID itself must not be stored in project-memory.
- Primary Telegram path is client -> VDSina relay 138.16.175.166:9443 -> managed HAProxy with PROXY protocol v2 -> WireGuard -> DE mtg 10.66.0.2:3128 -> Telegram. The existing shared mtg secret and FakeTLS hostname cloud.yandex.ru remain unchanged.
- New WireGuard peer addressing is relay 10.67.0.1/32 to DE interface wg-mtg; DE retains 10.66.0.2 and UDP 51820. The relay routes only the backend 10.66.0.2/32 through this peer and uses PersistentKeepalive 25.
- DE firewall permits 138.16.175.166 only to 8443/tcp and 51820/udp, and permits 10.67.0.1 only through wg-mtg to 10.66.0.2:3128. The mtg backend must not be exposed publicly.
- The former Yandex relay 178.154.193.39 and WireGuard peer 10.66.0.1/32 are no longer the verified primary path. Their DE peer and address-specific firewall rules remain temporarily until an explicit retirement decision.
- Temporary direct-DE Reality on 147.45.196.137:443 remains a non-primary fallback pending the scheduled post-soak cleanup. Do not confuse its client credentials with either the VDSina relay public inbound or DE:8443 backhaul credentials.
- Baseline Reality camouflage for both relay public inbound and DE backhaul remains www.cloudflare.com. The temporary direct profile may have independent live credentials managed in 3x-ui.
- Server-side validation passed for managed services/listeners, WireGuard handshake, DE:8443, private mtg backend and HAProxy backend. User validation passed for VPN DE egress/sites/reconnect and Telegram connection/messages/media/reconnect.
- Operational Windows SSH aliases are `ruhop` for the VDSina relay and `dev` for DE; aliases contain username, identity and port and should be used instead of duplicating those parameters.
- From the Windows vpn-relay-bootstrap checkout, `.\deliver.ps1 ruhop` delivers committed HEAD without bootstrap, and `.\get-links.ps1` explicitly displays the VLESS and MTProto credential links. The latter uses `ruhop` for VLESS state and `dev` only to read the protected mtg secret while forming public endpoint 138.16.175.166:9443.
- The live mtg config is protected as 0640 root:mtg for the dedicated static mtg service account. Group-write, any world access, or a different group is not accepted by client-link tooling.
- Reality private keys, shared client UUID, DE backhaul credentials, WireGuard private keys and MTProto secret must not be stored in project-memory or public documentation. Keep generated client material in protected storage and treat terminal link output as credentials.

## References

- session-note:vpn-reality:2026-10-11:vdsina-ru-relay-bootstrap
- session-note:vpn-reality:2026-10-11:vdsina-ru-relay-client-validation
- session-note:vpn-reality:2026-10-11:ruhop-client-link-tooling
- verification-result:vpn-reality:2026-10-11:vdsina-ru-relay-server-checks
- verification-result:vpn-reality:2026-10-11:vdsina-ru-relay-end-to-end
- verification-result:vpn-reality:2026-10-11:ruhop-windows-link-tooling
- runbook:vpn-reality:client-link-retrieval
- runbook:vpn-reality:two-hop-mtg-proxy
- provider-note:vpn-reality:vdsina
- decision:vpn-reality:2026-10-11:shared-ruhop-vless-identity
- decision:vpn-reality:2026-06-25:cloudflare-mask-over-microsoft-for-reality
