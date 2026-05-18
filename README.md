# Eco Sort Robotics

AI-assisted sustainability sorting robotics project combining computer vision, sensing, and robotic manipulation with the Arduino TinkerKit Braccio platform.

## Project Overview
This repository hosts the engineering artifacts, software modules, hardware documentation, and design files for an intelligent sorting system that identifies and separates materials (e.g., plastic, paper, metal) through automation.

## Motivation
Waste sorting quality and consistency are difficult to maintain in manual workflows. This project explores how accessible robotics and AI can support reliable, repeatable, and educational sustainability-focused automation.

## Sustainability Impact
- Encourages improved material separation at source
- Supports education in circular economy and responsible engineering
- Creates a reusable platform for local sustainability experiments

## Engineering Goals
- Build a modular, maintainable robotics platform
- Integrate computer vision and sensor fusion for classification support
- Design safe, repeatable pick-and-place behavior
- Document decisions, tests, and iterations with engineering rigor

## System Architecture Overview
A high-level architecture summary is maintained in [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md), with supporting placeholders under [`/docs`](docs/README.md).

## Hardware Stack
- Arduino TinkerKit Braccio robotic arm
- Vision capture hardware (camera module)
- Material detection sensors (to be finalized and documented)
- Power and safety subsystems

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) and [`/hardware`](hardware/README.md).

## Software Stack
- Arduino firmware/control layer
- Python-based vision and AI tooling
- Serial communication bridge
- Optional dashboard/web interface

See [SOFTWARE_SETUP.md](SOFTWARE_SETUP.md) and [`/software`](software/README.md).

## AI / Computer Vision Overview
The AI pipeline placeholders and model-development notes are tracked in:
- [`/software/python-computer-vision`](software/python-computer-vision/README.md)
- [`/software/ai-object-detection`](software/ai-object-detection/README.md)
- [`/datasets`](datasets/README.md)

## Robotics Overview
Robotics control, calibration, wiring, and power considerations are organized in:
- [`/hardware`](hardware/README.md)
- [`/software/arduino-control`](software/arduino-control/README.md)
- [`/cad`](cad/README.md)

## Future Plans
See [PROJECT_ROADMAP.md](PROJECT_ROADMAP.md) for staged milestones and technical growth paths.

## Development Roadmap
Roadmap phases, deliverables, and verification checkpoints are documented in [PROJECT_ROADMAP.md](PROJECT_ROADMAP.md).

## Media / Demo
Use [`/media`](media/README.md) for demo videos, photos, and validated experiment captures.

## Contribution
Contribution workflow, quality expectations, and review process are available in [CONTRIBUTING.md](CONTRIBUTING.md).

## License
This project is licensed under the terms in [LICENSE](LICENSE).
