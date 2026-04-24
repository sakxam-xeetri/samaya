AUTOMATIC SCHOOL / COLLEGE BELL SYSTEM FEATURES

[CORE SYSTEM]
- Fully Offline Operation (No Internet Required)
- ESP32-S3 Based Main Controller
- High Accuracy Timekeeping using DS3231 RTC
- Automatic Bell Ringing at Exact Scheduled Time
- Continuous 24/7 Operation Capability
- Auto Day Switching at Midnight

[SCHEDULING & TIME MANAGEMENT]
- 7-Day Programmable Schedule (Different for Each Day)
- Unlimited Schedules per Day
- Multiple Bells per Day (24-Hour Support)
- Winter / Summer Preset Timetable
- Special Day Preset Override
- Priority Logic: Emergency > Special Day > Seasonal > Weekly
- Manual "Next Bell" Trigger
- Missed Bell Handling Logic (Skip / Continue)
- Automatic Time Sync via Local Web Interface
- RTC Battery Backup (Up to 5 Years)
- RTC Invalid Time Detection

[AUDIO SYSTEM]
- MP3 / WAV Audio Playback Support
- MicroSD Card Based Audio Storage
- Preloaded Bell and Announcement Sounds
- Male / Female Voice Announcement Support
- Clean Audio Output using PCM5102A DAC
- 3.5mm Line-Level Audio Output
- Compatible with External PA Amplifier
- Audio Fallback (Default Beep if File Missing)
- Audio Mute When Idle
- Low Noise / Distortion-Free Output

[EMERGENCY & OVERRIDE SYSTEM]
- Dedicated Emergency Button
- Long-Press Safety Activation
- Immediate Schedule Interruption
- Emergency Siren Playback
- Emergency Announcement Playback
- Emergency LED Indicator
- Highest Priority Execution

[CONFIGURATION & INTERFACE]
- Offline Hotspot Configuration Mode
- Mobile-Friendly Web Dashboard
- No Internet Required for Configuration
- Live Schedule Editing
- Save Configuration to SD Card
- Auto Reload After Configuration Update

[DISPLAY & USER FEEDBACK]
- 16x2 LCD Display
- Time Display
- Next Bell Display
- System Status Display (RUN / CONFIG / EMERGENCY / DISABLED)
- Error Messages (SD Card, RTC, System Fault)
- Rotating Information Screens

[USER CONTROLS]
- Next Bell Button
- Emergency Button (Long Press Protected)
- Config Mode Button (Hotspot Activation)
- System Enable / Disable Button
- Button Debounce Logic
- Accidental Press Protection

[INDICATORS]
- Power LED
- Status LED
- Emergency LED
- Enable LED (Indicates System Active / Disabled State)

[POWER & ELECTRICAL SYSTEM]
- Industrial AC-DC Power Module (HLK-PM5)
- Isolated Power Supply Design
- 5V Main Rail + Regulated 3.3V
- Bulk Capacitor for Load Stability
- Decoupling Capacitors on All Modules
- Fuse Protection (Overcurrent Safety)
- Surge Protection (MOV)
- Stable Operation Under Load Variations

[RELIABILITY & FAIL-SAFE FEATURES]
- Auto Restart After Power Failure
- Resume Schedule After Reboot
- Watchdog Timer for System Recovery
- SD Card Health Check on Startup
- SD Card Removal Detection
- Audio File Validation Before Playback
- RTC Failure Detection and Warning
- Safe System Recovery Mode

[DATA & STORAGE]
- SD Card Based Configuration Storage
- JSON-Based Scheduling System
- Audio File Mapping System
- Config Backup Capability
- Data Integrity Checking

[FIRMWARE & UPDATES]
- OTA Firmware Update Support
- Dual Partition Safe Update System
- Rollback Protection (Update Failure Recovery)
- Version Control Support

[SYSTEM LOGIC]
- Real-Time Monitoring Loop
- Priority-Based Task Execution
- Interrupt-Driven Emergency Handling
- State Machine Architecture
- Low Latency Bell Triggering

[HARDWARE & PCB DESIGN]
- Proper Grounding Layout
- Decoupling Near Every Module
- Stable Power Routing Design
- Audio Signal Isolation
- Screw Terminal Connectivity
- Enclosure Mount Ready Design
- Thermal Safe Operation

[EDGE CASE HANDLING]

Power Issues:
- Safe Restart After Power Loss
- Voltage Dip Protection via Capacitors

Time Issues:
- RTC Battery Failure Detection
- Manual Time Reset Option

Storage Issues:
- SD Card Missing Detection
- Corrupt File Handling with Fallback Audio

User Errors:
- Schedule Correction via UI
- Emergency Button Long Press Protection

System Errors:
- Auto Reset Using Watchdog
- Audio Failure Skip and Continue Logic

[FINAL SYSTEM CAPABILITIES]
- Fully Autonomous Operation
- No Human Intervention Required
- High Accuracy and Reliability
- Long-Term Deployment Ready
- Fault-Tolerant Design
- Clean Professional Audio Output
- Easy Configuration Interface
- Production-Level Embedded System