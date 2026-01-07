# Threat Model – Headless IoT Security Monitoring Node

## Overview
This document outlines a basic threat model for the headless IoT security monitoring node. The goal is to identify realistic risks, attack surfaces, and defensive considerations aligned with CySA+ and Blue Team principles.

## System Description
The system consists of:
- A headless Raspberry Pi Zero 2 W running Linux
- A detachable Raspberry Pi Pico-based HMI over USB serial
- External power via battery pack
- Wireless monitoring interfaces

The device is designed to operate unattended in constrained environments.

## Assets
Key assets to protect include:
- System integrity and availability
- Collected telemetry and logs
- Configuration files and credentials
- Physical device access

## Threat Actors
Potential threat actors include:
- Unauthorized local users with physical access
- Nearby wireless attackers
- Network-based attackers attempting lateral movement
- Accidental misconfiguration or misuse

## Attack Surfaces
Identified attack surfaces:
- Wireless interfaces (Wi-Fi monitoring adapters)
- USB interfaces (data and power)
- Remote management services (SSH, web UI)
- Physical access to removable storage

## Threats
Potential threats include:
- Unauthorized access to the device
- Data exfiltration or log tampering
- Denial of service through resource exhaustion
- Physical theft or device modification

## Mitigations
Current and planned mitigations:
- Headless operation with minimal exposed services
- Strong authentication for remote access
- Separation of interface and compute layers
- Regular review of logs and system behavior
- Physical access controls when deployed

## Future Improvements
- Disk encryption for sensitive data
- Improved logging and alerting
- Network segmentation for deployments
- Automated integrity checks

## Disclaimer
This threat model is for educational and defensive security learning purposes only.