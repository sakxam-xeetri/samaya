# SAMAYA

Smart Automatic Management and Announcement System for Academic Yards

A production-oriented automatic school/college bell and announcement platform designed for fully offline, reliable, long-duration operation in educational institutions.

## Table of Contents

1. Project Summary
2. Background and Need
3. Objectives
4. Core Features
5. System Architecture
6. Hardware Stack
7. GPIO and Interface Mapping
8. Power Design and Electrical Safety
9. Software Architecture
10. Operating Workflow
11. Data, Scheduling, and Audio Model
12. Consolidated Bill of Materials
13. Assembly and Integration Guide
14. Configuration and Daily Operation
15. Test and Commissioning Checklist
16. Reliability and Fail-Safe Behavior
17. Performance Targets and Lifecycle
18. Deployment Model for Schools and Colleges
19. Future Scope
20. Repository Document Map
21. Author and Contact
22. Status and Next Steps

## 1) Project Summary

SAMAYA is a fully offline embedded bell automation system for schools, colleges, coaching centers, and campus-style institutions. It combines accurate RTC-based scheduling, MicroSD audio playback, emergency override support, and a local hotspot configuration interface.

The platform is designed to integrate with existing PA amplifiers through clean line-level output, reducing deployment cost while improving punctuality, operational consistency, and safety readiness.

## 2) Background and Need

Many educational institutions still depend on manual bell ringing or rigid timer systems. Common field problems include:

- Human error and delayed bell events
- Dependence on support staff availability
- Seasonal timetable switching complexity
- Weak emergency signaling capability
- Poor flexibility for exams, events, and special days

SAMAYA addresses these constraints with a local, low-maintenance, production-focused architecture suitable for Kathmandu Valley and similar regions.

## 3) Objectives

- Automate routine bell and announcement execution without manual intervention
- Provide high-accuracy long-term timekeeping using DS3231 RTC
- Support weekly, seasonal, and special-day timetable logic
- Enable emergency siren and high-priority interruption handling
- Offer simple offline configuration using a phone or laptop
- Deliver robust power-safe operation for 24/7 use

## 4) Core Features

### Scheduling and Time Management

- 7-day programmable scheduling
- Unlimited bell events per day (implementation-defined limit)
- Winter and summer preset support
- Special-day schedule override
- Priority resolution model:
  Emergency > Special Day > Seasonal > Weekly
- Manual next-bell trigger
- Missed bell handling after restart
- RTC invalid-time detection and recovery flow

### Audio and Announcement Subsystem

- MicroSD-based media storage
- MP3 and WAV playback support
- Bell tone and voice announcement playback
- PCM5102A-based digital-to-analog conversion
- 3.5 mm stereo line-out for external amplifier input
- Audio fallback (default beep) if mapped file is missing

### User Interface and Controls

- 16x2 I2C LCD status interface
- Current time, next event, and mode display
- Dedicated physical buttons for operational controls
- System enable/disable control
- Status LEDs and optional buzzer feedback

### Reliability and Maintainability

- Auto-restart and schedule resume after power interruption
- Watchdog-assisted runtime recovery
- SD health and presence checks
- OTA firmware update capability (with safe rollback design target)
- Designed for unattended long-duration service

## 5) System Architecture

### Functional Block Flow

AC Mains -> Isolated AC-DC Supply -> 5V Rail -> ESP32-S3 Controller ->
RTC + LCD + SD + Controls + LEDs + I2S DAC -> External Amplifier -> Speakers

### Main Hardware Interfaces

- I2C: RTC and LCD
- SPI: MicroSD storage
- I2S: PCM5102A audio DAC
- GPIO: Buttons, LEDs, and optional buzzer

## 6) Hardware Stack

Primary modules used across project documentation:

- ESP32-S3 DevKitC-1 (main controller)
- DS3231 RTC module with CR2032 backup cell
- PCM5102A I2S DAC module
- SPI MicroSD module with high-endurance card
- 16x2 LCD with I2C backpack (PCF8574 typical)
- HLK-PM5 isolated AC-DC power module
- Panel buttons, LEDs, optional buzzer

