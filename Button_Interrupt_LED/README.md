# STM32F446RE Button Interrupt using EXTI

## Overview

This project demonstrates interrupt-driven GPIO handling on the STM32F446RE microcontroller using direct register access.

The onboard user button connected to PC13 is configured to generate an external interrupt through EXTI13. When the button is pressed, an Interrupt Service Routine (ISR) is executed to toggle the onboard LD2 LED connected to PA5.

Unlike polling-based applications, the processor remains free to execute other tasks until an interrupt event occurs.

---

## Objectives

* Understand interrupt-driven embedded applications
* Configure EXTI peripheral registers
* Configure NVIC interrupt handling
* Implement Interrupt Service Routines (ISR)
* Understand interrupt execution flow
* Compare polling and interrupt-based approaches

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
* External interrupt configuration
* NVIC interrupt management
* Interrupt Service Routine (ISR)
* LED toggle on button press
* Register-level debugging

---

## Register Configuration

| Register       | Purpose                        |
| -------------- | ------------------------------ |
| RCC_AHB1ENR    | Enable GPIOA and GPIOC clocks  |
| RCC_APB2ENR    | Enable SYSCFG clock            |
| GPIOA_MODER    | Configure PA5 as output        |
| GPIOA_ODR      | Control LED state              |
| GPIOC_MODER    | Configure PC13 as input        |
| SYSCFG_EXTICR4 | Map PC13 to EXTI13             |
| EXTI_IMR       | Interrupt mask configuration   |
| EXTI_FTSR      | Falling edge trigger selection |
| EXTI_PR        | Clear pending interrupt flag   |
| NVIC_ISER      | Enable EXTI interrupt in NVIC  |

---

## Memory Map Used

| Peripheral          | Address    |
| ------------------- | ---------- |
| RCC Base Address    | 0x40023800 |
| GPIOA Base Address  | 0x40020000 |
| GPIOC Base Address  | 0x40020800 |
| SYSCFG Base Address | 0x40013800 |
| EXTI Base Address   | 0x40013C00 |

---

## Software Flow

1. Enable GPIOA and GPIOC peripheral clocks.
2. Configure PA5 as output.
3. Configure PC13 as input.
4. Enable SYSCFG peripheral clock.
5. Connect EXTI13 to PC13 using SYSCFG_EXTICR4.
6. Unmask EXTI13 interrupt using EXTI_IMR.
7. Configure falling-edge trigger using EXTI_FTSR.
8. Enable EXTI15_10 interrupt in NVIC.
9. Wait for button press event.
10. Execute ISR when interrupt occurs.
11. Toggle LED state.
12. Clear EXTI pending flag.

---

## Interrupt Execution Flow

```text
Button Press
      ↓
PC13 Detects Falling Edge
      ↓
EXTI13 Interrupt Generated
      ↓
NVIC Receives Interrupt Request
      ↓
ISR Executed
      ↓
LED State Toggled
      ↓
Pending Flag Cleared
      ↓
Return to Main Program
```

---

## Learning Outcomes

This project helped build understanding of:

* Cortex-M interrupt architecture
* EXTI peripheral operation
* Interrupt vector tables
* NVIC functionality
* Interrupt prioritization concepts
* Interrupt Service Routines (ISR)
* Event-driven software design
* Hardware interrupt debugging

---

## Polling vs Interrupts

| Polling                              | Interrupts                          |
| ------------------------------------ | ----------------------------------- |
| CPU continuously checks input status | CPU responds only when event occurs |
| Higher CPU utilization               | Lower CPU utilization               |
| Simpler implementation               | More efficient implementation       |
| Suitable for simple tasks            | Suitable for real-time applications |

This project demonstrates why interrupt-driven systems are preferred in most embedded applications.

---

## Debugging Experience

During development, the interrupt initially failed to trigger.

The issue was debugged by:

* Verifying SYSCFG clock enable configuration
* Checking EXTI13 mapping in SYSCFG_EXTICR4
* Verifying interrupt mask configuration in EXTI_IMR
* Validating falling-edge trigger configuration in EXTI_FTSR
* Monitoring interrupt pending status in EXTI_PR
* Verifying NVIC interrupt enable configuration
* Using debugger register view to trace interrupt execution

This exercise provided valuable experience in interrupt configuration and debugging.

---

## Relation to AUTOSAR MCAL

This project demonstrates hardware interrupt handling concepts that are typically abstracted by AUTOSAR MCAL and OS layers.

The implementation closely relates to:

* MCU Driver
* Port Driver
* DIO Driver
* AUTOSAR OS Interrupt Handling
* Complex Device Driver (CDD) Development

Typical AUTOSAR components involved in interrupt processing include:

```c
Mcu_Init();
Port_Init();
Dio_FlipChannel();
ISR(ExtiInterruptHandler)
{
    ...
}
```

Understanding interrupt configuration at the register level provides deeper insight into how AUTOSAR manages interrupt-driven events and hardware interactions.

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

* Interrupt Prioritization
* Multiple External Interrupt Sources
* Timer Interrupts
* UART Interrupt Handling
* DMA Interrupts
* RTOS Task Notification Using Interrupts

---

## References

* STM32F446RE Reference Manual (RM0390)
* STM32F446RE Datasheet
* STM32 NUCLEO-F446RE User Manual
* ARM Cortex-M4 Technical Reference Manual

