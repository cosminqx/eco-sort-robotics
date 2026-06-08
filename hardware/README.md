# Hardware Documentation

This folder collects practical notes for the current prototype hardware stack. It covers what has been assembled, what has been observed during testing, and what should be documented before the next integration step.

## Purpose
- Capture wiring and hardware decisions in one place
- Record calibration and testing observations for the Braccio arm
- Keep power and safety notes close to the prototype work
- Separate confirmed hardware from future expansion ideas

## Current Hardware Focus
- Arduino Braccio robotic arm
- Arduino UNO WiFi Rev2 and Arduino Education Shield for future prototyping paths
- Breadboard-based integration of buttons, LEDs, buzzer, potentiometer, phototransistor, and ultrasonic sensor planning

Note (2026-06-08): The project has adopted a dual-controller architecture separating motion (Uno R3) and perception (UNO WiFi Rev2). The ultrasonic sensor has been mounted on the Rev2 platform; software-level validation remains a priority.

## Files
- [electronics-notes.md](electronics-notes.md)
- [wiring-diagrams.md](wiring-diagrams.md)
- [robotic-arm-calibration.md](robotic-arm-calibration.md)
- [power-considerations.md](power-considerations.md)
- [sensors.md](sensors.md)

## TODO
- Add pin maps and wiring references as they are finalized
- Record calibration values and safe motion limits
- Document any repeatable power or grounding issues discovered during testing
