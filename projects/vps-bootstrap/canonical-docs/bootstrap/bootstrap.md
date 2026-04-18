---
date: 2026-04-18
recorded_at: 2026-04-18T14:38:04.588Z
project: vps-bootstrap
topic: bootstrap
registry_scope: bootstrap
source: agent
status: active
---
# Canonical Doc

## Summary

Authoritative description of the bootstrap flow, including phased execution and managed shell-profile provisioning.

## Guidance

- `full` remains the default mode and executes the complete VPS bootstrap flow end to end.
- The bootstrap flow is split into explicit phases: `prepare-system`, `provision-user`, `stage-ssh`, and `finalize-hardening`.
- `prepare-system` is responsible for package installation and ensuring the SSH service is enabled and running.
- `provision-user` creates or updates the sudo user, installs the SSH public key, and manages the user's `.bashrc` and `.profile` through bootstrap-owned blocks.
- `stage-ssh` adds the target SSH port alongside the currently active ports, validates and reloads `sshd`, verifies that the target port is listening, and updates `ufw` to allow the staged ports.
- `finalize-hardening` must only be run after the target port is already staged in `sshd`; it cuts over to the target port only, disables root SSH login, applies the final password-auth policy, and narrows `ufw` to that port.
- The intended manual split is `prepare-system` -> `provision-user` -> `stage-ssh` -> manual login verification on the new port -> `finalize-hardening`.
- The bootstrap-managed shell profile mirrors the current machine's prompt style, `tm` alias, `~/.local/bin` PATH handling, and conditional `nvm` loading without requiring `tmux` or `nvm` to be installed on the VPS.
- Repository validation after bootstrap changes remains `bash -n ./bootstrap.sh`, `bash -n ./tests/bootstrap.test.sh`, and `./tests/bootstrap.test.sh`.

## References

- runbook:vps-bootstrap:2026-04-18:repo-validation
