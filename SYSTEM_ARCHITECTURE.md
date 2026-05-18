# System Architecture

## Purpose
Define the technical architecture for the AI-assisted sorting robotic system and keep subsystem boundaries explicit.

## High-Level Subsystems
- Perception (camera + preprocessing + model inference)
- Decision Layer (classification confidence, sort target selection)
- Motion Control (trajectory selection, grasp/release commands)
- Hardware Interface (serial protocol, sensor ingestion)
- Observability (logs, experiment metadata, media)

## Data and Control Flow (Placeholder)
1. Capture sensor/camera input
2. Run preprocessing and inference
3. Select target bin and robotic action
4. Execute movement command sequence
5. Record outcomes and telemetry

## Interface Contracts (Placeholder)
- Host ↔ Arduino message format
- Sensor data schema
- Model input/output schema
- Safety and emergency-stop behavior

## Architecture Decisions Log (Placeholder)
Use this section to record major decisions, alternatives considered, and trade-offs.
