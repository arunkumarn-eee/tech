---
title: 'Interfacing 16x2 LCD display with Raspberry Pi Pico & MicroPython'
description: Learn how to connect a 16x2 LCD display to a Raspberry Pi Pico using simple MicroPython code. This easy guide shows you how to set it up and display messages step by step.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-08-05
published_date : 2025-08-05
# prefer light image
banner_image : assets/blogs/raspberrypipico/16x2-lcd-display.png
tags:
  - raspberry pi pico
  - raspberry pi pico 2
  - raspberry pi pico w
  - raspberry pi pico 2W
  - micro python
  - guide
hide:
  - navigation
  - toc
draft: false
---


![16x2 lcd](./../../../assets/blogs/raspberrypipico/16x2-lcd-display.png)

???+ Abstract "Table of Contents"

    [TOC]


## Abstract

 In this article, a comprehensive step-by-step guide to control the brightness of an LED using PWM (Pulse Width Modulation) with Raspberry Pi Pico board using MicroPython. Raspberry Pi Pico has 4 different variants (Pico, Pico 2, Pico W, Pico 2W) supporting micro-python. This articles lays the foundation for more advanced embedded system and IoT projects.

## :compass: Pre-Request

- OS : Windows / Linux / Mac / Chrome
- Thonny IDE.
- MicroPython firmware in Raspberry Pi Pico / Pico 2 / Pico W / Pico 2W. 
    - For step by step procedure [click here](../installing-micropython/index.md){target="_blank"} . 


## Hardware Required

- Raspberry Pi Pico / Pico 2 / Pico W / Pico 2W. 
- 16x2 LCD.
- Potentiometer (POT)
- Resistor.
- BreadBoard.
- Micro USB Cable.
- Connecting wires.
- 5V DC power supply (Optional)

