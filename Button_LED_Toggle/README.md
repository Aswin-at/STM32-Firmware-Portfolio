# STM32F446RE Button Controlled LED Toggle (Polling)

## Overview

This project demonstrates button-triggered LED toggling on the STM32F446RE microcontroller using direct register access.

The onboard user button connected to PC13 is used to toggle the state of the onboard LD2 LED connected to PA5. Unlike a simple button-controlled LED application, the LED maintains its state after the button is released and changes state only when a new button press is detected.

The implementation introduces state management, edge detection, and software debouncing concepts commonly used in embedded systems.

---

## Objectives

* Implement button-triggered state changes
* Detect button press events using polling
* Understand edge detection concepts
* Implement basic software debouncing
* Practice bitwise operations for GPIO control

---

## Hardware

* STM32 NUCLEO-F446RE Development Board
* STM32F446RE ARM Cortex-M4 Microcontroller
* User Button (PC13)
* Onboard LD2 LED (PA5)

---

## Features

* Bare-metal implementation
* Direct register-level programming
* GPIO input and output configuration
* Polling-based button monitoring
* LED toggle functionality
* Software debouncing
* Register-level debugging

---

## Register Configuration

| Register    | Purpose                       |
| ----------- | ----------------------------- |
| RCC_AHB1ENR | Enable GPIOA and GPIOC clocks |
| GPIOA_MODER | Configure PA5 as output       |
| GPIOA_ODR   | Toggle LED state              |
| GPIOC_MODER | Configure PC13 as input       |
| GPIOC_IDR   | Read button state             |

---

## Memory Map Used

| Peripheral         | Address    |
| ------------------ | ---------- |
| RCC Base Address   | 0x40023800 |
| GPIOA Base Address | 0x40020000 |
| GPIOC Base Address | 0x40020800 |

---

## Software Flow

1. Enable clocks for GPIOA and GPIOC.
2. Configure PA5 as output.
3. Configure PC13 as input.
4. Continuously monitor button state.
5. Detect a valid button press event.
6. Toggle LED state using XOR operation.
7. Wait for button release.
8. Apply software debounce delay.
9. Continue monitoring for the next button press.

---

## Learning Outcomes

This project helped build understanding of:

* GPIO input handling
* GPIO output control
* State management
* Event-driven logic
* Edge detection concepts
* Software debouncing techniques
* Bitwise operations
* Polling-based embedded applications

---

## Button State Management

Unlike a basic button-controlled LED application, this implementation maintains an internal LED state.

| Button Event | LED Action |
| ------------ | ---------- |
| First Press  | LED ON     |
| Second Press | LED OFF    |
| Third Press  | LED ON     |
| Fourth Press | LED OFF    |

This behavior is commonly implemented using a state variable or bitwise toggle operation.

---

## Toggle Implementation

LED state is toggled using a bitwise XOR operation:

```c
GPIOA->ODR ^= (1 << 5);
```

The XOR operation flips the current state of PA5:

* 0 → 1 (LED ON)
* 1 → 0 (LED OFF)

This is a common technique used in embedded firmware development.

---

## Software Debouncing

Mechanical push buttons may generate multiple transitions during a single press due to contact bounce.

To avoid multiple LED toggles from a single button press:

* Button press is detected
* LED state is toggled
* Button release is awaited
* A short debounce delay is applied

This ensures a single toggle event per button press.

---

## Debugging Experience

During development, the following checks were performed using STM32CubeIDE:

* Verification of GPIOA and GPIOC clock enable configuration
* Validation of PA5 output mode settings
* Monitoring of PC13 input state through GPIOC_IDR
* Verification of LED state changes through GPIOA_ODR
* Investigation of multiple toggles caused by button bounce
* Validation of software debounce implementation

This exercise provided practical experience in debugging user input handling and state-based embedded applications.

---

## Relation to AUTOSAR MCAL

This project demonstrates concepts commonly abstracted by AUTOSAR MCAL drivers.

The implementation relates to:

* MCU Driver (Clock Configuration)
* Port Driver (Pin Configuration)
* DIO Driver (Input Read and Output Control)

Typical AUTOSAR APIs performing similar functionality include:

```c
Port_Init();
Dio_ReadChannel();
Dio_FlipChannel();
```

The LED toggle operation closely resembles the functionality provided by Dio_FlipChannel() in AUTOSAR DIO drivers.

Implementing the logic at register level provided deeper insight into how MCAL drivers perform digital I/O operations internally.

---

## Project Structure

```text
Src/
└── main.c

Inc/
└── main.h

STM32F446RE.ioc
STM32F446RE_FLASH.ld
```

## Future Enhancements

* Interrupt-Based Button Handling
* EXTI Configuration
* Timer-Based Debouncing
* AUTOSAR-like GPIO Driver Abstraction
* RTOS Task-Based Input Processing

---

## References

* STM32F446RE Reference Manual (RM0390)
* STM32F446RE Datasheet
* STM32 NUCLEO-F446RE User Manual
* ARM Cortex-M4 Technical Reference Manual
