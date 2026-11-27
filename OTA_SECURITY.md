# Remote OTA security

The ESP32-C3 firmware reads `releases/latest.json` from this repository over HTTPS with certificate validation enabled. The manifest is accepted only when its fields match the firmware's validator and its ECDSA signature verifies against the public key compiled into the firmware.

## Manifest format

Required fields:

- `version`: three-part numeric version, newer than the installed version
- `target`: exactly `esp32c3`
- `size`: firmware image size in bytes, between 10,000 and 1,500,000
- `sha256`: hexadecimal SHA-256 digest of the exact firmware image
- `url`: HTTPS GitHub Release asset URL under `https://github.com/jett73637/Wald-Energy/releases/download/`
- `signature_algorithm`: `ECDSA-P256-SHA256`
- `signature`: Base64-encoded ASN.1 DER ECDSA P-256 signature

The signed UTF-8 message is exactly these five values joined by newline characters, with no trailing newline:

```text
version
target
size
sha256
url
```

The current `releases/latest.json` is an intentionally non-installable template: size is zero and URL, digest, version, and signature are empty. It does not represent a release.

## Signing and release rules

- The signing private key must match the ECDSA P-256 public key compiled into the firmware.
- Keep the private key offline or in a protected signing environment. Never commit it, place it in a public release, or embed it in the ESP.
- A release requires a built firmware image, a verified SHA-256 digest, a valid signature over the exact canonical message, and a GitHub Release asset URL.
- SHA-256 detects corruption but does not prove publisher identity. HTTPS does not replace firmware signing.
- Never use a blank or invalid signature, and do not bypass signature verification.
- Confirm the exact board flash size, OTA partition layout, and bootloader rollback behavior before installing a release.

The currently committed firmware uses ECDSA P-256. Do not switch to Ed25519 unless the firmware verifier and its embedded public key are intentionally changed and the new firmware is built and tested.
