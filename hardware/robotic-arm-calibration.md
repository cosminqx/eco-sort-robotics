# Robotic Arm Calibration

## Purpose
This document captures the calibration thinking for the Braccio arm during early prototyping. The goal is safe, repeatable movement rather than aggressive range extension.

## Safe Servo Movement Practices
- Move one joint or one motion variable at a time when validating the arm
- Start with conservative positions and slow transitions
- Keep hands and cables clear of the motion envelope during testing
- Stop immediately if motion becomes erratic or load-dependent behavior appears

## Calibration Concepts
- Joint offsets should be recorded relative to a known reference pose
- A calibration pose should be simple, reproducible, and easy to verify visually
- Any change in mounting, load, or cable routing can affect the calibration result

## Movement Limitations
- The arm is being used as a prototype platform, so safe operating limits matter more than maximum range
- Repeatability should be judged against the current setup, not against idealized vendor specifications
- Mechanical slack, power quality, and servo load can all reduce consistency

## Future Calibration Procedure
- Define a standard reference pose for startup checks
- Record joint offsets and observed drift after each major hardware change
- Validate the arm after wiring or power changes before any higher-level automation is added
- Add a short calibration checklist once the control software becomes more structured

## Template
- Calibration date:
- Operator:
- Reference pose:
- Joint offsets:
- Observed limitations:
- Validation method:
- Result summary:
- Follow-up actions:
