# STM32G491 — Day 1 Notes

## 1. MCU Architecture

### CPU vs MCU

A CPU is mainly the processing core that executes instructions.

An MCU (Microcontroller Unit) combines:

* CPU core
* Flash memory
* SRAM
* Peripherals
* Timers
* GPIO
* Communication interfaces
* Interrupt system
* Clock system

inside a single chip.

### STM32G491 hierarchy

```text
Arm
 ↓
Cortex-M4
 ↓
STM32G4 family
 ↓
STM32G491
 ↓
STM32G491RET6U
```

The STM32G491 is an STMicroelectronics microcontroller based on an ARM Cortex-M4 processor core.

---

## 2. Cortex-M4

The STM32G491 uses an ARM Cortex-M4 CPU core.

The Cortex-M4 is designed for embedded and real-time applications.

Important characteristics:

* 32-bit ARM Cortex-M architecture
* Designed for microcontrollers
* Interrupt-driven operation
* Low-level hardware access through registers
* Supports an FPU

---

## 3. Memory

### Flash

Flash is non-volatile memory.

It is used primarily to store:

* Firmware/program code
* Constant data
* Other non-volatile program information

Flash retains its contents when power is removed.

For the STM32G491:

```text
Flash = 512 KB
```

The program was programmed starting at:

```text
0x08000000
```

### SRAM

SRAM is volatile runtime memory.

It is used for things such as:

* Variables
* Stack
* Runtime data
* Temporary working data

Its contents are not retained after power is removed.

### Registers

Registers are hardware-controlled memory locations used to configure and interact with the MCU and its peripherals.

For example, software can use registers to:

* Configure GPIO
* Read inputs
* Control timers
* Configure communication peripherals
* Enable/disable hardware features

---

## 4. Important STM32G491 Peripherals

### GPIO

General Purpose Input/Output.

Used for:

* LEDs
* Buttons
* Digital inputs
* Digital outputs
* Control signals

### ADC

Analog-to-Digital Converter.

Converts an analog voltage into a digital value that software can process.

### Timers

Hardware counters used for:

* Timing
* Delays
* PWM
* Pulse measurement
* Period/frequency measurement

### UART / USART

Serial communication peripherals.

Commonly used for:

* Debug output
* Communication with a PC
* Communication with other devices

### SPI

A high-speed synchronous serial communication interface.

Commonly used with:

* Displays
* Sensors
* Memory devices
* Other ICs

### I2C

A two-wire communication bus using:

```text
SCL
SDA
```

It is commonly used for connecting sensors and other peripherals.

### DMA

Direct Memory Access.

DMA allows certain peripherals to transfer data to/from memory with reduced CPU involvement.

### Interrupts

Interrupts allow hardware events to notify the CPU that something needs attention.

---

## 5. STM32G491 Development Board

Board used:

```text
NUCLEO-G491RE
```

MCU:

```text
STM32G491RETx
```

The NUCLEO board includes an ST-LINK interface that allows the PC to communicate with and program the MCU.

---

## 6. Programming and Debugging Interface

The board was connected to the PC through ST-LINK.

The STM32CubeIDE used:

```text
ST-LINK GDB Server
```

Communication with the MCU was performed using:

```text
SWD
```

SWD = Serial Wire Debug.

The successful programming log showed:

```text
Board       : NUCLEO-G491RE
Device name : STM32G491xx
Device CPU  : Cortex-M4
NVM size    : 512 KBytes
Voltage     : 3.28V
SWD freq    : 8000 KHz
```

The firmware was programmed at:

```text
0x08000000
```

and verification completed successfully.

---

## 7. STM32CubeIDE Project

Project name:

```text
day1_mcu_inside
```

The project was created as:

```text
STM32CubeIDE Empty Project
```

Important files include:

```text
Src/
    main.c

Startup/
    startup_stm32g491retx.s

STM32G491RETX_FLASH.ld
```

### main.c

The initial program contains an infinite loop:

```c
int main(void)
{
    for(;;);
}
```

This demonstrates the basic structure of a firmware program that continues executing indefinitely.

### Startup file

```text
startup_stm32g491retx.s
```

The startup file contains the low-level startup code required before normal C execution begins.

It is responsible for things such as establishing the initial execution environment and providing the interrupt/vector table.

### Linker script

```text
STM32G491RETX_FLASH.ld
```

The linker script tells the linker how the firmware should be organized in the MCU's memory.

It defines memory regions such as Flash and RAM and determines where program sections are placed.

---

## 8. Build Result

The project successfully compiled using the ARM GCC toolchain.

Build result:

```text
0 errors
1 warning
```

The warning was related to the FPU not being initialized while the project was compiled with FPU-related compiler options.

The firmware was still successfully built and programmed.

Generated executable:

```text
day1_mcu_inside.elf
```

---

## 9. Firmware Programming Flow

The complete workflow was:

```text
main.c
   ↓
ARM GCC compiler
   ↓
Object files
   ↓
Linker
   ↓
day1_mcu_inside.elf
   ↓
ST-LINK GDB Server
   ↓
SWD
   ↓
STM32G491 Flash
   ↓
Cortex-M4 executes firmware
```

---

## 10. Key Takeaways

1. STM32G491 is an MCU, not a CPU.
2. Its CPU core is ARM Cortex-M4.
3. Flash stores firmware and retains data without power.
4. SRAM is used for runtime data.
5. Registers provide software access to hardware configuration and status.
6. Peripherals allow the MCU to interact with the physical world.
7. ST-LINK provides programming and debugging connectivity.
8. SWD is used for debug/programming communication.
9. The firmware was successfully programmed into Flash at `0x08000000`.
10. The MCU successfully accepted and verified the firmware.

---

## Day 1 Practical Result

### Hardware

```text
NUCLEO-G491RE
STM32G491
```

### Development environment

```text
STM32CubeIDE
ARM GCC
ST-LINK GDB Server
```

### Result

```text
Firmware built successfully
        +
Firmware programmed successfully
        +
Download verified successfully
```

Day 1 successfully established the basic STM32 development workflow.
