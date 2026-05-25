# Dual-Board Integration Notes

## Date
2026-05-25

## Entry Title
Distributed control path for Rev2, Python bridge, and Uno R3

## Phase Status
- Phase 2: completed
- Phase 3: in progress

## Distributed System Context
- WiFi Rev2 role: sensor input, local state machine, structured message output
- Python bridge role: serial parsing, routing, logging, future AI integration point
- Uno R3 role: deterministic Braccio control, command execution, emergency stop enforcement

## Goals
- Separate sensing and decision logic from real-time actuation
- Keep the laptop as the only board-to-board communication bridge
- Preserve a clear safety boundary around servo control

## Context
- Hardware setup: Arduino UNO WiFi Rev2, Arduino Uno R3, Braccio arm, buttons, LEDs, piezo buzzer, ultrasonic sensor, breadboards
- Software state: R3 emergency-stop system already functional; Rev2 and Python bridge are being integrated
- Power source: bench power and USB during development, with actuator stability checked independently
- Safety state: manual stop and safe-state behavior remains available on the actuator side
- Communication path: WiFi Rev2 -> Python bridge -> Uno R3

## Progress
- Board responsibilities have been assigned by layer instead of by convenience
- The Rev2 is now treated as the sensing and logic node rather than another motor controller
- Python is now the structured relay for messages and future AI or policy logic
- The Uno R3 remains the only board that directly moves the Braccio

## Problems Encountered
- Early prototypes tend to drift toward overlapping responsibilities if the control boundary is not written down
- Direct sensor-to-servo coupling would make debugging and safety validation harder

## Observations
- Separating real-time motion from higher-level logic makes the system easier to reason about
- The laptop bridge gives a visible point for logging and protocol validation
- The architecture is more scalable because AI or sorting logic can be added without rewriting the servo controller

## Solutions
- Keep the protocol line-based and explicit
- Route all board-to-board traffic through Python
- Keep STOP and SAFE behavior on the actuator side

## Validation
- What was checked: board role separation, serial path definition, safety ownership
- What passed: architecture agreement across control, communication, and actuation layers
- What still needs work: exact protocol fields, end-to-end message timing, and integration test coverage

## Next Steps
- Finalize the Rev2 sensor packet format
- Implement the Python relay script
- Add command acknowledgements on the Uno R3
- Record the first full sensor -> Python -> servo motion test

## Ideas or Improvements
- Add command sequence ids for easier debugging
- Keep protocol changes versioned so the bridge can evolve safely
- Use the journal to track every change to the distributed control contract