# Phase 3 Launch: Perception Layer Development

Date: 2026-06-08

Entry Title: Phase 3 Launch: Perception Layer Development

Phase Status
- Phase 2: Completed (safety and control layer validated at prototype level)
- Phase 3: In progress (perception layer deployment and validation)

Distributed System Context
- WiFi Rev2 role: Deployed as the dedicated perception controller. Reads sensors and emits structured sensor/state messages. Ultrasonic sensor physically mounted; software validation pending.
- Python bridge role: Planned host-side router and future intelligence layer. Responsible for parsing, logging, and forwarding commands between boards. Bridge development in progress.
- Uno R3 role: Dedicated Braccio actuator controller. Maintains deterministic servo timing, safe-state enforcement, emergency stop, LEDs, and buzzer feedback. Operational and tested.

Goals
- Document and validate the dual-controller architecture on the bench
- Complete ultrasonic sensor software validation and threshold tuning
- Stabilize the Python serial bridge protocol and capture initial traces

Context
- Hardware setup: Braccio arm mounted on bench, Uno R3 connected to Braccio and operator inputs; UNO WiFi Rev2 mounted with Education Shield and ultrasonic sensor; laptop available for Python bridge development
- Software state: Uno R3 firmware running deterministic control and safe-state logic; Rev2 firmware deployed for sensor sampling and message emission; Python bridge under development
- Power source: USB power for development; dedicated actuator supply under evaluation for force tests
- Safety state: Emergency stop and SAFE state validated on Uno R3. Manual arcade buttons provide hard overrides.
- Communication path: Planned path is Rev2 -> Python bridge -> Uno R3. Boards currently operate independently during early validation.

Progress
- Dual-controller deployment completed on 2026-06-08. Both boards operate independently on the bench.
- Ultrasonic sensor physically mounted to the Rev2 platform; integration wiring complete.

Problems Encountered
- Ultrasonic software validation and noise filtering remain work in progress.

Observations
- Separating perception and motion has simplified bench testing and reduced coupling between servo timing and sensor polling.

Solutions
- Keep STOP/HARD-OVERRIDE handling local to the Uno R3; do not allow higher-level code to bypass actuator safety.

Validation
- What was checked: Uno R3 safe-state behaviour and LED/buzzer indications; Rev2 deployment and basic sensor readouts on the serial monitor
- What passed: Uno R3 basic emergency stop and deterministic motion tested at bench
- What still needs work: Ultrasonic sensor validation, Python bridge end-to-end message traces, and protocol hardening

Next Steps
- Complete ultrasonic software validation: build test harness, capture repeated measurements, and tune filtering/thresholds
- Implement a minimal Python bridge prototype that logs Rev2 messages and forwards STOP/START/HOME commands to Uno R3
- Record first end-to-end protocol trace in the journal and include media assets

Ideas or Improvements
- Add structured protocol versioning and sequence ids before expanding automation
- Keep datasets and capture metadata alongside media when perception data collection begins