| Components | Purchase Link |
| -- | -- |
| Raspberry Pi Pico | [link](#) |
| Raspberry Pi Pico 2 | [link](#) |
| Raspberry Pi Pico W | [link](#) |
| Raspberry Pi Pico 2W | [link](#) |
| 16x2 LCD | [link](#) |
| Potentiometer (POT) | [link](#) |
| BreadBoard | [link](#) |
| Connecting Wires | [link](#) |
| Micro USB Cable | [link](#) |
| 5V DC Adaptor | [link](#) |

!!! tip "Don't own a hardware :cry:"

    No worries,

    Still you can learn using simulation.
    check out simulation part :smiley:.

### Connection Table


| 16x2 LCD | GPIO | Remarks | 
| :-- | :--: | :-- | 
| RS (4)  | 15 | Register Select Pin  |
| RW (5) | Ground | Read / Write Pin |
| E (6)  | 14 | Enable Pin  |
| D0 to D3  | -- | No connection  |
| D4  | 13 | Data line 4  |
| D5  | 12 | Data line 5  |
| D6  | 11 | Data line 6  |
| D7  | 10 | Data line 7  |


![Circuit Diagram](./images/16x-2_lcd_pico.png)
/// caption
fig-Connection Diagram
///

## :open_file_folder: Code

=== "main.py"
    ```python linenums="1"

    import utime
    from lcd_api import LCD_16x2_parallel


    # LCD_16x2_parallel(rs, e, d4, d5, d6, d7)
    lcd = LCD_16x2_parallel(15, 14, 13, 12, 11, 10)

    # Set cursor to Row 1, Column 1
    lcd.returnHome()
    lcd.display("  Aavishkarah   ")
    utime.sleep_ms(2000)

    # Move to LCD (2, 0) position 
    # Row 2 and Column 1 
    lcd.setCursor(2,0)
    lcd.display("---Simulation---" , 100)
    utime.sleep_ms(2000)


    # Clear the Screen
    lcd.clearScreen()
    lcd.display("Check Link for", 150)
    lcd.setCursor(2,0)
    lcd.display("more details" , 150)
    utime.sleep_ms(2000)

    ```

=== "lcd_api.py"
    ```python linenums="1"

    from machine import Pin
    import utime

    class LCD_16x2_parallel:
        
        def __init__(self, rs, e, d4, d5, d6, d7):
            self.rs = Pin(rs, Pin.OUT)
            self.e = Pin(e, Pin.OUT)
            self.d4 = Pin(d4, Pin.OUT)
            self.d5 = Pin(d5, Pin.OUT)
            self.d6 = Pin(d6, Pin.OUT)
            self.d7 = Pin(d7, Pin.OUT)
            self.setupLCD()

        def setupLCD(self):
            self.rs.value(0)
            self.send2LCD4(0b0011)
            self.send2LCD4(0b0011)
            self.send2LCD4(0b0011)
            self.send2LCD4(0b0010)
            self.send2LCD8(0b00101000)
            self.send2LCD8(0b00001100)#lcd on, blink off, cursor off.
            self.send2LCD8(0b00000110)#increment cursor, no display shift
            self.send2LCD8(0b00000001)#clear screen
            self.longDelay(2)#clear screen needs a long delay
            self.rs.value(1)

        def send2LCD4(self,BinNum):
            self.d4.value((BinNum & 0b00000001) >>0)
            self.d5.value((BinNum & 0b00000010) >>1)
            self.d6.value((BinNum & 0b00000100) >>2)
            self.d7.value((BinNum & 0b00001000) >>3)
            self.pulseE()

        def pulseE(self):
            self.e.value(1)
            utime.sleep_us(40)
            self.e.value(0)
            utime.sleep_us(40)
        
        def longDelay(self, t):
            utime.sleep_ms(t)

        def shortDelay(self,t):
            utime.sleep_us(t)
        
        def send2LCD4(self,BinNum):
            self.d4.value((BinNum & 0b00000001) >>0)
            self.d5.value((BinNum & 0b00000010) >>1)
            self.d6.value((BinNum & 0b00000100) >>2)
            self.d7.value((BinNum & 0b00001000) >>3)
            self.pulseE()
        
        def send2LCD8(self,BinNum):
            self.d5.value((BinNum & 0b00100000) >>5)
            self.d4.value((BinNum & 0b00010000) >>4)
            self.d6.value((BinNum & 0b01000000) >>6)
            self.d7.value((BinNum & 0b10000000) >>7)
            self.pulseE()
            self.d4.value((BinNum & 0b00000001) >> 0)
            self.d5.value((BinNum & 0b00000010) >> 1)
            self.d6.value((BinNum & 0b00000100) >> 2)
            self.d7.value((BinNum & 0b00001000) >> 3)
            self.pulseE()
        
        def setCursor(self, line, pos):
            b = 0
            if line==1:
                b=0
            elif line==2:
                b=40
            self.returnHome()
            for i in range(0, b+pos):
                self.moveCursorRight()
            
        def returnHome(self):
            self.rs.value(0)
            self.send2LCD8(0b00000010)
            self.rs.value(1)
            self.longDelay(2)

        def moveCursorRight(self):
            self.rs.value(0)
            self.send2LCD8(0b00010100)
            self.rs.value(1)

        def display(self, data, ms=0):
            for x in str(data):
                self.send2LCD8(ord(x))
                utime.sleep_ms(ms)

        def clearScreen(self):
            self.returnHome()
            self.display(" "*16)
            self.setCursor(2,0)
            self.display(" "*16)
            self.returnHome()


    ```

### Code Explanation

:point_right: Imports

```py linenums="1"

import utime
from lcd_api import LCD_16x2_parallel

```

- `time` module for creating delay.
- `lcd_api` module for interacting with 16x2 lcd display hardware.




!!! tip "Try It"
    - Alter the `display` method text to your required information and observe the output. 

---

## :material-chart-bubble:{style="color:#ffaa00"} Simulation

!!! danger "Not able to view the simulation"
    - :fontawesome-solid-laptop: Desktop or Laptop : Reload this page ( ++ctrl+r++ )
    - :fontawesome-solid-mobile: Mobile : Use Landscape Mode and reload the page


<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/438365155467439105" frameborder="2px" width="100%" height="700px"></iframe>


---

## :material-web-plus: Extras

### Components details

- Raspberry Pi Pico / Pico 2 : [Pin Diagram](../pico2-pico2-w-key-features-pin-config/index.md){target="_blank"}
- Raspberry Pi Pico : [Data Sheet](https://datasheets.raspberrypi.com/pico/pico-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico 2 : [Data Sheet](https://datasheets.raspberrypi.com/pico/pico-2-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico W : [Data Sheet](https://datasheets.raspberrypi.com/picow/pico-w-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico 2 W : [Data Sheet](https://datasheets.raspberrypi.com/picow/pico-2-w-datasheet.pdf){target="_blank"}


### Modules / Libraries Used

- *machine*
    - `machine` module contains specific attributes and methods related to hardware on a particular board. Here class `PWM` is imported to configure the GPIO pins as Pulse Width Modulator. 
    - [More Details](https://docs.micropython.org/en/latest/library/machine.html){target="_blank"} 

- *time*
    - `time` module provides functions related to date & time, measuring time intervals and generating delays.
    - [More Details](https://docs.micropython.org/en/latest/library/time.html){target="_blank"} 