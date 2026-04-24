
========================================================
DETAILED CIRCUIT PINOUT & INTERCONNECTION SPECIFICATION
ESP32-S3 BASED AUTOMATIC BELL SYSTEM -SAMAYA
========================================================

1. SYSTEM CONTROLLER
--------------------------------------------------------
Device: ESP32-S3-DevKitC-1
Operating Voltage: 5v
All GPIO levels: 3.3V logic

IMPORTANT:
- Do NOT apply 5V directly to any GPIO
- All grounds must be common

--------------------------------------------------------

2. POWER DISTRIBUTION
--------------------------------------------------------
PRIMARY INPUT:
AC 230V → HLK-PM5 AC-DC Module → 5V DC Output

5V RAIL DISTRIBUTION:
- LCD Display Module
- SD Card Module
- PCM5102A DAC Module
- ESP32-S3
- DS3231 RTC Module

RECOMMENDED FILTERING:
- 1000µF capacitor across 5V rail
- 47–100µF near ESP32 input
- 0.1µF decoupling at each module

--------------------------------------------------------

3. I2C COMMUNICATION BUS (SHARED BUS)
--------------------------------------------------------
Bus Type: I2C (Multi-device)

GPIO ASSIGNMENT:
GPIO 8  → SDA (Serial Data Line)
GPIO 9  → SCL (Serial Clock Line)

CONNECTED DEVICES:
- DS3231 RTC Module
- 16x2 LCD Display (I2C Backpack)

ELECTRICAL REQUIREMENTS:
- 4.7kΩ pull-up resistor on SDA → 3.3V
- 4.7kΩ pull-up resistor on SCL → 3.3V


-----this 4.7 k registors only if needed

NOTES:
- Keep I2C lines short (<30 cm recommended)
- Avoid parallel routing with power lines
- Only ONE set of pull-ups required

--------------------------------------------------------

4. REAL TIME CLOCK (RTC) CONNECTION
--------------------------------------------------------
Device: DS3231 RTC Module

PIN CONNECTION:
VCC  → 3.3V
GND  → GND
SDA  → GPIO 8
SCL  → GPIO 9
SQW  → GPIO 4 (Optional Interrupt Output)

FUNCTION:
- Maintains accurate system time
- Provides battery-backed timekeeping

--------------------------------------------------------

5. LCD DISPLAY (16x2 I2C)
--------------------------------------------------------
Device: 16x2 Character LCD with I2C Interface

PIN CONNECTION:
VCC  → 5V
GND  → GND
SDA  → GPIO 8
SCL  → GPIO 9

NOTES:
- Confirm I2C address (commonly 0x27 or 0x3F)
- Ensure contrast adjusted via onboard potentiometer

--------------------------------------------------------

6. SD CARD MODULE (SPI INTERFACE)
--------------------------------------------------------
Communication Type: SPI

GPIO ASSIGNMENT:
GPIO 11 → MOSI (Master Out Slave In)
GPIO 13 → MISO (Master In Slave Out)
GPIO 12 → SCK  (Serial Clock)
GPIO 10 → CS   (Chip Select)

POWER:
VCC → 5V (only if module has regulator)
GND → GND

RECOMMENDED ADDITIONS:
- 10–22µF capacitor near VCC
- 0.1µF decoupling capacitor



--------------------------------------------------------

7. AUDIO DAC (PCM5102A - I2S INTERFACE)
--------------------------------------------------------
Communication Type: I2S

GPIO ASSIGNMENT:
GPIO 16 → BCLK (Bit Clock)
GPIO 17 → LRCK (Left/Right Clock)
GPIO 18 → DIN  (Digital Audio Data)

POWER:
VCC → 5V
GND → GND

AUDIO OUTPUT:
L OUT → 3.5mm Jack (Left Channel)
R OUT → 3.5mm Jack (Right Channel)
GND   → Audio Ground

RECOMMENDED:
- Shielded cable for audio output
- 100µF coupling capacitors (optional for noise filtering)

--------------------------------------------------------

8. USER INPUT CONTROLS (BUTTONS)
--------------------------------------------------------
CONFIGURATION:
All buttons connected between GPIO and GND

GPIO ASSIGNMENT:
GPIO 2 → Next Bell Button
GPIO 3 → Emergency Button
GPIO 5 → Config Mode Button
GPIO 6 → System Enable/Disable Switch

LOGIC:
- Active LOW (pressed = 0)
with 
- 10kΩ pull-up resistor external


--------------------------------------------------------

9. STATUS INDICATOR LEDS
--------------------------------------------------------
GPIO ASSIGNMENT:
GPIO 1  → Power LED
GPIO 7  → Status LED
GPIO 15 → Emergency LED
Gpio 48  → Enable/disable Led
GPIO 14 → Buzzer (Optional)

CONNECTION:
GPIO → 330Ω resistor → LED → GND

NOTES:
- Use proper resistor to limit current
- Ensure LEDs do not exceed GPIO current limits

--------------------------------------------------------

10. AUDIO OUTPUT INTERFACE
--------------------------------------------------------
OUTPUT TYPE:
Analog stereo line-level output

CONNECTION:
DAC Output → 3.5mm Jack → External Amplifier Input

IMPORTANT:
- Do NOT connect directly to speakers
- Use amplifier for proper output power




--------------------------------------------------------

12. GROUNDING & LAYOUT GUIDELINES
--------------------------------------------------------
- Use single common ground reference
- Separate noisy power lines from audio lines
- Keep analog and digital grounds clean
- Use star grounding if possible

--------------------------------------------------------

13. CRITICAL DESIGN NOTES
--------------------------------------------------------
- Avoid using boot strapping pins for inputs
- Ensure all unused GPIOs are defined in firmware
- Keep power traces thick and short
- Keep signal traces clean and organized
- Place decoupling capacitors close to IC pins

--------------------------------------------------------

14. SYSTEM INTEGRATION SUMMARY
--------------------------------------------------------
ESP32-S3 acts as central controller interfacing with:
- RTC (timekeeping)
- SD Card (audio storage)
- DAC (audio output)
- LCD (user interface)
- Buttons & LEDs (control & feedback)

All subsystems operate synchronously to deliver
a fully automated bell and announcement system.

========================================================
END OF DETAILED PINOUT SPECIFICATION
========================================================
```

---

This version is now:

* ✔ engineering-grade
* ✔ unambiguous
* ✔ ready for PCB + documentation
* ✔ suitable for submission or product design

---
