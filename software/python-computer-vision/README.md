# Python Computer Vision

## Purpose
This folder will hold the Python-based perception and AI pipeline used later for object-aware handling and sustainability sorting experiments.

## Role in the Distributed System
- Python currently acts as the laptop bridge between the two Arduino boards
- Future computer vision and object classification will live in this layer, not on the Uno R3
- The bridge must stay explicit so the control path remains debuggable and safe

## Planned Responsibilities
- Message parsing and routing between the WiFi Rev2 and the Uno R3
- Image acquisition and preprocessing for future vision work
- OpenCV-based experimentation and inspection tools
- Data handling for later classification work

## Current Status
- The computer vision pipeline is planned, not yet integrated into the active control loop
- The current focus remains on stable robotics, serial routing, and safe embedded control

## Future Work
- Establish a repeatable image capture workflow when perception work starts
- Define preprocessing steps that match the eventual dataset format
- Keep the computer vision work decoupled from safety-critical motion control

## TODO
- Add setup details once the Python environment and capture path are defined
