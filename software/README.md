# Software Modules

This folder separates the software work into small, testable areas so firmware, perception, communication, and user-facing tooling can mature independently.

## Purpose
- Keep embedded control isolated from host-side vision and interface work
- Make future integrations easier to test and document
- Avoid coupling the prototype to a single monolithic application

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
- Add module-level implementation notes as code is introduced
- Keep interfaces narrow and documented
