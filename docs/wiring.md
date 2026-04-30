# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Components (from `diagram.json`)

- 1x Raspberry Pi Pico / Pico W-compatible board (`wokwi-pi-pico`)
- 1x 4x4 membrane keypad (`wokwi-membrane-keypad`)
- 12x LEDs (`wokwi-led`)
  - 8 blue LEDs labeled `1..8`
  - 4 red LEDs labeled `A..D`
- 12x LED series resistors (`220Ω`, ids `r1..r12`)
- 4x keypad pull-up resistors (`1kΩ`, ids `rp1..rp4`)

## GPIO Map

### Keypad Matrix

| Keypad Line | Pico GPIO |
|---|---|
| C4 | GP16 |
| C3 | GP17 |
| C2 | GP18 |
| C1 | GP19 |
| R4 | GP20 |
| R3 | GP21 |
| R2 | GP22 |
| R1 | GP26 |

> Note: The firmware uses `rowPins = {26,22,21,20}` and `colPins = {19,18,17,16}`.

### LED Outputs

| LED label | Firmware index | Pico GPIO |
|---|---:|---:|
| 1 | ledPins[0] | GP11 |
| 2 | ledPins[1] | GP10 |
| 3 | ledPins[2] | GP9 |
| 4 | ledPins[3] | GP8 |
| 5 | ledPins[4] | GP7 |
| 6 | ledPins[5] | GP6 |
| 7 | ledPins[6] | GP5 |
| 8 | ledPins[7] | GP4 |
| A | ledPins[8] | GP3 |
| B | ledPins[9] | GP2 |
| C | ledPins[10] | GP28 |
| D | ledPins[11] | GP27 |

All LED cathodes connect to GND. Each LED anode is driven from a GPIO through a 220Ω resistor.

## Electrical Notes

- Keypad row lines have external 1kΩ pull-ups to 3V3 (`rp1..rp4`).
- LED drive is active-high from GPIO.
- Shared reference ground is required across all devices.
