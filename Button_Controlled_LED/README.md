# STM32F446RE Button Controlled LED (Polling)

## Overview

This project demonstrates GPIO input and output handling on the STM32F446RE microcontroller using direct register access.

The onboard user button connected to PC13 is used to control the onboard LD2 LED connected to PA5. The implementation uses a polling mechanism to continuously monitor the button state and update the LED accordingly.

The project focuses on understanding GPIO input configuration, input data reading, output control, and polling-based embedded application design.

---

## Objectives

* Configure GPIO pins as input and output
* Read digital input signals using registers
* Control GPIO outputs using register-level programming
* Understand active-low button behavior
* Implement polling-based input handling

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
* GPIO input configuration
* GPIO output configuration
* Polling-based button monitoring
* LED control based on button state
* Register-level debugging

---

## Register Configuration

| Register    | Purpose                       |
| ----------- | ----------------------------- |
| RCC_AHB1ENR | Enable GPIOA and GPIOC clocks |
| GPIOA_MODER | Configure PA5 as output       |
| GPIOA_ODR   | Control LED state             |
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
2. Configure PA5 as General Purpose Output.
3. Configure PC13 as Input.
4. Continuously read PC13 using GPIOC_IDR.
5. Detect button press condition.
6. Turn LED ON when button is pressed.
7. Turn LED OFF when button is released.
8. Repeat indefinitely.

---

## Learning Outcomes

This project helped build understanding of:

* GPIO input configuration
* GPIO output configuration
* Input Data Register (IDR)
* Output Data Register (ODR)
* Polling mechanism
* Active-low input signals
* Digital signal monitoring
* Embedded software control flow

---

## Active-Low Button Behavior

The user button on the STM32 NUCLEO-F446RE board is configured as an active-low input.

| Button State | PC13 Value     |
| ------------ | -------------- |
| Released     | Logic High (1) |
| Pressed      | Logic Low (0)  |

Therefore, a button press is detected when PC13 reads LOW.

---

## Debugging Experience

During development, button detection was verified using STM32CubeIDE debugger.

The following checks were performed:

* Verification of GPIOA and GPIOC clock enable bits
* Verification of PA5 output configuration
* Verification of PC13 input configuration
* Monitoring GPIOC_IDR register values during button press
* Validation of active-low button operation
* Verification of LED output control through GPIOA_ODR

This exercise improved understanding of hardware signal monitoring and register-level debugging techniques.

---

## Relation to AUTOSAR MCAL

This project demonstrates functionality that is typically abstracted by AUTOSAR MCAL drivers.

The implementation closely relates to:

* MCU Driver (Peripheral Clock Configuration)
* Port Driver (Pin Direction and Configuration)
* DIO Driver (Digital Input Read and Output Write)

Typical AUTOSAR APIs performing similar functions include:

```c
Port_Init();
Dio_ReadChannel();
Dio_WriteChannel();
```

Implementing the functionality using direct register access provided a deeper understanding of how MCAL drivers interact with hardware peripherals.

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

* LED Toggle Application
* Software Debouncing
* External Interrupts (EXTI)
* Timer-Based Input Sampling
* AUTOSAR-like GPIO Driver Abstraction

---

## References

* STM32F446RE Reference Manual (RM0390)
* STM32F446RE Datasheet
* STM32 NUCLEO-F446RE User Manual
* ARM Cortex-M4 Technical Reference Manual
