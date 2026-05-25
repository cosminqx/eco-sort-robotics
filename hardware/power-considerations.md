# Power Considerations

## Purpose
Power behavior is one of the main constraints in this prototype. The documentation here captures why the current bench setup must stay conservative while the arm and sensors are being validated.

## Why Servos Should Not Rely Solely on Arduino Power
- Servo load can change quickly during motion, especially when multiple joints move together
- The Arduino is responsible for control logic, not for pretending to be a full actuator power supply
- If the supply path is weak, the arm can behave unpredictably even when the firmware is correct

## USB Limitations
- USB power is convenient for development and low-risk testing
- It is not a universal solution for actuator-heavy operation
- Logic behavior may look stable even when actuator demand is pushing the supply beyond a comfortable range

## Future External Power Considerations
- A more robust external supply path may be needed as the system grows
- Any future power design should include clear grounding and separation of noisy actuator paths from logic signals
- Power decisions should be tied to observed behavior rather than assumed headroom

## Safety Observations
- Sudden resets, weak motion, or jitter should be treated as power or stability warnings until proven otherwise
- The safe-state system should remain available even when motion power is limited
- Power tests should be recorded alongside the exact hardware configuration

## Template
- Power source specifications:
- Observed actuator behavior:
- Grounding notes:
- Safety protections:
- Thermal observations:
- Test summary:
