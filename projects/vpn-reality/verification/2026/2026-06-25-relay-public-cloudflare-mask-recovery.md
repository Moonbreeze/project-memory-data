---
date: 2026-06-25
recorded_at: 2026-06-25T18:23:38.747Z
project: vpn-reality
topic: relay-public-cloudflare-mask-recovery
source: agent
status: active
---
# Verification Result

## Scope

Relay-first public inbound and DE backhaul REALITY handshake recovery

## Steps

- Validated relay `xray` config and listener on `443/tcp`.
- Captured relay `journalctl -u xray -f` and tcpdump during failing client attempts; observed old `relay-public` REALITY handshake failures before VLESS auth.
- Created temporary `relay-test` inbound on relay with `www.cloudflare.com` mask host and confirmed successful REALITY handshake plus accepted inbound traffic.
- Captured tcpdump on DE `8443/tcp`; observed TCP handshake and payload arrival from relay followed by immediate close on DE backhaul inbound.
- Compared relay outbound `de-backhaul` and DE inbound `8443`; confirmed UUID, flow, security, serverName, shortId and keypair alignment.
- Changed DE inbound `8443` REALITY `dest/serverNames` to `www.cloudflare.com`, changed relay outbound `de-backhaul.serverName` to `www.cloudflare.com`, and re-tested traffic.

## Result

Recovery successful. Public-side REALITY handshake succeeds with Cloudflare-based mask host, relay accepts traffic again, and end-to-end relay-first traffic works after aligning DE backhaul mask host and relay outbound `serverName` to `www.cloudflare.com`. Previous Microsoft-based mask host produced handshake/EOF failures despite unchanged UUID/key parameters.
