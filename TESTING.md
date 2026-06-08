# Testing Strategy

## Purpose
Testing is treated as an engineering control, not an afterthought. The project is still in early prototyping, so testing focuses on safe motion, clear state behavior, and protocol reliability rather than formal automation alone.

## Current Validation Areas

### Servo Testing
- Confirm that the Braccio joints move only within known safe limits
- Observe startup behavior, smoothness, and repeatability
- Record any instability, jitter, or unexpected motion during bench testing

### Emergency Stop Validation
- Verify that the system can enter the SAFE state reliably
- Confirm that manual state control works from the arcade button input
- Ensure the robot remains in a controlled state after stop requests
- Verify that the Uno R3 stop override works even if the laptop bridge is disconnected

### LED State Testing
- Green LED indicates RUNNING mode
- Red LED indicates STOPPED or SAFE mode
- Check that state changes are visible from the operator position

### Piezo Feedback Testing
- Confirm audio alerts occur at the intended state transitions
- Use buzzer feedback as a quick operator signal during hands-on testing

### Protocol Testing
- Confirm that Rev2 messages are newline terminated and parse cleanly on the laptop
- Confirm that Python forwards only valid structured commands to the Uno R3
- Confirm that the Uno R3 returns ACK or ERR messages for every command

## Future Testing Areas
- Ultrasonic sensor response and threshold validation
- Sensor noise and repeatability checks
- Serial communication reliability tests across longer runs
- Object detection and classification accuracy checks
- End-to-end sorting workflow validation

Current priorities (next test cycles):
- Complete ultrasonic sensor validation on the UNO WiFi Rev2 (mounting done; software validation pending)
- Record first live protocol traces through the Python bridge once the bridge is functional
- Verify emergency stop behaviour under partial integration (e.g., Python disconnected)

## Test Evidence
For each test cycle, record:
- Date and test objective
- Hardware configuration and power source
- Observed behavior and state transitions
- Protocol messages exchanged between nodes
- Failures, anomalies, and suspected causes
- Follow-up actions or design changes

## Status
Automated test coverage is expected to grow as software modules are implemented. For now, disciplined manual validation and engineering notes are the main source of truth.
