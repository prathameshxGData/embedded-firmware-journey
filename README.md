# Embedded Firmware Journey

A 12-week hands-on learning and portfolio journey focused on becoming job-ready for Embedded Firmware / Embedded Systems Engineer roles.

The goal of this repository is to document my learning through actual implementation, experiments, debugging, testing, and engineering documentation rather than simply listing technologies I plan to learn.

## Career Goal

I am preparing for Embedded Firmware Engineer opportunities, with a focus on product-based startups in India.

This journey is intended to strengthen my practical skills and engineering fundamentals before I begin applying for jobs.

## Hardware

Current hardware available for this journey:

* **STM32 NUCLEO-G491RE**

  * STM32G491RET6U
  * ARM Cortex-M4
* **ESP32 development module**

Experiments will be designed around the available hardware and PC whenever possible. No additional sensors or hardware will be assumed unless specifically required later.

## Learning Roadmap

| Phase | Area                             | Status         |
| ----- | -------------------------------- | -------------- |
| 00    | Engineering Environment + GitHub | 🔄 In Progress |
| 01    | Cortex-M Fundamentals            | ⏳ Planned      |
| 02    | STM32 Peripherals                | ⏳ Planned      |
| 03    | ADC, DMA & Measurement           | ⏳ Planned      |
| 04    | SWD & GDB Debugging              | ⏳ Planned      |
| 05    | FreeRTOS                         | ⏳ Planned      |
| 06    | ESP32 Networking                 | ⏳ Planned      |
| 07    | MQTT                             | ⏳ Planned      |
| 08    | Industrial IoT Platform          | ⏳ Planned      |
| 09    | Embedded Linux                   | ⏳ Planned      |
| 10    | ARM Assembly                     | ⏳ Planned      |
| 11    | MCU Architecture                 | ⏳ Planned      |

## Repository Structure

```text
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
│   ├── learning-log/
│   └── engineering-notes/
│
└── README.md
```

## Engineering Documentation Standard

Projects and experiments will be documented with relevant information such as:

* Requirements
* Architecture
* Implementation details
* Build and flash instructions
* Test procedure
* Expected results
* Actual results
* Failure cases
* Debugging notes
* Limitations
* Screenshots and logs where useful
* Lessons learned

Documentation will reflect what was actually implemented and tested.

## Git Discipline

Git will be used throughout the journey to maintain a clear engineering history.

The repository will follow these principles:

* Make meaningful commits around logical milestones.
* Write descriptive commit messages.
* Keep changes focused where practical.
* Document bugs and fixes when relevant.
* Never commit passwords, private keys, API keys, or other secrets.
* Never claim a feature was implemented unless it was actually implemented and verified.

## Purpose of This Repository

This repository is both a learning record and a technical portfolio.

The objective is not to create a collection of copied examples. Each completed experiment should represent something I personally implemented, tested, debugged, and understood.

As the journey progresses, this repository will contain evidence of my practical development across embedded C/C++, ARM Cortex-M, STM32, peripherals, debugging, RTOS, connectivity, IoT, Embedded Linux, and MCU architecture.