## 7) GPIO and Interface Mapping

Documentation includes two pin profiles. Use one profile consistently in firmware.

### Recommended profile (Hardware Revision A)

I2C
- GPIO8: SDA
- GPIO9: SCL

SPI (SD)
- GPIO10: CS
- GPIO11: MOSI
- GPIO12: SCK
- GPIO13: MISO

I2S (DAC)
- GPIO16: BCLK
- GPIO17: LRCK
- GPIO18: DIN

Buttons
- GPIO21: Next Bell
- GPIO38: Emergency
- GPIO39: Config
- GPIO40: Enable/Disable

Indicators and alerts
- GPIO1: Power LED
- GPIO7: Status LED
- GPIO15: Emergency LED
- GPIO48: Enable LED
- GPIO14: Optional buzzer

Optional RTC interrupt
- GPIO4: SQW (optional)

### Alternate/legacy profile found in notes

Buttons appear as GPIO2, GPIO3, GPIO5, GPIO6 in one earlier circuit document.

Professional recommendation:
- Freeze a single final pin map before PCB/final harness production.
- Mirror this map in firmware constants and test documentation.

## 8) Power Design and Electrical Safety

### Power topology

- 230VAC input (region dependent)
- HLK-PM5 isolated AC-DC conversion to 5V rail
- 5V rail distribution to controller peripherals

### Protection and filtering

- Input fuse (500 mA to 1 A, slow-blow target)
- MOV surge suppression across line-neutral
- Bulk rail capacitor (1000 uF target)
- Local decoupling near each module (0.1 uF + 10/100 uF where needed)
- Optional 22 ohm series resistors on I2S digital lines

### Mandatory safety practices

- All mains work by qualified personnel only
- AC section physically isolated from low-voltage section
- No direct 5V injection into ESP32 GPIO lines
- Common ground strategy for low-voltage modules
- Proper enclosure, strain relief, and insulation in final build

## 9) Software Architecture

A task-oriented firmware model is intended:

- Real-time scheduler loop based on RTC readings
- Priority event engine for emergency and routine triggers
- Audio playback manager with file existence checks
- LCD/LED UI task for runtime state visibility
- Button input task with debounce and long-press logic
- Local hotspot web server for offline configuration updates

Suggested runtime states:

- BOOT
- RUN
- CONFIG
- EMERGENCY
- DISABLED
- FAULT

## 10) Operating Workflow

1. Power on and initialize hardware
2. Validate RTC and storage
3. Load schedule and audio mapping
4. Enter monitoring loop
5. Trigger bells/announcements at schedule match
6. Process manual and emergency controls at all times
7. Recover gracefully from faults and continue operation

## 11) Data, Scheduling, and Audio Model

Configuration is intended to be persisted on MicroSD.

Expected data categories:

- Weekly timetable definition
- Seasonal preset tables
- Special-day overrides
- Audio file mapping (event -> file path)
- Device settings (mode, timezone policy, output behavior)

Recommended file strategy:

- Human-readable config format (JSON or equivalent)
- Startup schema validation
- Backup configuration copy
- Last-known-good fallback file

## 12) Consolidated Bill of Materials

| Category | Key items |
| --- | --- |
| Controller | ESP32-S3 DevKitC-1 |
| Timekeeping | DS3231 + CR2032 |
| Audio | PCM5102A DAC + 3.5 mm out |
| Storage | SPI MicroSD module + 8-16 GB high-endurance card |
| Display | 16x2 LCD + I2C backpack |
| Power | HLK-PM5, IEC inlet, rocker switch, fuse holder, fuse, MOV |
| Controls | 4 momentary push buttons + enable switch function |
| Indicators | 4 LEDs + current-limit resistors |
| Passive | 10k pull-ups, 4.7k I2C pull-ups, 22 ohm I2S, decoupling capacitors |
| Integration | Terminal blocks, panel audio jack, wiring, glands, enclosure |
| Tools | USB cable, multimeter, soldering tools, hand tools |

