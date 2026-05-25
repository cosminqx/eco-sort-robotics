# Contributing Guidelines

Thank you for contributing to Eco Sort Robotics.

## Contribution Principles
- Keep changes modular and easy to review
- Document assumptions about hardware, power, and control state
- Prefer reproducible experiments, clear logs, and traceable decisions
- Avoid claims that imply completed autonomy when the system is still in prototyping

## Development Workflow
1. Create a focused branch for one change set.
2. Keep commits small and descriptive.
3. Update related documentation with the implementation or observation.
4. Include validation evidence such as test notes, logs, or manual checks.

## Pull Request Expectations
- Clear problem statement and intended outcome
- Files changed and why they changed
- Validation summary with any observed limitations
- Follow-up work or open risks that remain

## Documentation Requirements
When behavior changes, update the relevant architecture, hardware, software, and testing documents. At minimum, review:
- [SYSTEM_ARCHITECTURE.md](SYSTEM_ARCHITECTURE.md)
- [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md)
- [SOFTWARE_SETUP.md](SOFTWARE_SETUP.md)
- [TESTING.md](TESTING.md)
- folder-level docs under [docs/](docs/README.md), [hardware/](hardware/README.md), and [software/](software/README.md)

## Code and Safety
- Prioritize safe robotics behavior and fail-safe defaults
- Do not bypass the controlled STOP or SAFE state
- Keep communication protocols versioned and documented
- Treat power, servo motion, and manual control as safety-critical during prototype work
