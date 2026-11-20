# Wald Energy

ESP32-C3 firmware and release repository.

## Repository layout

- `firmware/` — Arduino source sketches and private-config template.
- `releases/` — public update manifest consumed by the ESP32.
- `docs/` — setup, security and release instructions.
- `tools/` — local helper scripts for preparing releases.

## Security rules

- Never commit Wi-Fi passwords, dashboard credentials, Google Apps Script tokens, API tokens, or private signing keys.
- `firmware/private_config.example.h` is a template only. Copy it to `private_config.h` locally and fill in secrets there.
- `private_config.h`, signing private keys, compiled local config files and build outputs are ignored by Git.
- A public GitHub release is downloadable by anyone. Firmware authenticity must be checked using a signature whose private key is kept offline.

## Current baseline

The hardware-tested baseline is Wald Energy v2.5.0. On 2026-11-20, the user observed two successful Google Sheets uploads: 2 attempts, 2 successes, HTTP 200, response `OK`.

This repository scaffold does not yet contain a v2.6.0 firmware. Do not publish a release until the firmware has been compiled for the ESP32-C3 and tested on hardware.

## First setup

1. Upload this folder's contents to the empty GitHub repository `jett73637/Wald-Energy`.
2. Keep the repository public if the ESP should download release assets without GitHub authentication.
3. Add the actual firmware only after secrets have been removed from the source.
4. Create a GitHub Release only after a tested `.bin`, manifest and valid signature exist.
