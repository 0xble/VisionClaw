# Maintenance

## Background

Maintained source fork: `0xble/VisionClaw` of `Intent-Lab/VisionClaw`, both
`main`. This temporary clone was inspected from owned `origin/main`
`193e972a727610186c24a2eabaa1a86bd7998e20`; accepted upstream baseline:
`b06ed115cc139453e748b689432cf711819837d7`. Publish only to `origin`, never
upstream. Build, installation, device access, and runtime operation remain
separate stages.

## Preserve

- The CameraAccess OpenClaw bridge reports usable connectivity/auth failures and
  keeps configured model and thinking overrides through settings.

## Active patches

### VISIONCLAW-001: `fix: tighten OpenClaw bridge connectivity and auth errors`

- **Provenance:** `fd2bd1c50d76d00a5f212ab235765fa486ddda8f`.
- **Surfaces:** `samples/CameraAccess/CameraAccess/OpenClaw/OpenClawBridge.swift`.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.
- **Regression:** Blocked: no focused offline/auth-error test was added; add one before reconciliation or publication.
- **Rollback:** Revert `fd2bd1c50d76d00a5f212ab235765fa486ddda8f` and run the complete gate.
- **Retire when:** an upstream release gives equivalent connectivity/auth handling with focused proof.

### VISIONCLAW-002: `feat: add OpenClaw model and thinking overrides`

- **Provenance:** `193e972a727610186c24a2eabaa1a86bd7998e20`.
- **Surfaces:** `GeminiConfig.swift`, `OpenClawBridge.swift`, `Secrets.swift.example`, `SettingsManager.swift`, `SettingsView.swift` under `samples/CameraAccess/CameraAccess`.
- **Upstream issue / PR:** None after checked 2026-09-09 / None after checked 2026-09-09.
- **Regression:** Blocked: no focused settings-to-request override test was added; add one before reconciliation or publication.
- **Rollback:** Revert `193e972a727610186c24a2eabaa1a86bd7998e20` and run the complete gate.
- **Retire when:** an upstream release preserves model/thinking override propagation with focused proof.

## Update and verify

Every run fetches owned `main` and latest upstream `main`, reconciles only these
active patches, then runs the repository's documented CameraAccess test and
build gate. It is `Blocked` until the two focused regressions exist; do not
invent a simulator/device command. Immediately fetch upstream again;
`git rev-list --left-right --count upstream/main...main` must have zero
upstream-only commits. After authorized publication require local/`origin/main`
SHA parity. Installation, device deployment, and runtime proof require separate
authorization and exact runtime-SHA evidence.
