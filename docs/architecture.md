# Firmware Architecture

## Overview

This project uses Arduino-style C++ for RP2040-class boards (Pico/Pico W) and is organized for clarity without altering the original logic.

## File Layout

- `src/main.cpp`: Original application logic (`setup()` / `loop()`), preserved.
- `docs/wiring.md`: Hardware connectivity and pin mapping.
- `docs/architecture.md`: This architecture overview.
- `README.md`: User-facing setup and usage guide.
- `CMakeLists.txt`: Documentation scaffold noting Arduino-based build expectations.

## Runtime Behavior

1. **Initialization (`setup`)**
   - Configures all 12 LED GPIOs as outputs.
   - Drives all LEDs LOW at startup.

2. **Main loop (`loop`)**
   - Polls keypad using `keypad.getKey()`.
   - On valid key press (`key != NO_KEY`), executes a switch-case action.
   - Keys map to individual or grouped LED ON/OFF operations.
   - Includes `delay(10)` for simple scan pacing.

## Key-to-Action Summary

- `1..8`: Turn ON corresponding blue LED.
- `9`: Turn ON all blue LEDs (indices 0..7).
- `0`: Turn OFF all blue LEDs (indices 0..7).
- `A..D`: Turn ON corresponding red LED.
- `*`: Turn ON all red LEDs (indices 8..11).
- `#`: Turn OFF all red LEDs (indices 8..11).

## Assumptions

- The provided source is authoritative and intentionally Arduino API-based (`Keypad.h`, `pinMode`, `digitalWrite`).
- No behavioral refactor to native Pico SDK APIs is performed to avoid logic changes.
