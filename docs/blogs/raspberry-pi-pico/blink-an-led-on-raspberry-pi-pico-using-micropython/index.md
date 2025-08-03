---
title: 'Blink an LED on Raspberry Pi Pico Using MicroPython (Hardware & Simulation) : Step-by-Step Guide'
description: Beginner-friendly guide to LED blinking with Raspberry Pi Pico, MicroPython, and online simulations.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-06-05
published_date : 2025-07-17
# prefer light image
banner_image : assets/blogs/raspberrypipico/pico-led-blinking.png
tags:
  - raspberry pi pico
  - raspberry pi pico w
  - micro python
  - guide
hide:
  - navigation
  - toc
draft: true
---


![blink led](./../../../assets/blogs/raspberrypipico/pico-led-blinking.png)

???+ Abstract "Table of Contents"

    [TOC]


## Abstract


## Pre-Request



## Circuit Diagram


## Hardware Required

### Components detail

## Connection Diagram

### Connection Table

## Code

```python

from machine import Pin
import utime

# Built-in LED is connected to GPIO 25
led = Pin(25, Pin.OUT)

while True:
    led.on()
    utime.sleep(1)
    led.off()
    utime.sleep(1)


```

### Libraries Used

### Code Explanation

## Simulation

<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/434985121708836865" frameborder="2px" width="100%" height="700px"></iframe>

## Result

## Conclusion
