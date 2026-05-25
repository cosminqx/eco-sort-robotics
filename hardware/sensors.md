# Sensors

## Purpose
This document tracks the current and planned sensing elements for the prototype. The sensor set is intentionally small so the team can validate safety and control behavior before expanding perception.

## Phototransistor
- Measurement purpose: light response and experimental sensing
- Electrical interface: simple analog-style prototype use through the breadboard setup
- Integration notes: useful for small signal experiments and learning about threshold behavior
- Risks or limitations: ambient light and placement can make readings unstable if the setup is not controlled

## Push Buttons
- Measurement purpose: operator control and state changes
- Electrical interface: digital input through the breadboard
- Integration notes: the arcade buttons are part of the safety-oriented control design
- Risks or limitations: bounce and wiring issues should be considered during manual testing

## LEDs
- Measurement purpose: clear machine-state indication
- Electrical interface: digital output with resistors
- Integration notes: green indicates RUNNING, red indicates SAFE or STOPPED
- Risks or limitations: LEDs are status indicators only and do not replace control logic

## Piezo Buzzer
- Measurement purpose: audio feedback for operator awareness
- Electrical interface: digital output or tone-style feedback, depending on the control implementation
- Integration notes: useful for alerts and state transitions during bench testing
- Risks or limitations: audio cues should stay simple and unambiguous

## Ultrasonic Sensor
- Measurement purpose: distance and obstacle detection
- Electrical interface: planned for the next implementation stage
- Integration notes: should be added once safe-state behavior is stable and thresholds can be tested properly
- Risks or limitations: false readings, alignment sensitivity, and threshold tuning will need careful validation

## TODO
- Add measured values, pin assignments, and placement notes once each sensor is wired and tested
