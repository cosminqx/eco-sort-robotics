# Software Modules

This folder separates the software work into small, testable areas so firmware, communication, perception, and user-facing tooling can mature independently.

## Purpose
- Keep embedded control isolated from host-side logic and future AI work
- Make the laptop bridge explicit instead of hidden inside one firmware file
- Avoid coupling the prototype to a single monolithic application

## Current Software Roles
- Arduino control firmware on the Uno R3 handles deterministic servo execution and emergency stop behavior
- Arduino firmware on the UNO WiFi Rev2 reads sensors and emits structured state messages
- Python on the laptop validates, routes, and logs messages between the boards
- Future computer vision and AI work will live on the laptop, not on the Uno R3

## Subdirectories
- [arduino-control/](arduino-control/README.md)
- [serial-communication/](serial-communication/README.md)
- [python-computer-vision/](python-computer-vision/README.md)
- [ai-object-detection/](ai-object-detection/README.md)
- [dashboard-web-interface/](dashboard-web-interface/README.md)

## Development Order
1. Firmware and safe-state behavior
2. Serial communication contracts
3. Computer vision and object classification
4. Dashboard, analytics, and monitoring

## TODO
- Keep interfaces narrow and documented
- Add module-level implementation notes as code is introduced
