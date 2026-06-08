# Project Roadmap

This roadmap reflects the current prototype stage of Eco Sort Robotics. The first two phases are completed at the bench level, and the distributed communication layer is now in progress.

## Phase 1: Robotic Arm Setup and Testing
Status: completed at the prototype level.

- Braccio arm assembly and breadboard prototyping setup
- Initial servo testing and movement experimentation
- Basic calibration exploration for safe joint motion
- Early validation of the workspace, fixtures, and cable routing

Deliverables completed in this phase:
- A functioning robotic arm test bench
- A repeatable starting point for motion testing
- Notes captured for calibration and hardware observations

## Phase 2: Emergency Stop and Safe State System
Status: completed at the prototype level.

- Controlled stop and safe-state behavior
- Green LED for RUNNING mode
- Red LED for STOPPED or SAFE mode
- Arcade button input for state control
- Piezo buzzer feedback for state changes and alerts

This phase establishes the safety-first operating model for future automation work. Additional logic can build on this state machine without bypassing the known safe state.

## Phase 3: Perception Layer Development (Distributed Control)
Status: in progress. (Milestone reached 2026-06-08)

- Dual-controller deployment completed: Arduino Uno R3 (motion) and UNO WiFi Rev2 (perception) are operating independently on the bench.
- UNO WiFi Rev2: deployed with the Education Shield; ultrasonic sensor mounted but software validation and threshold tuning are still in progress.
- Uno R3: continues to operate the Braccio arm, run deterministic servo sequences, and enforce emergency stop and safe-state behaviours.
- Python bridge and structured protocol design: in active development; serial routing will be the only board-to-board channel.

This phase consolidates the communication and separation boundaries so sensing and decision logic evolve independently from the real-time actuator controller. The immediate goals are sensor validation, protocol stabilization, and a minimal Python bridge demonstration.

## Planned Future Phases

### Phase 4: Ultrasonic Obstacle Detection
- Integrate the ultrasonic sensor into the Rev2 decision layer
- Use distance feedback to prevent unsafe motion near obstacles
- Define clear thresholds and failure handling behavior

### Phase 5: Object Detection AI
- Develop a Python/OpenCV workflow for object-aware perception
- Define a dataset structure and labeling rules
- Evaluate lightweight classification approaches before automation is added

### Phase 6: Automated Sorting
- Link perception results to robotic handling actions
- Add sorting logic for sustainability categories
- Document decision points and failure cases

### Phase 7: Dashboard System
- Add an operator-facing interface for status and diagnostics
- Surface run state, errors, and test notes
- Avoid coupling the UI directly to low-level control logic

### Phase 8: Analytics and Monitoring
- Collect structured logs for experiments and regressions
- Track system behavior over time rather than relying on anecdotal testing
- Use observations to guide redesigns and reliability improvements

## Cross-Phase Engineering Priorities
- Safety before autonomy
- Modular subsystem boundaries
- Reproducible tests and documented observations
- Conservative expansion of hardware and software scope
