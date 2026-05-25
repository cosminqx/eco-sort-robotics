# Electronics Notes

## Purpose
This file is the working notebook for practical hardware observations, troubleshooting, and small design changes during prototype development.

## Practical Lessons Learned
- Breadboard connections are useful for quick iteration, but they need to be checked carefully before every motion test
- Servo behavior becomes easier to reason about when only one change is introduced at a time
- Clear state indication with LEDs and buzzer feedback reduces uncertainty during hands-on debugging

## Servo Instability Notes
- Servo motion should be treated as part of a controlled test, not as a continuous stress test
- Small changes in load, cable routing, or power quality can alter movement behavior
- Any unexpected jitter or weak movement should be recorded with the exact test setup

## Breadboard Reliability Observations
- Breadboards are appropriate for prototype wiring, but they are not a final mechanical solution
- Jumper lead strain and loose connections are common failure points during repeated testing
- Connections should be reviewed after any physical repositioning of the arm or components

## Power Considerations
- The arm and indicators should be evaluated with power limitations in mind, especially when several components are active together
- USB power is convenient for logic testing, but it should not be assumed to handle all actuator demands indefinitely
- The 9V battery connector is available for experiments, but it must be validated before being treated as a practical operating source

## Debugging Notes
- Always document what changed before a fault appeared
- Note whether the issue is electrical, mechanical, or software-controlled
- Keep a short log of any repeatable symptom, the test conditions, and the first likely cause

## TODO
- Add wiring revisions once the pin map is finalized
- Record specific fault cases and recovery steps as they occur
