# Development workflow

## Branch policy

- `main` is the protected stable baseline.
- Work on feature branches and merge through pull requests.
- CI artifacts are test outputs, not OTA releases.
- Never publish firmware until compile, security checks and required hardware
  validation are recorded.

## Build

The repository uses PlatformIO with the ESP32-C3 DevKitM-1 board definition
and Arduino framework. Verify the exact physical board and partition layout
before treating the build as deployable.

## Secrets

Never commit Wi-Fi passwords, Apps Script credentials, API tokens or signing
private keys. Use GitHub Actions secrets only for CI tasks that actually need
them. The ESP firmware must not contain a GitHub personal access token.

## Simulation and hardware

Wokwi may cover supported peripherals and deterministic logic. MPPT, battery,
BMS, real Wi-Fi/TLS and power-failure behavior still require physical tests.
