---
title: 'Raspberry Pi Pico 2 Series: Your Ultimate Pinout & Feature Guide'
description: Discover the major upgrades in the Raspberry Pi Pico 2 and Pico 2 W.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-06-05
published_date : 2025-06-13
# prefer light image
banner_image : assets/blogs/raspberrypipico/pico-2-and-pico-2-w-features-pin-config.png
tags:
  - raspberry pi pico 2
  - raspberry pi pico 2 w
hide:
  - navigation
---


![pico-2-and-pico-2-w-features-pin-config](./../../../assets/blogs/raspberrypipico/pico-2-and-pico-2-w-features-pin-config.png)

Pico 2 W is the latest, low cost IoT featured microcontroller available in market. with feature rich Upgrades from Cortex-M0+ processor to Cortex-M33 processor with higher SRAM capabilities and more. Let us do a point by point comparison in table format.


???+ Abstract "Table of Contents"

    [TOC]


## Raspberry Pi Pico 2

### Pin Configuration

![pico 2 pin config](./images/pico-2-pinout.svg)


### Key Features

- Raspberry Pi Pico 2 is powered by RP2350 microcontroller chip with 4 MB flash
- Dual Coretex-M33 or Hazard3 processor
- Support frequency up to 150 MHz
- Serial Wire Debug (SWG) 3-pin port
- SRAM of 560 kB
- On-board USB 1.1 for power and data
- 30 Multifunctional GPIO (General Purpose Input Output) pins
- 12-bit 500ksps ADC (Analogue to Digital Convertor) (A0, A1, A2)
- Serial Communication
  - 2 UART (Rx, Tx)
  - 2 I2C (Inter-Integrated Circuit) (SDA, SCL)
  - 2 SPI (Serial Peripheral Interface) (SCL, MISO, MOSI, SS)
- 24 PWM (Pulse Width Modulation) channels
- 2 Timers with 4 Alarms
- 3 Programmable IO (PIO) blocks, 12 state machines used for high-speed IO
- On-board buck-boost SMPS to generate 3.3V for microcontroller


[Raspberry Pi Pico 2 DataSheet :material-file-download:](https://datasheets.raspberrypi.com/pico/pico-2-datasheet.pdf){.md-button .md-button--primary}

## Raspberry Pi Pico 2 W

### Pin Configuration

![pico 2 w pin config](./images/pico2w-pinout.svg)
/// caption
Pico 2 W Pin Configuration
///

![pico 2 w Supply](./images/pico2w-supply.svg)
/// caption
Pico 2 W Supply Pins
///

![pico 2 w GPIO](./images/pico2w-GPIO.svg)
/// caption
Pico 2 W GPIO Pins
///


![pico 2 w ADC](./images/pico2w-ADC.svg)
/// caption
Pico 2 W ADC Pins
///


![pico 2 w I2C](./images/pico2w-I2C.svg)
/// caption
Pico 2 W I2C Pins
///

![pico 2 w SPI](./images/pico2w-SPI.svg)
/// caption
Pico 2 W SPI Pins
///

![pico 2 w UART](./images/pico2w-UART.svg)
/// caption
Pico 2 W UART Pins
///

### Key Features

- Raspberry Pi Pico 2 is powered by RP2350 microcontroller chip with 4 MB flash
- Dual Coretex-M33 or Hazard3 processor.
- Support frequency up to 150 MHz.
- On-board 2.4 GHz wireless interface (Infineon CYW43439) supporting
  - 802.11n wifi
  - Bluetooth 5.2
- Bluetooth
  - Supports bluetooth classic.
  - Support bluetooth LE central and peripheral roles.
- Serial Wire Debug (SWG) 3-pin port
- SRAM of 560 kB
- On-board USB 1.1 for power and data
- 30 Multifunctional GPIO (General Purpose Input Output) pins
- 12-bit 500ksps ADC (Analogue to Digital Convertor) (A0, A1, A2)
- Serial Communication
  - 2 UART (Rx, Tx)
  - 2 I2C (Inter-Integrated Circuit) (SDA, SCL)
  - 2 SPI (Serial Peripheral Interface) (SCL, MISO, MOSI, SS)
- 24 PWM (Pulse Width Modulation) channels
- 2 Timers with 4 Alarms
- 3 Programmable IO (PIO) blocks, 12 state machines used for high-speed IO
- On-board buck-boost SMPS to generate 3.3V for microcontroller

[Raspberry Pi Pico 2 W DataSheet :material-file-download:](https://datasheets.raspberrypi.com/picow/pico-2-w-datasheet.pdf){.md-button .md-button--primary}