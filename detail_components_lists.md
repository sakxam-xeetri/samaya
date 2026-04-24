# Automatic School Bell System - Bill of Materials & Setup Guide

## Project Overview

A fully autonomous, microcontroller-based automatic bell system designed for educational institutions. Features include accurate RTC-based scheduling, high-quality MP3 audio playback, offline web configuration, emergency override, and 24/7 continuous operation capability.

**Target Platform:** ESP32-S3 Dual-Core Microcontroller
**Power Input:** 100-240V AC Mains (via internal HLK-PM5 module)
**Audio Output:** Line-level 3.5mm stereo (connects to existing PA amplifier)

---

## Table of Contents

- [Safety Warning](#safety-warning)
- [Bill of Materials](#bill-of-materials)
  - [A. Core Modules](#a-core-modules)
  - [B. User Controls & Indicators](#b-user-controls--indicators)
  - [C. Power System (Safety Critical)](#c-power-system-safety-critical)
  - [D. Passive Components](#d-passive-components)
  - [E. Connectors, Wiring & Enclosure](#e-connectors-wiring--enclosure)
  - [F. Tools & Accessories](#f-tools--accessories)
- [Component Notes & Specifications](#component-notes--specifications)
- [Pre-Assembly Checklist](#pre-assembly-checklist)
- [Wiring Quick Reference](#wiring-quick-reference)
- [Safety Requirements](#safety-requirements)
- [Estimated Cost](#estimated-cost)

---

## Safety Warning

> ⚠️ **DANGER - HIGH VOLTAGE**
> This project involves connecting to mains electricity (100-240V AC).
> Improper assembly can cause **electric shock, fire, or death**.
>
> - All AC wiring must be done by a qualified person
> - AC section must be physically separated from low-voltage DC section
> - Metal enclosure must be connected to Earth ground
> - Fuse and surge protection are MANDATORY
> - Disconnect power before opening enclosure
> - Use heat-shrink tubing on all AC connections

---

## Bill of Materials

### A. Core Modules

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| A1 | ESP32-S3 Dev Board | 1 | ESP32-S3-DevKitC-1 (N16R8) | Must have 8MB PSRAM for audio buffering |
| A2 | RTC Module | 1 | DS3231 I2C Module | Includes battery holder |
| A3 | Battery | 1 | CR2032 3V Lithium Coin Cell | Backup power for RTC |
| A4 | Audio DAC Module | 1 | PCM5102A I2S Module | Must have 3.5mm output jack |
| A5 | SD Card Module | 1 | SPI MicroSD Reader (3.3V) | Logic level compatible |
| A6 | MicroSD Card | 1 | 8-16GB High Endurance | FAT32 formatted. Use High Endurance type |
| A7 | LCD Display | 1 | 16x2 Character LCD + I2C Backpack | PCF8574 adapter, address 0x27 or 0x3F |

---

### B. User Controls & Indicators

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| B1 | Push Buttons | 4 | 16mm Panel Mount, Momentary, N.O. | CONFIG, BYPASS, EMERGENCY, Enable/Disable |
| B2 | LEDs | 4 | 5mm, 3V, 20mA | Red (Emergency), Green (Status), Blue (WiFi), Yellow (Enable/Disable) |
| B3 | Resistors | 4 | 330Ω, 1/4W, ±5% | LED current limiting |
| B4 | Active Buzzer | 1 | 5V DC, Self-oscillating | Built-in driver, no external circuit needed |
| B5 | Diode (Optional) | 1 | 1N4148 Signal Diode | Flyback protection if using passive buzzer |---------optional if using active buzzer---

---

### C. Power System (Safety Critical)

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| C1 | AC-DC Module | 1 | HLK-PM5 (Hi-Link) | 5V 1A, Isolated, 3000V isolation |
| C2 | AC Inlet Socket | 1 | IEC C14 Panel Mount, Male | Standard computer power cord compatible |
| C3 | AC Power Cord | 1 | IEC C13 to Local Plug | Standard computer power cable |
| C4 | AC Rocker Switch | 1 | SPST, 250V 6A, Illuminated | Panel mount, mains rated |
| C5 | Fuse Holder | 1 | 5x20mm, Panel/PCB Mount | Enclosed type recommended |
| C6 | Fuse | 1 | 500mA, Slow-Blow, 250V AC | Time-delay type for inrush current |
| C7 | Varistor (MOV) | 1 | 10D471K (230V) or 10D271K (120V) | Surge protection across L-N |

---

### D. Passive Components

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| D1 | Resistors | 10 | 10kΩ, 1/4W, ±5% | Button pull-ups |
| D2 | Resistors | 4 | 4.7kΩ, 1/4W, ±5% | I2C pull-ups (SDA, SCL) |
| D3 | Resistors | 3 | 22Ω, 1/4W, ±5% | I2S series termination |
| D4 | Capacitor, Electrolytic | 1 | 1000µF, 16V | Main 5V rail bulk filtering |
| D5 | Capacitor, Electrolytic | 2 | 100µF, 16V | DAC power filter, RTC hold-up |
| D6 | Capacitor, Electrolytic | 2 | 10µF, 16V | ESP32 power filter |
| D7 | Capacitor, Ceramic | 10 | 100nF (0.1µF), X7R, 25V | Module decoupling |

---

### E. Connectors, Wiring & Enclosure

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| E1 | Jumper Wires | 1 set | Male-to-Female Dupont, 20cm, 40pcs | Module connections |
| E2 | Jumper Wires | 1 set | Female-to-Female Dupont, 20cm, 20pcs | I2C & power connections |
| E3 | Audio Jack | 1 | 3.5mm Stereo, Panel Mount, Female | Breaks out to screw terminals |
| E4 | Audio Cable | 1 | 3.5mm Male-to-Male, 1-3m | To connect to PA amplifier |
| E5 | Terminal Block | 2 | 2-pin, 5.08mm pitch | AC input wiring |
| E6 | Terminal Block | 1 | 3-pin, 5.08mm pitch | Audio jack connection |
| E7 | Project Enclosure | 1 | ABS or Metal, ~150x120x80mm | With ventilation holes |
| E8 | Standoffs + Screws | 1 set | M3 Nylon, assorted heights | Module mounting |
| E9 | Cable Glands | 2 | PG7 or PG9 | AC input & audio output strain relief |
| E10 | Heat Shrink Tubing | 1 set | Assorted sizes | AC wire insulation |
| E11 | Solid Core Wire | 1 roll | 22 AWG, assorted colors | For AC section wiring |
| E12 | Solder Wire | 1 roll | 60/40 or 63/37, 0.8mm | For button/LED connections |

---

### F. Tools & Accessories

| # | Item | Qty | Part Number / Specification | Notes |
|:-:|:-----|:---:|:----------------------------|:------|
| F1 | USB-C Cable | 1 | Data capable | For programming ESP32-S3 |
| F2 | Multimeter | 1 | Digital | Voltage verification essential |
| F3 | Soldering Iron | 1 | 25-40W temperature controlled | Panel mount component soldering |
| F4 | Wire Stripper/Cutter | 1 | AWG 10-24 capable | Wire preparation |
| F5 | Screwdriver Set | 1 | Precision + Standard | Enclosure assembly |
| F6 | Hot Glue Gun | 1 | Standard craft type | Strain relief and insulation |

---

## Component Notes & Specifications

### ESP32-S3 Development Board