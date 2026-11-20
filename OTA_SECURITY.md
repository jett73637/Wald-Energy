# Remote OTA security design

Target design:
1. ESP fetches release metadata over HTTPS with certificate validation.
2. ESP validates manifest schema, version policy, file size and SHA-256.
3. ESP verifies an Ed25519 signature using a public key compiled into firmware.
4. Only then does it write the inactive OTA partition.
5. After reboot, a bounded self-test confirms the image only if bootloader rollback is actually enabled and the device is healthy.

Important:
- SHA-256 alone detects corruption but does not prove publisher identity.
- HTTPS alone does not replace firmware signing.
- A public release is public to download; do not embed a GitHub personal access token in the ESP.
- The OTA partition table and bootloader rollback configuration must be verified for the exact ESP32-C3 board/build.
- Do not use the placeholder `latest.json` as a real release.
