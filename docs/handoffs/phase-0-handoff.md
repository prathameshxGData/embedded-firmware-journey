# Phase 0 Handoff — Development Environment & Engineering Workflow

## Purpose

This document records the development environment, Git/GitHub workflow,
repository structure, documentation templates, and engineering practices
established during Phase 0.

Future phases should build on this foundation rather than recreate it.

---

# 1. Repository

## Local Repository

D:\job-switch-journey\embedded-firmware-journey\

## GitHub Repository

https://github.com/prathameshxGData/embedded-firmware-journey.git

## Git Configuration

Remote:

origin

Primary branch:

main

The local repository is connected to the GitHub remote.

At the completion of Phase 0, the working tree was verified clean and
synchronized with origin/main.

---

# 2. Repository Structure

Current repository structure:

embedded-firmware-journey/
│
├── 00-environment-setup/
├── 01-cortex-m-fundamentals/
├── 02-stm32-peripherals/
├── 03-adc-dma-measurement/
├── 04-swd-gdb-debugging/
├── 05-freertos/
├── 06-esp32-networking/
├── 07-mqtt/
├── 08-industrial-iot-platform/
├── 09-embedded-linux/
├── 10-arm-assembly/
├── 11-mcu-architecture/
│
├── docs/
│   ├── handoffs/
│   ├── learning-log/
│   └── engineering-notes/
│
├── README.md
├── .gitignore
└── .gitattributes

Git does not track empty directories.

Do not create fake placeholder files simply to make empty directories
appear in Git.

---

# 3. Hardware Available

Available hardware:

- STMicroelectronics NUCLEO-G491RE
- MCU: STM32G491RET6U
- ARM Cortex-M4
- ESP32 development module

There is currently no budget for additional sensors or hardware.

Experiments should prioritize:

- GPIO
- timers
- ADC
- UART
- USB
- built-in MCU peripherals
- generated/internal signals
- PC-side tools
- software-based verification

Do not assume access to:

- oscilloscope
- logic analyzer
- external sensors
- signal generator
- additional modules

When an experiment normally requires unavailable equipment, provide a
technically valid no-cost alternative where possible.

Clearly distinguish between:

1. Physically verified results
2. Software/debugger verified results
3. Theoretical reasoning that cannot be physically verified

---

# 4. Documentation Templates

Phase 0 established reusable documentation templates.

These templates should be reused in future projects.

## 4.1 Requirements Template

Location:

docs/templates/requirements-template.md

Purpose:

Define what the project must accomplish before implementation.

It contains:

- Project Description
- Hardware Requirements
- Software Requirements
- Power Requirements
- Functional Requirements
- Non-Functional Requirements
- Verification Method
- Status
- Notes

Requirements should describe what the system must do, not merely how it
will be implemented.

Example:

REQ-001: Firmware shall configure the selected GPIO pin as an output.
REQ-002: Firmware shall drive the GPIO output to the required logic level.

---

## 4.2 Project README Template

Location:

docs/templates/project-readme-template.md

Purpose:

Provide a professional structure for documenting individual projects.

It contains:

1. Project Overview
2. Objectives
3. Requirements
4. Hardware Requirements
5. Software Requirements
6. Concepts Covered
7. System Architecture
8. Project Structure
9. Implementation
10. Build Instructions
11. Flash / Run Instructions
12. Test Procedure
13. Expected Results
14. Actual Results
15. Evidence
16. Debugging / Issues
17. Limitations
18. Lessons Learned
19. Future Improvements
20. Verification Status
21. Repository / Documentation Notes

Use this as the starting point for project-specific README files.

---

## 4.3 Test Template

Location:

docs/templates/test-template.md

Purpose:

Document verification of requirements and actual system behavior.

It contains:

- Test ID
- Requirement
- Test Objective
- Preconditions
- Test Procedure
- Expected Result
- Actual Result
- Evidence
- Status

A test should clearly distinguish between:

Expected Result

and:

Actual Result

Never write an expected result as though it has already been observed.

---

## 4.4 Debugging Template

Location:

docs/templates/debugging-template.md

Purpose:

Document real technical problems and their resolution.

It contains:

- Issue ID
- Date
- Related Requirement / Test
- Problem Description
- Expected Behavior
- Actual Behavior
- Observed Evidence
- Initial Hypothesis
- Investigation
- Root Cause
- Corrective Action
- Verification
- Verification Result
- Final Status
- Lessons Learned

A debugging record should capture the technical root cause, not merely
classify an issue as "software" or "hardware."

---

# 5. Engineering Workflow

The established engineering workflow is:

Requirements
      ↓
Hardware + Constraints
      ↓
Software / Toolchain Selection
      ↓
Project / Folder Structure
      ↓
Architecture / Design
      ↓
Documentation Plan
      ↓
Implementation
      ↓
Build
      ↓
Flash / Run
      ↓
Test
      ↓
Debug if Necessary
      ↓
Retest
      ↓
Document Actual Results + Evidence
      ↓
Git Commit
      ↓
GitHub Push

This workflow should be adapted to the project rather than followed
mechanically when a project does not require every step.

---

# 6. Git Workflow

The Git state model learned during Phase 0 is:

Working Directory
        │
        │ git add
        ▼
Staging Area
        │
        │ git commit
        ▼
Local Repository
        │
        │ git push
        ▼
GitHub / Remote

The following commands are already understood:

git status
git diff
git add <filename>
git add .
git diff --staged
git restore --staged <filename>
git commit -m "message"
git log --oneline
git push

---

# 7. Git Practices

Before committing:

git status
      ↓
git diff
      ↓
