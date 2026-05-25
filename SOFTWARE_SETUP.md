# Software Setup

## Scope
This document covers the software environments that support the current prototype and the next planned integration stages. The repository is not yet a finished software stack, so setup is organized around incremental development rather than a single monolithic install.

## Current Software Areas
- Arduino firmware for Braccio control and safe-state behavior
- Future serial communication between the Arduino and host computer
- Python computer vision and AI tooling for later perception work
- Optional dashboard and analytics components for monitoring and diagnostics

## Environment Strategy
- Keep embedded firmware and host software separate
- Use small, versioned interfaces between components
- Avoid adding dependencies that are not tied to a documented requirement
- Validate each layer independently before connecting them into a larger workflow

## Suggested Development Setup
- Arduino IDE or a compatible Arduino toolchain for firmware work
- Python environment for future computer vision and AI tasks
- Serial test utilities for communication checks
- Documentation and logging workflow for experiment notes

## Current Setup Checklist
- [x] Repository structure and documentation hierarchy defined
- [x] Early Arduino control and safety documentation established
- [ ] Firmware development environment standardized
- [ ] Python environment documented for vision work
- [ ] Serial communication protocol defined
- [ ] Baseline integration test plan expanded as software modules mature

## Future Setup Notes
- The Arduino UNO WiFi Rev2 may be used later for connected or telemetry-oriented experiments
- The Education Shield should reduce wiring friction during sensor integration and test iterations
- A dashboard should be added only after the data path and control path are stable
