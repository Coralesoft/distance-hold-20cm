# Distance-Hold @ 20 cm (ESP32 + OLED + HC-SR04)

Simple “Target Timer” build: hold your hand/object at **20.0 cm ± 2 cm** for **10 s**.  
When you’re in range the timer runs; drift out and it pauses. Success beeps + summary on screen.

## Features
- Live distance display on SSD1306 (128×32)
- In-range tick + out-of-range chirp
- 10 s progress bar and success screen
- Safe 5 V → 3.3 V ECHO divider for ESP32

## Hardware
- ESP32-HW-394
- SSD1306 0.91" OLED (I²C 0x3C)
- HC-SR04 ultrasonic (5 V) with 10k/20k divider on ECHO
- Push button (D18→GND), active buzzer (D15)

## Wiring (HC-SR04)
| HC-SR04 | ESP32 | Notes |
|---|---|---|
| VCC | VIN (5 V) | 5 V power |
| GND | GND | — |
| TRIG | D5 | — |
| ECHO | D4 | **via 10k/20k divider → ~3.3 V** |

OLED: SDA=D21, SCL=D22. Button: D18→GND. Buzzer: D15→+, −→GND.

## Build
- Arduino IDE: add **Adafruit SSD1306** + **Adafruit GFX**
- Open `firmware/distance_hold_20cm.ino` and flash to ESP32

## Tuning
Edit constants in code:
- `TARGET_CM` (default 20.0)
- `WINDOW_CM` (±2.0)
- `HOLD_MS` (10000)

## Evidence (for submission)
- Wiring photo showing the ECHO divider
- Short clip: live distance → hold at ~20 cm → success beeps + screen
- Screenshot of the code highlighting the window + hold time

## Licence
MIT
