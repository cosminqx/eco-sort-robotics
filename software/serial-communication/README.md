# Serial Communication

## Purpose
This folder defines the structured serial protocol between the Arduino UNO WiFi Rev2, the Python bridge on the laptop, and the Arduino Uno R3.

## Protocol Overview
- Messages are newline-delimited UTF-8 text
- Fields use a simple `key=value` format separated by `|`
- Every packet includes an explicit message type
- The Python bridge is the only board-to-board router

## Message Types
- `SENSOR` from the WiFi Rev2 to Python
- `CMD` from the WiFi Rev2 or Python to the Uno R3
- `ACK` from the Uno R3 back to Python
- `ERR` from any node when a message is malformed or rejected

## Command Types
- `STOP`
- `START`
- `MOVE_PICK`
- `MOVE_PLACE`
- `HOME`

## Sensor Data Fields
- `distance_cm`
- `object_detected`
- `state`
- Optional fields such as `source`, `node`, `reason`, and `seq`

## Example Messages
```text
SENSOR|node=wifi_rev2|state=RUNNING|distance_cm=24|object_detected=0
SENSOR|node=wifi_rev2|state=RUNNING|distance_cm=12|object_detected=1
CMD|source=wifi_rev2|action=STOP|reason=obstacle
CMD|source=python_bridge|action=MOVE_PICK|seq=14
ACK|node=uno_r3|action=MOVE_PICK|status=OK
ERR|node=uno_r3|code=UNKNOWN_ACTION|message=Unrecognized command
```

## Error Handling Strategy
- Ignore empty lines
- Reject messages that do not include a known type
- Treat malformed packets as `ERR` conditions rather than guessing intent
- Keep `STOP` as the highest-priority action in the system
- Log unexpected payloads on the Python bridge for debugging

## Design Notes
- Keep the protocol small and explicit
- Include safe-state handling in the message design from the start
- Avoid adding complexity that cannot be tested on the current prototype hardware

## Future Work
- Add sequence ids to every message once the protocol is stable
- Add optional timestamps if timing analysis becomes necessary
- Keep the protocol versioned before any AI or dashboard layer is added

## TODO
- Capture the first live protocol trace once the distributed path is running end to end
