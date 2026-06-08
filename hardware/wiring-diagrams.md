# Wiring Diagrams

## Purpose
This file is the place for authoritative wiring references once the prototype connections are finalized. Until the pin map is stable, the goal is to preserve the reasoning behind each connection rather than pretend the wiring is finished.

## Current Wiring Focus
- Braccio arm control connections
- Arcade button inputs for safe-state control
- LED outputs for RUNNING and SAFE status
- Piezo buzzer output for feedback
- Breadboard-based integration of the phototransistor, potentiometer, and ultrasonic sensor planning

## Controller and Board Notes
- The Arduino UNO WiFi Rev2 is reserved for future communication-oriented work
- The Arduino Education Shield should simplify prototyping and sensor routing during later integration

Note (2026-06-08): The current bench layout uses separate controllers for motion and perception. When finalizing wiring diagrams, include explicit pin maps for the Rev2 sensor mounting and the Uno R3 Braccio connections, and note that board-to-board communication will use the laptop bridge as the only router.

## Validation Checklist
- Confirm each wire before power-up
- Check that all grounds are consistent across the bench setup
- Verify that no servo line is swapped with an indicator or input line
- Record the wiring revision alongside the test notes

## Template
- Diagram version:
- Controller pin assignments:
- Power rails:
- Grounding notes:
- Signal directions:
- Validation checklist:
- Revision notes:

## TODO
- Add finalized pin maps when the current prototype wiring stops changing frequently
