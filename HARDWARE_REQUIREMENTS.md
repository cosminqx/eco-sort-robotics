# Hardware Requirements

## Purpose
This document defines the confirmed hardware inventory and the minimum requirements for the current prototype stage. It separates the board responsibilities so the distributed architecture stays explicit.

## Confirmed Core Platform
- Arduino Braccio robotic arm
- 1x Arduino Uno R3 for real-time actuator control
- 1x Arduino UNO WiFi Rev2 for sensors, local logic, and future connected features
- 1x Arduino Education Shield
- 1x large breadboard and 1x mini breadboard
- Additional jumper wire set and USB cable
- 9V battery connector

## Confirmed Inputs and Indicators
- 1x ultrasonic sensor
- 1x phototransistor
- 1x potentiometer with knob
- 2x arcade buttons
- Piezo buzzer
- Additional 5mm LEDs and 10mm LEDs

## Prototyping Components
- Resistors
- Modular construction pieces
- Robotic prototyping parts

## System Role Requirements
- The Uno R3 must remain the real-time actuator controller for Braccio movement
- The UNO WiFi Rev2 must not directly drive servos or bypass the laptop bridge
- The laptop must remain the structured communication path between the two boards
- Future AI and policy logic should live on the laptop, not in the servo control firmware

## Electrical and Power Requirements
- The Braccio servos should not be assumed to run safely from an undersized supply path
- USB power is useful for development and low-risk testing, but it is not a substitute for proper actuator power planning
- Both boards should be powered and validated independently before they are integrated through the serial protocol
- The 9V battery connector may support experiments, but current and runtime limits must be evaluated before relying on it
- Grounding and noise control become more important as sensors and multiple actuators are added

## Mechanical and Safety Requirements
- A stable bench or base for the arm
- Clear arm travel limits during testing
- A known safe state that can be reached quickly during development
- Manual interaction through the arcade buttons and visual feedback through LEDs and buzzer

## Future Expansion Considerations
- The UNO WiFi Rev2 can support future communication experiments and connected diagnostics
- The Education Shield can simplify sensor wiring and prototyping cleanup
- Additional sensing should only be added when there is a documented need

## Documentation References
- [hardware/README.md](hardware/README.md)
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md)
- [TESTING.md](TESTING.md)
