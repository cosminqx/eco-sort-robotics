# Eco Sort Robotics

Eco Sort Robotics is an early-stage robotics and sustainability automation prototype built as a distributed system. The current architecture uses an Arduino Uno R3 for deterministic Braccio arm control, an Arduino UNO WiFi Rev2 for sensing and local decision logic, and a laptop running Python as the communication bridge and future AI layer.

## Project Overview
The project is currently focused on safe prototype assembly, repeatable motion control, and clean separation of responsibilities between boards. Phase 1 established the Braccio arm test bench and basic servo experimentation. Phase 2 added a safety-oriented stop system with LED and buzzer feedback so the arm can be placed into a known safe state during development. Phase 3 is now in progress and is centered on the distributed control path.

## Objectives
- Build a professional robotics platform for sustainability-focused sorting experiments
- Keep sensing, decision-making, communication, and actuation isolated in separate layers
- Validate motion, power, and protocol behavior before adding automation
- Document the engineering process clearly enough for portfolio, research, and open-source use

## Current Progress
- Braccio arm assembly and breadboard prototyping are in place
- Initial servo testing and calibration exploration have been completed
- A controlled RUNNING and SAFE state system is implemented with arcade button input
- Green and red LEDs provide immediate state indication
- The piezo buzzer is used for feedback alerts during state changes
- Dual-board integration is underway with the laptop acting as the communication bridge

## Distributed Architecture
- Arduino UNO WiFi Rev2 reads sensors and maintains the local state machine
- Python on the laptop receives Rev2 messages, validates them, and routes commands
- Arduino Uno R3 executes Braccio movements and handles real-time actuator control
- Safety decisions are kept explicit so AI and higher-level logic never bypass the control boundary

## Hardware Stack
- Arduino Braccio robotic arm
- 1x Arduino Uno R3
- 1x Arduino UNO WiFi Rev2
- 1x Arduino Education Shield
- 1x large breadboard and 1x mini breadboard
- Additional jumper wires and USB cable
- 9V battery connector
- 1x ultrasonic sensor, 1x phototransistor, 1x potentiometer with knob, and 2x arcade buttons
- Piezo buzzer, additional 5mm LEDs, additional 10mm LEDs, resistors, and modular prototyping pieces

The UNO WiFi Rev2 is reserved for sensors, state logic, and future connected-system experiments. The Uno R3 remains the real-time actuator controller. The Education Shield helps keep the prototyping setup organized during integration.

## Software Stack
- Arduino firmware for the Uno R3 actuator layer
- Arduino firmware for the UNO WiFi Rev2 sensor and state layer
- Python communication bridge on the laptop
- Future computer vision and AI modules under staged development
- Future dashboard and monitoring tools for diagnostics and observability

See [SOFTWARE_SETUP.md](SOFTWARE_SETUP.md) and [software/README.md](software/README.md) for the planned software structure.

## Roadmap Summary
The project is moving from manual robotics validation toward a modular sensing, communication, and sorting pipeline. The roadmap documents the confirmed prototype phases and the planned integration phases for serial communication, ultrasonic obstacle detection, AI classification, automated sorting, and operator tooling.

See [PROJECT_ROADMAP.md](PROJECT_ROADMAP.md) for the phase-by-phase plan.

## Repository Structure
- [hardware/](hardware/README.md) for wiring, calibration, power, and electronics notes
- [software/](software/README.md) for firmware, communication, perception, and UI work
- [cad/](cad/README.md) for mechanical concepts and redesign notes
- [docs/](docs/README.md) for supporting technical documentation
- [datasets/](datasets/README.md) for dataset planning and management
- [tests/](tests/README.md) for validation notes and future automated checks
- [journal/](journal/README.md) for engineering log entries
- [media/](media/README.md) for demo captures and experiment assets

## Future Goals
- Complete the WiFi Rev2 to Python to Uno R3 communication pipeline
- Add ultrasonic obstacle handling as the next sensing step
- Introduce AI-assisted object classification using Python and OpenCV
- Build a sustainable sorting workflow with clear decision tracing
- Add dashboard and analytics support for monitoring, debugging, and reporting

## Supporting Documentation
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md)
- [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md)
- [TESTING.md](TESTING.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)

## License
This project is licensed under the terms in [LICENSE](LICENSE).
