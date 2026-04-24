```txt
========================================================
SAMAYA AUTOMATIC SCHOOL/COLLEGE BELL SYSTEM
HARDWARE CIRCUIT CONNECTION README
Hardware Revision A
========================================================


1. PROJECT OVERVIEW
--------------------------------------------------------
SAMAYA is a production-level fully offline automatic
school/college bell and announcement system built using:

- ESP32-S3 DevKitC-1
- DS3231 RTC
- MicroSD Audio Storage
- PCM5102A Audio DAC
- 16x2 I2C LCD
- Industrial AC-DC Power Supply

The system provides:
- Automated bell scheduling
- Audio announcement playback
- Emergency alerts
- Offline hotspot configuration
- Long-term unattended operation


========================================================
2. POWER SYSTEM
========================================================

AC INPUT:
230VAC
   |
   v
HLK-PM5 AC-DC MODULE
   |
   v
5V DC POWER RAIL

5V RAIL DISTRIBUTION:
- ESP32-S3 VIN
- DS3231 RTC Module
- 16x2 LCD Module
- SD Card Module
- PCM5102A DAC

PROTECTION COMPONENTS:
- Fuse (500mA–1A)
- MOV surge protection

POWER FILTERING:
- 1000uF bulk capacitor across 5V rail
- 100uF capacitor near ESP32
- 0.1uF decoupling capacitor at each module


IMPORTANT:
- All grounds must be common.
- Never connect 5V directly to ESP32 GPIO.


========================================================
3. MAIN CONTROLLER
========================================================

DEVICE:
ESP32-S3 DevKitC-1

SUPPLY:
VIN -> 5V
GND -> Common Ground

GPIO LOGIC LEVEL:
3.3V ONLY


========================================================
4. I2C BUS CONNECTIONS
========================================================

GPIO ASSIGNMENT:
GPIO8  -> SDA
GPIO9  -> SCL


--------------------------------
DS3231 RTC MODULE
--------------------------------

VCC -> 5V
GND -> GND
SDA -> GPIO8
SCL -> GPIO9
SQW -> GPIO4 (optional interrupt)


--------------------------------
16x2 LCD I2C MODULE
--------------------------------

VCC -> 5V
GND -> GND
SDA -> GPIO8
SCL -> GPIO9

Typical address:
0x27 or 0x3F


--------------------------------
OPTIONAL I2C PULLUPS
(Only if modules do not have them)
--------------------------------

SDA -> 4.7k resistor -> 3.3V
SCL -> 4.7k resistor -> 3.3V

Use only ONE set of pullups.


========================================================
5. SD CARD MODULE (SPI)
========================================================

GPIO10 -> CS
GPIO11 -> MOSI
GPIO12 -> SCK
GPIO13 -> MISO

POWER:
VCC -> 5V
GND -> GND

FILTERING:
- 10uF capacitor
- 0.1uF capacitor


========================================================
6. PCM5102A AUDIO DAC (I2S)
========================================================

GPIO16 -> BCLK
GPIO17 -> LRCK
GPIO18 -> DIN


RECOMMENDED SERIES RESISTORS:
22 ohm on each line:

GPIO16 -> 22R -> BCLK
GPIO17 -> 22R -> LRCK
GPIO18 -> 22R -> DIN


POWER:
VCC -> 5V
GND -> GND


AUDIO OUTPUT:

L OUT -> 3.5mm jack Left
R OUT -> 3.5mm jack Right
GND   -> Audio Ground

Output goes to external amplifier line input.


========================================================
7. PUSH BUTTON CONTROLS
========================================================

BUTTON WIRING:

GPIO ---- Button ---- GND
 |
 10k pullup resistor
 |
3.3V


ACTIVE LOW LOGIC:
Pressed = LOW


BUTTON GPIOs:

GPIO21 -> Next Bell Button
GPIO38 -> Emergency Button
GPIO39 -> Config Button
GPIO40 -> Enable/Disable Switch


========================================================
8. STATUS LEDS
========================================================

LED WIRING:

GPIO -> 330 ohm resistor -> LED -> GND


GPIO1  -> Power LED
GPIO7  -> Status LED
GPIO15 -> Emergency LED
GPIO48 -> Enable LED

Optional:
GPIO14 -> Buzzer


========================================================
9. DECOUPLING CAPACITORS
========================================================

Use 0.1uF at every module:

- RTC
- LCD
- SD
- DAC

Use 0.1uF + 10uF parallel for:
- ESP32
- SD Module
- DAC


========================================================
10. GROUNDING GUIDELINES
========================================================

- Single common ground reference
- Use ground plane if PCB
- Keep audio traces away from power traces
- Keep analog and digital routing clean
- Use star grounding if possible


========================================================
11. GPIO SUMMARY
========================================================

I2C:
GPIO8   SDA
GPIO9   SCL

SPI:
GPIO10  CS
GPIO11  MOSI
GPIO12  SCK
GPIO13  MISO

I2S:
GPIO16  BCLK
GPIO17  LRCK
GPIO18  DIN

BUTTONS:
GPIO21  Next Bell
GPIO38  Emergency
GPIO39  Config
GPIO40  Enable

INDICATORS:
GPIO1   Power LED
GPIO7   Status LED
GPIO14  Buzzer
GPIO15  Emergency LED
GPIO48  Enable LED


========================================================
12. FIRMWARE SAFETY FEATURES
========================================================

Implement:
- Hardware watchdog
- Auto schedule resume after reboot
- RTC validity check
- SD card failure detection
- Emergency override priority


========================================================
13. TEST POINTS (RECOMMENDED)
========================================================

Add PCB test pads for:

- 5V
- 3.3V
- GND
- SDA
- SCL
- BCLK
- LRCK
- DATA


========================================================
14. PRE-POWER CHECKLIST
========================================================

[ ] Common grounds connected
[ ] No 5V connected to GPIO pins
[ ] Button pullup resistors installed
[ ] I2C pullups verified
[ ] Decoupling capacitors installed
[ ] 22 ohm I2S resistors installed
[ ] Fuse installed
[ ] MOV installed
[ ] Audio jack wired correctly


========================================================
15. SYSTEM BLOCK FLOW
========================================================

230VAC
 |
 v
HLK-PM5
 |
 v
5V Rail
 |
 +--- ESP32-S3
 |      |
 |      +--- RTC
 |      +--- LCD
 |      +--- SD Card
 |      +--- DAC
 |      +--- Buttons
 |      +--- LEDs
 |
 +--- External Amplifier (via DAC output)


========================================================
CORE COMPONENTS
========================================================

- ESP32-S3 DevKitC-1
- DS3231 RTC
- PCM5102A DAC
- MicroSD Module
- 16x2 LCD I2C
- HLK-PM5 Power Module

Designed For:
- Fully Offline Operation
- Industrial Reliability
- Long-Term Deployment
- School/College Automation


========================================================
END OF HARDWARE CIRCUIT CONNECTION README
========================================================
```
