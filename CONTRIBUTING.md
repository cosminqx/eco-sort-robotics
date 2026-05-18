# Contributing Guidelines

Thank you for contributing to Eco Sort Robotics.

## Contribution Principles
- Keep changes modular and well-scoped
- Document hardware/software assumptions explicitly
- Prefer reproducible experiments and traceable decisions
- Avoid unsupported claims in documentation or code comments

## Development Workflow
1. Create a focused branch for each feature/fix.
2. Keep commits atomic and descriptive.
3. Update related documentation in the same change set.
4. Include validation evidence in pull requests (tests, logs, or test notes).

## Pull Request Expectations
- Clear problem statement and proposed solution
- Files changed and rationale
- Validation summary (what was tested and how)
- Risks, limitations, and follow-up work

## Documentation Requirements
When modifying system behavior, update relevant files in:
- `SYSTEM_ARCHITECTURE.md`
- `HARDWARE_REQUIREMENTS.md`
- `SOFTWARE_SETUP.md`
- `TESTING.md`
- folder-level docs under `docs/`, `hardware/`, and `software/`

## Code and Safety
- Prioritize safe robotics behavior and fail-safe defaults
- Do not merge code that bypasses essential safety checks
- Keep communication protocols and interfaces versioned/documented
