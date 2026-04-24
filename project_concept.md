# **Project Proposal**

# **SAMAYA**

### *Smart Automatic Management and Announcement System for Academic Yards*

**A Production-Level Automatic School/College Bell and Announcement System**

---

# **Abstract**

Educational institutions across Kathmandu Valley continue to rely largely on manual bell ringing or basic timer-based bell systems for class transitions, examinations, breaks, and emergency alerts. These conventional approaches often lead to human error, schedule inconsistency, limited flexibility, and operational inefficiencies. With growing institutional demands and increasing interest in smart-campus infrastructure, there is a clear need for a reliable, accurate, and low-maintenance automated bell and announcement system.

This project proposes **SAMAYA**, a production-level embedded automation system designed for schools and colleges. The system integrates high-accuracy scheduling, audio announcements, emergency alerting, offline configuration, and industrial-grade reliability in a single platform. Based on an ESP32-S3 controller and DS3231 real-time clock, the system supports weekly schedules, seasonal routines, special-day presets, amplifier-integrated audio playback, and offline hotspot-based configuration.

The project aims to provide a scalable and commercially deployable solution suitable for institutions in Kathmandu Valley and across Nepal.

---

# **1. Introduction**

Time regulation is fundamental to educational operations. In schools and colleges, bells coordinate class periods, assemblies, examinations, and safety alerts. However, many institutions still depend on manual operation or outdated timer systems that lack flexibility and precision.

Kathmandu Valley, comprising Kathmandu, Lalitpur, and Bhaktapur, hosts thousands of educational institutions, many operating multiple shifts and varying academic routines. According to education statistics and municipal records, the valley contains a high density of schools and colleges, making standardized bell automation increasingly relevant.

Current challenges include:

* Manual bell ringing dependency
* Schedule errors and delayed transitions
* Difficulty managing seasonal or special routines
* No integrated emergency announcement mechanism
* Limited or no digital configuration

These limitations motivate the need for a modern automated solution.

SAMAYA is proposed as a smart embedded system addressing these challenges while remaining practical, affordable, and deployable in Nepalese institutions.

---

# **2. Problem Statement**

Many educational institutions continue using conventional bell systems that suffer from:

## Operational Problems

* Human error in manual ringing
* Bell delays or missed periods
* Inconsistent scheduling
* Staff dependency for routine operation

## Technical Limitations

* Conventional timers cannot handle:

  * Multiple daily schedules
  * Seasonal routines
  * Exam schedules
  * Emergency alerts
* Poor audio integration for announcements

## Safety Concerns

Most systems lack:

* Fire alarms
* Earthquake sirens
* Campus-wide emergency announcements

## Maintenance Issues

* Legacy systems often require regular intervention
* Limited fault tolerance
* No centralized configuration

### Core Problem:

There is no low-cost, locally deployable, production-grade automatic bell system specifically designed for educational institutions in Nepal.

---

# **3. Objectives**

## General Objective

To design and develop a production-level automatic school bell and announcement system for educational institutions.

## Specific Objectives

* Automate academic bell scheduling
* Provide accurate RTC-based timing
* Support weekly and seasonal schedules
* Enable emergency alarm functionality
* Provide offline mobile/web configuration
* Interface with existing school amplifier systems
* Develop a low-maintenance, scalable embedded product

---

# **4. Need and Significance of the Project**

## Why Kathmandu Valley Needs This

Educational institutions commonly operate:

* Morning shifts
* Day shifts
* Seasonal timing adjustments
* Event-specific schedules

Manual management becomes inefficient.

## Significance

SAMAYA can provide:

* Academic punctuality
* Reduced manpower dependency
* Improved emergency readiness
* Affordable institutional automation
* Foundation for smart-campus systems

---

# **5. Literature Review**

## Existing Bell Systems

Most available systems fall into:

### Manual Bell Systems

* Human operated
* Low cost
* Error prone
* No automation

