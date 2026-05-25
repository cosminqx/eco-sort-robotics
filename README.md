# Eco Sort Robotics

Eco Sort Robotics is an early-stage robotics and AI-assisted sustainability sorting prototype built around the Arduino Braccio arm, Arduino UNO WiFi Rev2, and a small set of sensors and prototyping components. The repository is organized as an engineering notebook, documentation hub, and future software workspace for a modular sorting system that will gradually move from manual control to autonomous, AI-assisted object handling.

## Project Overview
The current focus is safe prototype assembly, repeatable motion control, and controlled-state operation. Phase 1 established the Braccio arm test bench and basic servo experimentation. Phase 2 added a safety-oriented stop system with LED and buzzer feedback so the arm can be placed into a known safe state during development.

## Objectives
- Build a professional robotics platform for sustainability-focused sorting experiments
- Keep the system modular so hardware, firmware, perception, and UI work can evolve independently
- Validate motion and power behavior before expanding into automation
- Document the engineering process clearly enough for portfolio, research, and open-source use

## Current Progress
- Braccio arm assembly and breadboard prototyping are in place
- Initial servo testing and calibration exploration have been completed
- A controlled RUNNING and SAFE state system is implemented with arcade button input
- Green and red LEDs provide immediate state indication
- The piezo buzzer is used for feedback alerts during state changes

## Hardware Stack
- Arduino Braccio robotic arm
- 1x Arduino UNO WiFi Rev2
- 1x Arduino Education Shield
- 1x large breadboard and 1x mini breadboard
- Additional jumper wires and USB cable
- 9V battery connector
- 1x ultrasonic sensor, 1x phototransistor, 1x potentiometer with knob, and 2x arcade buttons
- Piezo buzzer, additional 5mm LEDs, additional 10mm LEDs, resistors, and modular prototyping pieces

The Arduino UNO WiFi Rev2 is reserved for future communication and connected-system experiments. The Education Shield is useful for simplifying sensor and prototyping integration during early-stage testing.

## Software Stack
- Arduino firmware for state control and motion experimentation
- Serial communication planning for future host integration
- Python computer vision and AI modules under staged development
- Future dashboard and monitoring tools for diagnostics and observability

See [SOFTWARE_SETUP.md](SOFTWARE_SETUP.md) and [software/README.md](software/README.md) for the planned software structure.

## Roadmap Summary
The project is moving from manual robotics validation toward a modular sensing, perception, and sorting pipeline. The roadmap documents the confirmed prototype phases and the planned integration phases for obstacle detection, AI classification, serial communication, and operator tooling.

See [PROJECT_ROADMAP.md](PROJECT_ROADMAP.md) for the phase-by-phase plan.

## Repository Structure
- [hardware/](hardware/README.md) for wiring, calibration, power, and electronics notes
- [software/](software/README.md) for firmware, vision, communication, and UI work
- [cad/](cad/README.md) for mechanical concepts and redesign notes
- [docs/](docs/README.md) for supporting technical documentation
- [datasets/](datasets/README.md) for dataset planning and management
- [tests/](tests/README.md) for validation notes and future automated checks
- [journal/](journal/README.md) for engineering log entries
- [media/](media/README.md) for demo captures and experiment assets

## Future Goals
- Add ultrasonic obstacle detection as the next sensing stage
- Introduce AI-assisted object classification using Python and OpenCV
- Connect Arduino control to host software through a serial protocol
- Build a sustainable sorting workflow with clear decision tracing
- Add dashboard and analytics support for monitoring, debugging, and reporting

## Supporting Documentation
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md)
- [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md)
- [TESTING.md](TESTING.md)
- [CONTRIBUTING.md](CONTRIBUTING.md)

## License
This project is licensed under the terms in [LICENSE](LICENSE).
