# STM32F446RE Bare-Metal LED Blink

## Overview

This project demonstrates GPIO programming on the STM32F446RE using direct register access without HAL GPIO APIs.

The onboard LD2 LED connected to PA5 is configured and controlled by manipulating RCC and GPIO registers directly. The project focuses on understanding the STM32 memory map, peripheral registers, and low-level embedded programming concepts.

---

## Features

* Direct register-level programming
* No HAL GPIO APIs used
* GPIO clock enable through RCC
* GPIO output configuration using MODER
* LED control using BSRR register
* Software delay implementation
* Register-level debugging using STM32CubeIDE

---

## Hardware

* STM32 Nucleo-F446RE Development Board
* STM32F446RE Microcontroller
* Onboard LD2 LED (PA5)

---

## Register Configuration

| Register      | Purpose                       |
| ------------- | ----------------------------- |
| RCC_AHB1ENR   | Enable GPIOA peripheral clock |
| GPIOA_MODER   | Configure PA5 as output       |
| GPIOA_OTYPER  | Configure PA5 output type     |
| GPIOA_OSPEEDR | Configure output speed        |
| GPIOA_PUPDR   | Configure pull-up/pull-down   |
| GPIOA_BSRR    | Set and reset LED state       |

---

## Memory Map Used

| Peripheral         | Address    |
| ------------------ | ---------- |
| RCC Base Address   | 0x40023800 |
| GPIOA Base Address | 0x40020000 |
| RCC_AHB1ENR        | 0x40023830 |
| GPIOA_MODER        | 0x40020000 |
| GPIOA_OTYPER       | 0x40020004 |
| GPIOA_OSPEEDR      | 0x40020008 |
| GPIOA_PUPDR        | 0x4002000C |
| GPIOA_BSRR         | 0x40020018 |

---

## Software Flow

1. Enable GPIOA peripheral clock using RCC.
2. Configure PA5 as a general-purpose output.
3. Configure output type as push-pull.
4. Configure output speed.
5. Disable pull-up and pull-down resistors.
6. Toggle LD2 LED using the BSRR register.

---

## Learning Outcomes

This project helped explore:

* STM32 memory map
* Peripheral base addresses
* Register offsets
* GPIO architecture
* RCC clock gating
* Memory-mapped I/O
* GPIO output configuration
* Write-only BSRR register behavior
* Bit manipulation
* Register-level debugging

---

## Debugging Experience

During development, the LED initially failed to blink.

The issue was debugged by:

1. Verifying GPIOA clock enable through RCC_AHB1ENR.
2. Checking GPIOA_MODER configuration for PA5.
3. Confirming PA5 output mode configuration.
4. Understanding the write-only nature of the BSRR register.
5. Verifying LED control by forcing PA5 HIGH.
6. Identifying the software delay duration as the root cause.

This exercise provided hands-on experience with register-level debugging and STM32 peripheral configuration.

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

---

## Future Enhancements

* GPIO Input using PC13 User Button
* Button-controlled LED
* External Interrupt (EXTI)
* Timer-based LED blinking
* UART driver development

---

## References

* STM32F446RE Reference Manual (RM0390)
* STM32F446RE Datasheet
* STM32 Nucleo-F446RE User Manual
