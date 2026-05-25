# Architecture Documentation

## Purpose
This directory is reserved for deeper architecture references that complement [SYSTEM_ARCHITECTURE.md](../../SYSTEM_ARCHITECTURE.md). It is intended for diagrams, interface notes, and design decisions as the system becomes more modular.

## Architecture Focus
- The UNO WiFi Rev2 owns sensing and local state logic
- The Python laptop bridge owns message routing and future AI policy logic
- The Uno R3 owns deterministic actuator control for the Braccio arm
- All board-to-board communication goes through the laptop bridge

## Planned Contents
- Detailed subsystem diagrams
- Protocol and interface specifications
- Design decision records
- Reliability and safety architecture notes

## Current Use
- Architecture planning remains lightweight while the prototype is still in early integration
- Keep notes here only when they support a concrete implementation or integration decision

## TODO
- Add the first subsystem diagram or decision record when the architecture stabilizes enough to justify it
