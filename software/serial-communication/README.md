# Serial Communication

## Purpose
This folder will define how the Arduino and host computer exchange commands, state updates, and diagnostic information.

## Planned Responsibilities
- Host-to-Arduino control messages
- Arduino-to-host status and telemetry messages
- Versioned protocol definitions
- Basic diagnostics for debugging integration issues

## Design Notes
- Keep the protocol small and explicit
- Include safe-state handling in the message design from the start
- Avoid adding complexity that cannot be tested on the current prototype hardware

## Future Work
- Define a minimal text or framed message format
- Add logging for protocol errors and unexpected input
- Align the protocol with the Arduino UNO WiFi Rev2 if connected features are added later

## TODO
- Capture the first protocol draft after firmware and host assumptions are finalized
