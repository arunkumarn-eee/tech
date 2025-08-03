---
title: 'Next-Gen Pico: A Side-by-Side Comparison of Raspberry Pi Pico and Pico 2'
description: key differences between the original Pico and the upgraded Pico 2.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-06-05
published_date : 2025-06-12
# prefer light image
banner_image : assets/blogs/raspberrypipico/pico1-vs-pico2.png
tags:
  - raspberry pi pico
  - raspberry pi pico 2
hide:
  - navigation
---


![pico_1-vs-pico_2](./../../../assets/blogs/raspberrypipico/pico1-vs-pico2.png
)

Pico 2 is the newer 2<sup>nd</sup> generation of the raspberry pi pico board. Upgraded from Cortex-M0+ processor to Cortex-M33 processor with higher SRAM capabilities and more. Let us do a point by point comparison in table format.


???+ Abstract "Table of Contents"

    [TOC]


## Comparison Table

| Feature                              | Pico 1             | Pico 2             |
| ------------------------------------ | ------------------ | ------------------ |
| Processor                            | Cortex-M0+         | Cortex M33         |
| Controller                           | RP2040             | RP2350             |
| RISC-V Cores                         | None               | Hazard3            |
| Frequency                            | 133 MHz            | 150 MHz            |
| SRAM                                 | 264 kB (6 banks)   | 520 kB (10 banks)  |
| One Time Programmable Storage        | --                 | 8kB                |
| On-Board Flash                       | 2 MB               | 4 MB               |
| USB                                  | 1.1                | 1.1                |
| GPIO                                 | 30                 | 30                 |
| Analogue Input                       | 3(4)               | 3(4)               |
| ADC Resolution                       | 12 bit, 500 ksps   | 12 bit, 500 ksps   |
| PWM                                  | 16                 | 24                 |
| UART                                 | 2                  | 2                  |
| SPI                                  | 2                  | 2                  |
| I2C                                  | 2                  | 2                  |
| PIO state machines                   | 8                  | 12                 |
| HSTX (high-speed transmit periphera) | --                 | 1                  |
| Temperature Sensor (in-built)        | :white_check_mark: | :white_check_mark: |
| Serial Wire Debug (SWD)              | :white_check_mark: | :white_check_mark: |
| Languages                            | :simple-c: :simple-cplusplus: :simple-micropython: | :simple-c: :simple-cplusplus: :simple-micropython: |

!!! info "languages"

    - :simple-c: C Programming
    - :simple-cplusplus: C++
    - :simple-micropython: MicroPython


!!! tip "RP2350"

    RP2350 controller comes with different package, with and without flash-in-package.

      - RP2350A : QFN-60 : 30 GPIO : 4 Analogue
      - RP2350B : QFN-80 : 48 GPIO : 8 Analogue
      - RP2354A : QFN-60 : 30 GPIO : 4 Analogue : 2 MB Flash
      - RP2354B : QFN-80 : 48 GPIO : 8 Analogue : 2 MB Flash
    
    Both board supports Drag-and-drop programming using mass storage over USB


