# Arduino Control

## Purpose
This folder is reserved for the embedded control layer that drives the Braccio arm and maintains the current safe-state behavior on the Uno R3.

## Current Scope
- Deterministic servo execution for the Braccio arm
- Emergency STOP enforcement on the actuator side
- Command handling from the Python bridge
- LED and buzzer feedback for state changes and manual overrides

Status (2026-06-08): Uno R3 firmware is operational and tested for the core safe-state and motion behaviours. Continue to keep firmware focused on actuator control and safe-state enforcement.

## Design Notes
- Keep control logic deterministic and easy to reason about
- Treat safety state handling as part of the core firmware, not an optional feature
- Accept only structured commands from Python rather than sensor payloads
- Do not mix perception or AI decisions into the actuator firmware

## Command Contract
- `START` transitions the arm into a ready state
- `STOP` forces the arm into the safe state
- `HOME` moves the arm to a known reference pose
- `MOVE_PICK` and `MOVE_PLACE` are executed only when the robot is running

## Future Work
- Add more structured motion commands once the calibration workflow is stable
- Add explicit command acknowledgements for every action
- Keep the motion library usage narrow and documented

## TODO
- Document pin assignments and firmware architecture when the implementation is added
