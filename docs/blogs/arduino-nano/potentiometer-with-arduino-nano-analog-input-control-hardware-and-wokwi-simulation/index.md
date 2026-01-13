---
title: 'Potentiometer with Arduino Nano – Analog Input Control (Hardware & Wokwi Simulation)'
description: Arduino Nano and potentiometer tutorial for analog input control with hardware wiring, Arduino code, and Wokwi simulation.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-12-19
published_date : 2026-01-12
# prefer light image
banner_image : assets/blogs/arduino-nano/pot_interface.png
tags:
  - arduino nano
  - arduino
  - cpp
  - c
  - guide
  - DHT11
  - DHT22
hide:
  - navigation
  - toc
draft: false
---


![DHT 11 / 22](./../../../assets/blogs/arduino-nano/pot_interface.png)

???+ Abstract "Table of Contents"

    [TOC]


## Abstract

In this article, we will learn how to interface a **potentiometer** with the **Arduino Nano** to read analog values. A potentiometer is a variable resistor that allows us to manually change voltage levels, making it ideal for controlling brightness, motor speed, volume, and sensor calibration.

We will cover the **hardware connections**, understand how **analog input works**, write the **Arduino code**, and test the setup using **real hardware** or **Wokwi simulation**.

## :compass: Pre-Request

- OS : Windows / Linux / Mac / Chrome
- Arduino IDE 

## Hardware Required

<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"


- Arduino Nano. 
- Potentiometer (10kΩ)
- BreadBoard.
- Mini USB Cable.
- Connecting wires.
- 5V DC power supply (Optional)

| Components | Purchase Link |
| -- | -- |
| Arduino Nano | [link](#) |
| Potentiometer (10kΩ) | [link](#) |
| Mini USB Cable | [link](#) |
| BreadBoard | [large](https://amzn.to/4pgNX1c) : [small](https://amzn.to/47SMzvB)|
| Connecting Wires | [link](https://amzn.to/4pepr0H) |
| 5V DC Adaptor | [link](https://amzn.to/4m82t8D) |

!!! tip "Don't own a hardware :cry:"

    No worries,

    💡Still you can learn using simulation. check out simulation part :smiley:.

    💡Power your mission with reliable Arduino Kits. [Explore :simple-arduino: Hardware →](https://www.skilldisk.com/category/arduino){target="_blank"}

<!-- Nano Craft Advertisement -->
--8<-- "includes/nano-craft-cta.md"

## Understanding the Potentiometer

A **potentiometer** is a **three-terminal variable resistor**. It works as a **voltage divider**, producing a variable output voltage depending on the position of its knob.

### Pin Description

| Pin        | Function                  |
| ---------- | ------------------------- |
| Left Pin   | GND                       |
| Middle Pin | Output (Variable voltage) |
| Right Pin  | VCC (5V)                  |

As you rotate the knob, the middle pin outputs a voltage between **0V and 5V**.

## Connection Table

#### Potentiometer → Arduino Nano

| Potentiometer Pin | Arduino Nano |
| ----------------- | ------------ |
| Left Pin          | 5V           |
| Middle Pin        | A0           |
| Right Pin         | GND          |


!!! Note
    Arduino Nano has a built-in **10-bit Analog-to-Digital Converter (ADC)**.
    This converts voltage (0–5V) into digital values from **0 to 1023**.

    | Voltage | ADC Value |
    | ------- | --------- |
    | 0 V     | 0         |
    | 2.5 V   | ~512      |
    | 5 V     | 1023      |

![Circuit Diagram](./images/ckt.png)
/// caption
fig-Connection Diagram
///

## :open_file_folder: Code

```arduino linenums="1"

#define POT_PIN A0

void setup() {
Serial.begin(9600);
}

void loop() {
int potValue = analogRead(POT_PIN);

Serial.print("Potentiometer Value: ");
Serial.println(potValue);

delay(500);
}

```


### Code Explanation

* `analogRead(A0)` reads voltage from the potentiometer.
* The value ranges from **0 to 1023**.
* The value is displayed on the **Serial Monitor**.
* `delay(500)` updates the reading every 0.5 seconds.


---

## :material-chart-bubble:{style="color:#ffaa00"} Simulation

!!! danger "Not able to view the simulation"
    - :fontawesome-solid-laptop: Desktop or Laptop : Reload this page ( ++ctrl+r++ )
    - :fontawesome-solid-mobile: Mobile : Use Landscape Mode and reload the page


<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/453013917030743041" frameborder="2px" width="100%" height="700px"></iframe>

<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"

--8<-- "includes/nano-craft-cta.md"

---

## :material-web-plus: Extras

### Components details

- Arduino Nano [Data Sheet](../blink-an-led-on-arduino-nano/files/nano-datasheet.pdf){target="_blank"}

### Modules / Libraries Used

NIL
  
---

## Common Applications

* LED brightness control
* Volume control
* Motor speed control
* Menu navigation
* Sensor calibration

---

## Conclusion

Interfacing a **potentiometer with Arduino Nano** is one of the best ways to understand **analog input**. It allows real-time control of voltage, making it ideal for interactive electronics and IoT projects. Using **Wokwi simulation**, you can test and learn even without physical components.