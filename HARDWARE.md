# Hardware Architecture

## Overview
This document describes the hardware components and design decisions behind the headless IoT security monitoring node. The system was intentionally designed to be modular, power-aware, and resilient.

## Core Components

### Raspberry Pi Zero 2 W
**Role:** Primary compute node  
- Runs headless Linux
- Hosts monitoring and logging services
- Operates without a directly attached display
- Optimized for low power consumption and unattended operation

**Rationale:**
Chosen for its balance of performance, power efficiency, and Linux compatibility in constrained IoT environments.

---

### Raspberry Pi Pico + Display (HMI)
**Role:** Detachable human–machine interface  
- Displays system status and telemetry
- Provides physical input via buttons
- Communicates with the Pi over USB serial

**Rationale:**
Separating the interface from the core system improves reliability. The monitoring node continues to function even if the interface is disconnected or replaced.

---

### Power System
**Role:** External battery pack  
- Provides portable power
- Enables long-running deployments
- Simulates real-world field operation

**Rationale:**
Power independence is critical for realistic IoT security deployments.

---

## Design Principles
- Separation of concerns (compute, interface, power)
- USB-based communication over GPIO dependency
- Minimal exposed attack surface
- Replaceable and upgrade-friendly components

## Future Hardware Enhancements
- External Wi-Fi adapters for improved RF performance
- Additional sensors (environmental or positional)
- Secure storage enhancements