Review changes
      ↓
Stage intended files
      ↓
git diff --staged
      ↓
Review staged changes
      ↓
git commit
      ↓
git log --oneline
      ↓
git status

Important rules:

- git add does not create a commit.
- git commit records the staged changes.
- git push sends existing commits to the remote repository.
- git add . can accidentally stage unrelated changes.
- git restore --staged <file> removes a file from staging without
  deleting the work.
- Commits should represent logical/atomic changes.
- Commit messages should describe the change truthfully.
- Do not commit secrets, credentials, temporary artifacts, or unrelated
  changes.
- Do not describe unverified work as complete.

---

# 8. Branch Understanding

Branches are used to isolate development.

Example:

main
  │
  └── feature/uart-driver

Changes committed to the feature branch do not automatically modify
main.

Branches are useful for:

- isolated feature development
- experimentation
- debugging
- keeping unfinished work away from stable code

Git history can also be used to compare previous states and investigate
when a problem was introduced.

A previous commit should only be described as "known good" if that state
was actually verified.

---

# 9. Requirements vs Implementation

A requirement describes what the system must do.

Implementation describes how the system achieves it.

Example:

Requirement:

REQ-001:
Firmware shall configure the selected GPIO pin as an output.

Possible implementation:

Application
    ↓
GPIO configuration
    ↓
STM32 GPIO peripheral
    ↓
GPIO pin
    ↓
LED

Do not confuse the implementation mechanism with the requirement itself.

---

# 10. Architecture Thinking

The basic architecture distinction established in Phase 0 is:

Application Logic
        ↓
Peripheral / Driver
        ↓
MCU Hardware
        ↓
Physical Interface

For example:

Application
    │
    │ decides ON/OFF
    ▼
GPIO Peripheral
    │
    │ produces logic level
    ▼
GPIO Pin
    │
    ▼
LED
    │
    ▼
Observable Result

Application logic decides what should happen.

The peripheral implements the required hardware function.

The physical interface produces the observable behavior.

---

# 11. Testing Standard

Testing should follow:

Requirement
    ↓
Test Objective
    ↓
Preconditions
    ↓
Test Procedure
    ↓
Expected Result
    ↓
Actual Result
    ↓
Evidence
    ↓
PASS / FAIL

If a test fails:

Test
 ↓
Expected vs Actual
 ↓
Failure
 ↓
Document
 ↓
Investigate
 ↓
Debug
 ↓
Root Cause
 ↓
Fix
 ↓
Retest
 ↓
Document Final Result

Never mark a test as PASS without verification.

---

# 12. Debugging Standard

When a real issue occurs, use:

Problem
    ↓
Expected Behavior
    ↓
Actual Behavior
    ↓
Evidence
    ↓
Initial Hypothesis
    ↓
Investigation
    ↓
Confirmed Root Cause
    ↓
Corrective Action
    ↓
Retest
    ↓
Verification

Do not simply change code repeatedly until the system appears to work.

The debugging record should explain why the problem occurred and how
the fix was verified.

---

# 13. Evidence Standard

Evidence may include:

- terminal output
- compiler output
- debugger observations
- register values
- UART logs
- screenshots
- measurements
- photos
- videos
- test results

Evidence must represent something that was actually observed.

Do not fabricate screenshots, measurements, logs, test results, or
hardware behavior.

---

# 14. Professional Documentation Principle

The repository should allow another engineer to understand:

- What the project does
- Why it exists
- What requirements it has
- What hardware is required
- What software is required
- How the system is structured
- How the firmware is implemented
- How to build it
- How to flash/run it
- How it was tested
- What actually happened
- What problems occurred
- How problems were debugged
- What limitations exist
- What was learned

The repository is intended to be both a learning record and a truthful
engineering portfolio.

---

# 15. Phase 0 Completion Status

Phase 0 established:

- Git fundamentals
- GitHub fundamentals
- Repository creation
- Remote configuration
- Git authentication
- Branch fundamentals
- Working directory / staging / repository model
- Professional commit workflow
- Git history usage
- Requirements documentation
- Project documentation
- Test documentation
- Debugging documentation
- Engineering workflow
- Portfolio documentation practices

Phase 0 is complete.

Future phases should build on this foundation.

---

# 16. Rules for Future Phases

When starting a new phase:

1. Do not restart Phase 0.
2. Do not recreate the GitHub repository.
3. Do not recreate existing documentation templates.
4. Reuse the existing requirements template when appropriate.
5. Reuse the project README template when appropriate.
6. Reuse the test template for verification.
7. Reuse the debugging template for real technical issues.
8. Follow the established Git workflow.
9. Keep commits logical and meaningful.
10. Document actual results only after testing.
11. Do not fabricate evidence.
12. Keep implementation, testing, documentation, and Git history
    synchronized.
13. If the repository structure needs to change, explain the technical
    reason before making the change.

---

# 17. Future Phase Handoffs

All phase handoff documents should be stored in:

docs/handoffs/

Example:

docs/handoffs/
├── phase-0-handoff.md
├── phase-1-handoff.md
├── phase-2-handoff.md
└── ...

Each handoff should record the important knowledge, completed work,
artifacts, workflow, and decisions from that phase.

This allows future phase chats to continue from the established state
without requiring the entire previous conversation to be repeated.

---

# 18. Important Principle

The purpose of this handoff is not to replace engineering judgment.

If a future project requires a different structure, tool, workflow, or
documentation approach, evaluate the requirement first.

Existing infrastructure should be reused when appropriate, not followed
blindly.

The goal is to maintain a professional, reproducible, truthful, and
maintainable embedded-firmware development workflow.