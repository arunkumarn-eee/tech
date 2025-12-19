---
title: 'Blink an LED on Arduino Nano Using C/Cpp (Hardware & Simulation) : Step-by-Step Guide'
description: Beginner-friendly guide to LED blinking with Arduino Nano, C/C++, and online simulations.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
update_date : 2025-11-25
published_date : 2025-11-25
# prefer light image
banner_image : assets/blogs/arduino-nano/blink_led_nano.png
tags:
  - arduino nano
  - arduino
  - cpp
  - c
  - guide
hide:
  - navigation
  - toc
draft: false
---


![blink led](./../../../assets/blogs/arduino-nano/blink_led_nano.png)

???+ Abstract "Table of Contents"

    [TOC]


## Abstract

Arduino Nano Development board is equipped with ATmega328p chip, which has 32K bytes of Flash program memory, 2k bytes of SRAM and 1K bytes of EEPROM. Nano board supports Embedded System C, Cpp and arduino code.  

In this article we go through.

- Accessing the built-in led (13) of the Arduino Nano board.
- Turning `on` and `off` built-in led using arduino code.
- Simulation using wokwi.
- Hardware demo.

## :compass: Pre-Request

- OS : Windows / Linux / Mac / Chrome
- Arduino IDE. 


## Hardware Required

<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"

- Arduino Nano 
- Micro USB Cable.

| Components | Purchase Link |
| -- | -- |
| Arduino Nano | [Purchase Link](#) |
| Mini B USB Cable | [Purchase Link](#) |


!!! tip "Don't own a hardware :cry:"

    No worries,

    💡Still you can learn using simulation. check out simulation part :smiley:.

    💡Power your mission with reliable Arduino Kits. [Explore :simple-arduino: Hardware →](https://www.skilldisk.com/category/arduino){target="_blank"}


<!-- Advertisement -->
--8<-- "includes/nano-craft-cta.md"

### Connection Table

Built-in led of Arduino Nano is internally connected to GPIO 13.

| Particular | GPIO | Remarks | 
| :--: | :--: | :-- | 
| Built-in LED | 13 | Internally Connected |

![Built-in LED](./images/Built_in_LED_nano.png)

## :open_file_folder: Code


```arduino linenums="1"

void setup() {
  // Initializing built-in LED as OUTPUT pin
  pinMode(LED_BUILTIN, OUTPUT);
  // pinMode(13, OUTPUT);

}

void loop() {
  
  // Turning ON built-in LED
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000);

  // Turning OFF built-in LED
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000);

}


```

### Code Explanation


:point_right: Accessing built-in led of Arduino Nano board.

```arduino linenums="1"

void setup() {
  // Initializing built-in LED as OUTPUT pin
  pinMode(LED_BUILTIN, OUTPUT);
  // pinMode(13, OUTPUT);

}

```

- LED_BUILTIN (GPIO pin 13) is configured as `OUTPUT` pin (Line number 3) 
- You can alternatively use GPIO 13 in place of LED_BUILTIN.

:point_right: Blinking LED

```arduino linenums="8"

void loop() {
  
  // Turning ON built-in LED
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000);

  // Turning OFF built-in LED
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000);

}
```

- Continuous loop is achieved using `loop` method.
- `digitalWrite` is used to change the state of GPIO pin.
- `digitalWrite(LED_BUILTIN, HIGH);` sets the value of GPIO 13 to `HIGH` or `1`, which in turn  turns ON the LED. (line number 11)
- Delay of `1` second is achieved through `delay(1000);` method. (line number 12 & 16) 
- `digitalWrite(LED_BUILTIN, LOW);` sets the value of GPIO 13 to `LOW` or `0`, which in turn  turns OFF the LED. (line number 15)


!!! tip "Try It"
    - Change the value in the sleep method and observe the change in the on and off time.
        - `delay(2000)`, `delay(4000)` , etc
    - the values in terms of milli seconds.
        - `delay(1000)` : 1000 ms or 1 s
        - `delay(500)`  : 500 ms or 0.5 s

---

## :material-chart-bubble:{style="color:#ffaa00"} Simulation

!!! danger "Not able to view the simulation"
    - :fontawesome-solid-laptop: Desktop or Laptop : Reload this page ( ++ctrl+r++ )
    - :fontawesome-solid-mobile: Mobile : Use Landscape Mode and reload the page


<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/448605654738044929" frameborder="2px" width="100%" height="700px"></iframe>


<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"

--8<-- "includes/nano-craft-cta.md"

## Result

Above code turns ON LED for 1 second and OFF for 1 second. Similar to a square wave of `0.5 Hz` output connected to an LED.

---

## :material-web-plus: Extras

### Components details

- Arduino Nano [Data Sheet](./files/nano-datasheet.pdf){target="_blank"}


### Modules / Libraries Used

-Nil-