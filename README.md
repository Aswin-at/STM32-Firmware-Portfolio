# STM32 Bare-Metal Embedded Portfolio

## Overview

This repository documents my hands-on embedded systems learning journey using the STM32 NUCLEO-F446RE development board.

As an AUTOSAR Embedded Software Engineer with experience in Automotive Basic Software (BSW) development and testing, I created this repository to strengthen my understanding of low-level firmware development, microcontroller architecture, peripheral drivers, interrupt handling, and register-level programming.

The projects are implemented primarily using direct register access (Bare-Metal Programming) to gain a deeper understanding of how microcontroller peripherals operate beneath abstraction layers such as HAL and AUTOSAR MCAL.

---

## Hardware Platform

* STM32 NUCLEO-F446RE Development Board
* STM32F446RE ARM Cortex-M4 Microcontroller
* STM32CubeIDE
* STM32CubeMX

---

## Technical Objectives

The primary goal of this repository is to develop practical expertise in:

* GPIO Driver Development
* RCC (Reset and Clock Control)
* Register-Level Programming
* Interrupt Handling (NVIC & EXTI)
* Timer Peripherals
* UART Communication
* SPI Communication
* I2C Communication
* ADC Configuration
* PWM Generation
* RTOS Fundamentals
* Embedded Debugging Techniques

---

## Implemented Projects

### 01. LED Blink Using HAL

**Concepts Covered**

* GPIO Configuration using STM32CubeMX
* HAL Driver APIs
* System Tick Delay
* Basic Peripheral Initialization

---

### 02. LED Blink Using Register-Level Programming

**Concepts Covered**

* RCC Clock Enable Configuration
* GPIO Mode Register (MODER)
* GPIO Output Data Register (ODR)
* Bit Set Reset Register (BSRR)
* Direct Register Manipulation

---

### 03. Button Controlled LED

**Concepts Covered**

* GPIO Input Configuration
* GPIO Output Configuration
* Reading Input Data Register (IDR)
* Polling-Based Input Handling
* Basic Debouncing Concepts

---

### 04. Button Controlled LED Toggle

**Concepts Covered**

* State Management
* Edge Detection Using Polling
* Software Debouncing
* GPIO Output Control

---

### 05. External Interrupt (EXTI) Button Interrupt

**Concepts Covered**

* SYSCFG Configuration
* EXTI Line Mapping
* Interrupt Mask Register (IMR)
* Falling Edge Trigger Configuration
* NVIC Interrupt Configuration
* Interrupt Service Routine (ISR) Development

---

## Upcoming Projects

### Communication Peripherals

* UART Driver Development
* SPI Communication
* I2C Communication

### Timer Projects

* Timer Interrupt Generation
* Input Capture
* Output Compare

### Analog Peripherals

* ADC Data Acquisition
* PWM Generation

### Advanced Topics

* DMA
* CAN Communication
* FreeRTOS Fundamentals
* Bootloader Concepts

---

## Repository Structure

```text
STM32_Bare_Metal_Portfolio/
│
├── 01_LED_Blink_HAL/
├── 02_LED_Blink_Register_Level/
├── 03_Button_LED_Control/
├── 04_Button_LED_Toggle/
├── 05_EXTI_Button_Interrupt/
├── 06_UART_Communication/
├── 07_Timer_Projects/
├── 08_ADC_Projects/
├── 09_SPI_Communication/
├── 10_I2C_Communication/
├── 11_CAN_Communication/
└── 12_FreeRTOS/
```

## Development Environment

* Embedded C
* STM32CubeIDE
* STM32CubeMX
* Git
* GitHub

---

## Career Objective

This repository serves as a practical embedded systems portfolio demonstrating continuous learning beyond AUTOSAR application development.

The objective is to build strong expertise in:

* Embedded Firmware Development
* Device Driver Development
* AUTOSAR MCAL Concepts
* Automotive Software Architecture
* Real-Time Embedded Systems
* Bare-Metal Programming
* Microcontroller Peripherals and Hardware Interaction

Through these projects, I aim to bridge the gap between high-level AUTOSAR software development and low-level embedded firmware engineering.
