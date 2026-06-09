# STM32_bare-metal-portfolio
# STM32 Embedded Learning Journey

This repository documents my hands-on journey into Embedded Systems development using the STM32 NUCLEO-F446RE development board.

As an AUTOSAR Embedded Software Engineer, I am using these projects to strengthen my understanding of microcontroller architecture, peripheral drivers, register-level programming, and embedded software development fundamentals.

The repository contains projects implemented using both STM32 HAL libraries and direct register manipulation to gain a deeper understanding of the underlying hardware.

## Hardware Platform

* STM32 NUCLEO-F446RE Development Board
* STM32F446RE Microcontroller
* STM32CubeIDE

## Learning Objectives

* GPIO Configuration
* Clock Management (RCC)
* Register-Level Programming
* Interrupt Handling
* Timers
* UART Communication
* SPI Communication
* I2C Communication
* ADC
* PWM Generation
* RTOS Fundamentals

## Project List

### 01. LED Blink using HAL

* GPIO configuration using STM32CubeMX
* HAL GPIO APIs
* HAL Delay

### 02. LED Blink using Register-Level Programming

* RCC clock configuration
* GPIO MODER configuration
* Direct register access
* GPIO ODR and BSRR usage

### Upcoming Projects

* Button Controlled LED
* External Interrupts (EXTI)
* UART Communication
* Timers
* PWM Generation
* ADC
* SPI Communication
* I2C Communication
* FreeRTOS Basics

## Repository Structure

```text
STM32-Embedded-Learning/
│
├── 01_LED_Blink_HAL/
├── 02_LED_Blink_Register_Level/
├── 03_Button_LED_Control/
├── 04_EXTI_Button_Interrupt/
├── 05_UART_Communication/
├── 06_Timer_Projects/
├── 07_ADC_Projects/
├── 08_SPI_Communication/
├── 09_I2C_Communication/
└── 10_FreeRTOS/
```

## Development Environment

* STM32CubeIDE
* STM32CubeMX
* Embedded C
* Git
* GitHub

## Purpose

The purpose of this repository is to document practical embedded systems development projects while building expertise beyond AUTOSAR application development and gaining stronger low-level firmware and microcontroller knowledge.