For procurement details and quantity guidance, refer to detailed component lists in project documents.

## 13) Assembly and Integration Guide

1. Build and verify low-voltage prototype first (bench supply preferred)
2. Validate RTC, LCD, SD, and DAC communications independently
3. Integrate buttons, LEDs, and buzzer with pull-up/debounce logic
4. Add amplifier line-out path and verify clean audio
5. Only then integrate isolated AC stage and protections
6. Move to enclosure with AC/DC segregation and strain relief
7. Perform full-day dry-run schedule tests before site deployment

## 14) Configuration and Daily Operation

### Initial setup

- Enter config mode using dedicated button
- Connect to local hotspot from phone/laptop
- Set device time and upload schedule set
- Map event identifiers to audio files
- Save and reboot into RUN mode

### Daily operation

- Device runs continuously without internet
- LCD shows status and next bell information
- Emergency input interrupts routine schedule immediately
- Enable/disable control allows temporary suspension when needed

## 15) Test and Commissioning Checklist

Electrical and hardware:

- Common ground continuity confirmed
- No 5V on GPIO pins
- Input fuse and MOV installed
- Decoupling components installed
- I2C pull-up strategy verified (single effective pull-up set)

Functional:

- RTC time retention after power cycle
- SD detection and file read success
- Bell trigger timing verification across day boundaries
- Emergency override trigger and recovery behavior
- Audio fallback behavior when file is absent
- Enable/disable state behavior

Deployment soak test:

- 24-hour continuous operation run
- Multiple restart and brownout simulations
- Schedule integrity validation after repeated resets

## 16) Reliability and Fail-Safe Behavior

Targeted resilience behavior:

- Power failure: Auto boot and schedule resume
- RTC invalid state: Warning + correction flow
- Missing SD: Fault indication + retry policy
- Missing audio file: Fallback alert output
- Runtime hang: Watchdog-assisted self-recovery

## 17) Performance Targets and Lifecycle

Targets consolidated from proposal documents:

- Bell timing accuracy: approximately +/-1 second
- Startup readiness: less than 5 seconds (target)
- Audio trigger latency: less than 200 ms (target)
- Continuous duty cycle: 24/7
- DS3231 drift expectation: very low annual drift

Service life expectations (environment dependent):

- ESP32-S3 board: 5 to 10 years typical field expectation
- DS3231 module: 10+ years
- CR2032 RTC cell: 3 to 5 years replacement cycle
- MicroSD: 2 to 5 years based on media quality and writes

## 18) Deployment Model for Schools and Colleges

Recommended deployment pattern:

- Install controller near existing PA amplifier rack
- Route line-out to amplifier AUX/line input
- Maintain secure service access to enclosure
- Keep schedule management with authorized academic/admin staff
- Maintain spare SD cards, fuse stock, and RTC cells on-site

## 19) Future Scope

- Multi-building synchronized bell operation
- Centralized multi-campus schedule management
- Attendance or institutional ERP integration
- Richer dashboard analytics and event logging
- Structured maintenance diagnostics

## 20) Repository Document Map

Current documentation in this repository includes:

- concept and abstract material
- project proposal and objective details
- circuit and pinout specifications
- feature lists (draft and final)
- component and material lists
- personal profile/readme-style author info
- two PDF references related to materials and time-accuracy context

## 21) Author and Contact

Prepared by: Sakshyam Bastakoti

Public links captured in repository profile document:

- LinkedIn: https://www.linkedin.com/in/sakshyambastakoti/
- GitHub: https://github.com/sakxam-xeetri
- YouTube: https://www.youtube.com/@TechWorldXYZ
- Instagram: https://www.instagram.com/sakxam_console.log

## 22) Status and Next Steps

Current repository status is documentation-focused. Firmware source, web UI source, and production files are expected as next implementation assets.

Recommended immediate next actions:

- finalize one authoritative GPIO map
- publish firmware repository structure
- define configuration schema and sample schedule files
- add commissioning report template and maintenance SOP
- include release and versioning strategy
