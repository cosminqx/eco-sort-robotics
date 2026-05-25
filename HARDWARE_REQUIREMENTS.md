# Hardware Requirements

## Purpose
This document defines the confirmed hardware inventory and the minimum requirements for the current prototype stage. It intentionally separates what is already in use from what is planned for later integration.

## Confirmed Core Platform
- Arduino Braccio robotic arm
- 1x Arduino UNO WiFi Rev2
- 1x Arduino Education Shield
- 1x large breadboard and 1x mini breadboard
- Additional jumper wire set and USB cable
- 9V battery connector

## Confirmed Inputs and Indicators
- 1x ultrasonic sensor, planned for the next implementation stage
- 1x phototransistor
- 1x potentiometer with knob
- 2x arcade buttons
- Piezo buzzer
- Additional 5mm LEDs and 10mm LEDs

## Prototyping Components
- Resistors
- Modular construction pieces
- Robotic prototyping parts

## Electrical and Power Requirements
- The Braccio servos should not be assumed to run safely from an undersized supply path
- USB power is useful for development and low-risk testing, but it is not a substitute for proper actuator power planning
- The 9V battery connector may support experiments, but current and runtime limits must be evaluated before relying on it
- Grounding and noise control become more important as sensors and multiple actuators are added

## Mechanical and Safety Requirements
- A stable bench or base for the arm
- Clear arm travel limits during testing
- A known safe state that can be reached quickly during development
- Manual interaction through the arcade buttons and visual feedback through LEDs and buzzer

## Future Expansion Considerations
- The Arduino UNO WiFi Rev2 can support future communication experiments and connected diagnostics
- The Education Shield can simplify future sensor wiring and prototyping cleanup
- Additional sensing or camera hardware should only be added when there is a documented need

## Documentation References
- [hardware/README.md](hardware/README.md)
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md)
- [TESTING.md](TESTING.md)
