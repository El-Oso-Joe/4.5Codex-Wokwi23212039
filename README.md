# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W-compatible project that reads a 4x4 matrix keypad and controls 12 LEDs. The firmware is preserved exactly in Arduino-style C++ logic while repository structure and documentation are normalized for maintainability.

## Features

- 4x4 keypad input scanning via `Keypad` library
- 12 individually addressable LED outputs
- Group controls:
  - `9`/`0` => all blue LEDs ON/OFF
  - `*`/`#` => all red LEDs ON/OFF
- Clean project documentation for Wokwi and hardware bring-up

## Repository Structure

```text
.
├── CMakeLists.txt
├── README.md
├── src/
│   └── main.cpp
├── include/
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Source Compatibility Note

The provided firmware uses Arduino APIs (`setup()`, `loop()`, `Keypad.h`). It is therefore best built with an Arduino RP2040 core or run in Wokwi Arduino simulation.

A native Pico SDK port is intentionally not done here to preserve behavior exactly.

## Pin Mapping

See full mapping in [`docs/wiring.md`](docs/wiring.md).

## Run in Wokwi

1. Create/open a **Raspberry Pi Pico** project in Wokwi.
2. Copy `src/main.cpp` into the sketch source.
3. Use the provided `diagram.json` wiring.
4. Ensure `Keypad` library is available in the project configuration.
5. Start simulation and press keypad buttons.

## Run on Real Pico W Hardware (Arduino Core Path)

1. Install Arduino IDE 2.x.
2. Install **Raspberry Pi RP2040** board support package (Arduino core).
3. Install library: **Keypad** by Mark Stanley / Alexander Brevig.
4. Create sketch and paste `src/main.cpp` content.
5. Select board: **Raspberry Pi Pico W**.
6. Build and upload over USB.

## Wi-Fi / Secrets

- This firmware does **not** use Wi-Fi, despite targeting Pico W hardware.
- No credentials are required.
- If Wi-Fi is added later, store credentials in ignored local config (never commit secrets).

## Flashing Notes (UF2 workflow)

If using Arduino IDE upload fails, use BOOTSEL mode:

1. Hold **BOOTSEL** while plugging USB.
2. Pico appears as a USB mass storage device.
3. Export/copy generated `.uf2` to the device.
4. Board reboots and starts firmware.

## Behavior Reference

- `1..8`: turn on corresponding blue LED
- `9`: all blue ON
- `0`: all blue OFF
- `A..D`: turn on corresponding red LED
- `*`: all red ON
- `#`: all red OFF