---

## Timer-Based Bell Controllers

Basic programmable timers offer:

* Fixed bell schedules
* Simple relay outputs

Limitations:

* No dynamic schedules
* No announcements
* Limited flexibility

---

## Commercial Automatic Bell Systems

Available imported products offer:

* Digital scheduling
* Audio playback
* Higher reliability

Limitations:

* Expensive
* Limited localization
* Often internet dependent
* Difficult maintenance

---

## Embedded Automation Research

Recent embedded automation projects using:

* Microcontrollers
* RTC scheduling
* IoT interfaces
* Audio integration

show feasibility of:

* offline scheduling
* smart campus devices
* low-cost automation systems

---

## Research Gap

Most existing solutions:

* Are too simple for production use
* Lack emergency integration
* Are expensive imports
* Are not tailored for Nepalese institutions

SAMAYA addresses this gap.

---

# **6. Proposed System**

## Hardware Architecture

Main components:

* ESP32-S3 Microcontroller
* DS3231 RTC
* PCM5102A DAC
* MicroSD Audio Storage
* 16x2 LCD Interface
* Push Button Controls
* Hi-Link HLK-PM5 Power Module
* External Amplifier Audio Output

---

## Key Features

* Fully offline operation
* 7-day programmable schedule
* Winter/summer presets
* Special day routines
* Emergency siren
* Announcement playback
* Hotspot configuration
* OTA firmware update
* RTC backup (5 years)
* Surge and fuse protection

---

# **7. Methodology**

## Phase 1 — Requirement Analysis

* Study school operational bell requirements
* Collect sample schedules from institutions
* Identify amplifier integration needs

---

## Phase 2 — System Design

Design:

* Hardware architecture
* Scheduling logic
* Audio subsystem
* Protection circuitry

---

## Phase 3 — Hardware Development

Develop:

* Circuit schematic
* Prototype PCB
* Power and protection stage
* Embedded hardware integration

---

## Phase 4 — Firmware Development

Implement:

* RTC scheduler engine
* Audio playback engine
* Web configuration dashboard
* Emergency interrupt handling
* Fail-safe logic

---

## Phase 5 — Testing

Perform:

* Timing accuracy testing
* Audio output testing
* Power interruption recovery test
* Long-run reliability testing

---

## Phase 6 — Deployment Validation

Pilot installation in school environment.

Evaluate:

* Accuracy
* Reliability
* User feedback

---

# **8. System Workflow**

```text
Power On
↓
Initialize Hardware
↓
Load Schedule
↓
RTC Time Check
↓
Monitor Bell Events
↓
Trigger Audio
↓
Return to Schedule Loop
```

Emergency override has highest priority.

---

# **9. Expected Outcomes**

* Fully automated institutional bell system
* Reduced manual workload
* Reliable timing automation
* Enhanced emergency preparedness
* Commercially viable product prototype

---

# **10. Innovation of the Project**

Novel aspects:

* Offline smart scheduling
* Seasonal preset logic
* Embedded announcement platform
* Production-grade design focus
* Designed specifically for Nepalese institutions

---

# **11. Feasibility**

## Technical Feasibility

High:

* Mature hardware components
* Proven embedded technologies

## Economic Feasibility

Affordable compared to imported systems.

## Operational Feasibility

Simple deployment using existing amplifiers.

---

# **12. Future Scope**

Potential expansion:

* Multi-building synchronized bell systems
* Central campus management
* Attendance integration
* Smart school automation ecosystem

---

# **13. Conclusion**

SAMAYA proposes a practical, reliable and scalable automatic bell and announcement system addressing real educational operational challenges in Kathmandu Valley. Beyond being an academic project, it has potential to become a deployable commercial product supporting digital transformation in Nepalese education.

---

## Proposed Project Title

**SAMAYA**
*Smart Automatic Management and Announcement System for Academic Yards*

---


