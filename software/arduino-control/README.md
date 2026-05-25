# Arduino Control

## Purpose
This folder is reserved for the embedded control layer that drives the Braccio arm and maintains the current safe-state behavior.

## Current Scope
- State control for RUNNING and SAFE modes
- LED and buzzer feedback handling
- Button-driven operator interaction
- Early motion experiments and control primitives for the Braccio arm

## Design Notes
- Keep control logic deterministic and easy to reason about
- Treat safety state handling as part of the core firmware, not an optional feature
- Avoid mixing future perception logic into the embedded control path

## Future Work
- Add more structured motion commands once the calibration workflow is stable
- Introduce a small command interface for host-controlled actions
- Prepare for serial integration without hard-coding host assumptions

## TODO
- Document pin assignments and firmware architecture when the implementation is added
