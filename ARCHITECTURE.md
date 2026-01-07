# System Architecture

## High-Level Architecture
The system follows a modular, service-oriented design suitable for IoT 

[ Battery Power ]
|
[ Raspberry Pi Zero 2 W ]
|
[USB Serial]
|
[ Pico-Based HMI ]

## Functional Layers

### Compute Layer
- Embedded Linux operating system
- Security monitoring and data collection services
- Logging and analysis components

### Interface Layer
- Physical display and controls
- Read-only visualization of system state
- No direct access to core services

### Power Layer
- Independent power source
- Enables mobility and fault tolerance

## Security Considerations
- Headless operation reduces attack surface
- Limited exposed services
- Physical interface separated from sensitive processes

## Design Goals
- Reliability over convenience
- Observability over complexity
- Security-first defaults