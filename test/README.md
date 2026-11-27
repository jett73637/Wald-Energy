# Test strategy

Planned layers:

1. Compile check: PlatformIO builds the ESP32-C3 Arduino target.
2. Unit tests: pure logic such as scheduling, event deduplication, payload
   validation and ring-buffer behavior, separated from hardware APIs.
3. Simulation: Wokwi for supported GPIO/peripheral behavior.
4. Hardware validation: real ESP32-C3, MPPT, battery/BMS, Wi-Fi and Apps Script.

A simulator result is not a substitute for real electrical or network testing.
Record each test as PASS, FAIL, BLOCKED or NOT RUN, with firmware commit,
board, toolchain and test conditions.
