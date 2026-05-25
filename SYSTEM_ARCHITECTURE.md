# System Architecture

## Purpose
This document describes the current and planned technical boundaries of Eco Sort Robotics. The architecture is being built incrementally, starting with safe embedded control and moving toward host-assisted perception and sorting.

## Current Architecture Snapshot
The system is organized around a stable Arduino hardware layer, a small set of direct sensors and indicators, and a future software layer for vision and coordination. At this stage, the architecture is still prototype-focused and should be read as a staged integration plan rather than a finished product.

## Arduino Hardware Layer
- Arduino Braccio robotic arm provides the motion platform
- Arduino UNO WiFi Rev2 is available for future communication and connected-system experiments
- Arduino Education Shield supports easier prototyping and sensor integration
- Breadboards, buttons, LEDs, buzzer, potentiometer, and wiring provide the current bench setup
- Safety logic currently centers on known RUNNING and SAFE states

## Sensor Layer
- Phototransistor for basic light-response or experimental sensing work
- Arcade buttons for state control and manual interaction
- LEDs for immediate machine-state feedback
- Piezo buzzer for audio alerts and operator feedback
- Ultrasonic sensor is planned for the next implementation stage as a distance and obstacle-checking input

## AI and Software Layer
- Arduino firmware handles local state control and motion experimentation
- Python/OpenCV will support future perception and object-aware behavior
- AI object classification is planned, not yet part of the active control loop
- Dashboard and analytics tools will be added later for supervision and debugging

## Communication Flow
1. Operator input changes the current machine state
2. Arduino firmware updates LEDs, buzzer behavior, and safe-state handling
3. Future sensors and host software will add higher-level interpretation
4. Serial communication will eventually bridge Arduino control and computer vision outputs
5. Logged observations will inform calibration, safety checks, and redesign decisions

## Future Modular Architecture
The next architecture step is a layered system with narrow interfaces between control, sensing, perception, and user interface components. That structure will allow the project to scale without turning the Arduino sketch into a monolithic controller.

Planned modules include:
- Motion and state control
- Proximity and safety sensing
- Vision and classification
- Serial communication bridge
- Operator dashboard and metrics

## Interface Contracts
- Arduino state machine messages
- Sensor readout formats
- Future serial command and telemetry schema
- Safety override and stop semantics

## Architecture Decisions Log
- Keep safety logic local to the embedded control layer
- Treat AI as a future decision-support layer, not a substitute for safety checks
- Use the UNO WiFi Rev2 for future integration paths instead of adding unnecessary hardware now
- Prefer simple, observable interfaces over hidden automation
