# Firmware source

Place the active Wald Energy ESP32-C3 source here.

Accepted entry points:
- `main.cpp`
- One or more Arduino `.ino` files

Do not copy secrets into this directory. Keep local credentials in an ignored
`private_config.h`; commit only a sanitized example template.

The CI build is intentionally skipped until an actual source entry point exists.
