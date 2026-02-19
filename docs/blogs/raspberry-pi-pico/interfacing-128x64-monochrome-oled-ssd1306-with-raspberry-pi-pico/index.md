---
title: 'Interfacing 128x64 Monochrome OLED (SSD1306) with Raspberry Pi Pico (MicroPython)'
description: Display Text, Graphics & Sensor Values on OLED using I2C (Beginner-Friendly Guide) ⚡
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2026-02-19
published_date : 2026-02-19
# prefer light image
banner_image : assets/blogs/raspberrypipico/oled-display.png
tags:
  - raspberry pi pico
  - raspberry pi pico 2
  - raspberry pi pico w
  - raspberry pi pico 2W
  - OLED
  - micro python
  - guide
hide:
  - navigation
  - toc
draft: false
---


![OLED Display Interface](./../../../assets/blogs/raspberrypipico/oled-display.png)

???+ Abstract "Table of Contents"

    [TOC]



## 🧾 Abstract

Monochrome OLED displays are widely used in embedded projects because they are compact, sharp, and consume low power. In this guide, you will learn how to interface a **128x64 SSD1306 OLED display** with the **Raspberry Pi Pico variant** using **MicroPython**. By the end, you’ll be able to display text, draw shapes, and build your own mini dashboards.

---

## 📚 Prerequisites

Before starting, you should know:

* Basic understanding of **GPIO pins**
* Basic knowledge of **MicroPython**
* Familiarity with **Thonny IDE**


### ✅ Supported OS

| Platform      | Supported |
| ------------- | --------- |
| Windows 10/11 | ✅ Yes     |
| Ubuntu/Linux  | ✅ Yes     |
| macOS         | ✅ Yes     |

### Recommended Software Versions

| Software                    | Recommended Version |
| --------------------------- | ------------------- |
| MicroPython Firmware (Pico) | Latest stable       |
| Thonny IDE                  | 4.0+                |
| Python                      | 3.8+                |

!!! note
    If you're using Arduino IDE instead of Thonny, you can still follow the wiring section. The code section is written in **MicroPython**.

---

## 🧰 Hardware Required

<!-- Advertisement -->
--8<-- "includes/pico-disk-link-cta.md"


| Component           | Specification        | Quantity | Purchase Link                              |
| ------------------- | -------------------- | -------- | ------------------------------------------ |
| Raspberry Pi Pico   | RP2040 Dual Core     | 1        | [Buy Here](https://amzn.to/3JNpv7v)       |
| OLED Display Module | SSD1306, 128x64, I2C | 1        | [Buy Here](https://www.skilldisk.com/category/all-products)    |
| Breadboard          | Mini/Full size       | 1        | [Buy Here](https://www.skilldisk.com/category/all-products) |
| Jumper Wires        | Male-to-Male         | 5+       | [Buy Here](https://www.skilldisk.com/category/all-products)     |
| Micro USB Cable     | Data Cable           | 1        | [Buy Here](https://www.skilldisk.com/category/all-products)        |


---

## ⚡ Understanding the OLED Display (SSD1306)

The **SSD1306** is a popular OLED driver IC used in small 128x64 monochrome displays.

### Why SSD1306 OLED is Popular? 💡

* No backlight required (OLED pixels emit light)
* Very sharp text
* Low power usage
* Supports I2C and SPI
* Great for dashboards and sensor projects

### OLED Resolution Meaning

**128x64** means:

* 128 pixels horizontally
* 64 pixels vertically

You can draw:

* Text
* Lines
* Rectangles
* Icons (bitmaps)

---

## 🧷 Connection / Wiring Guide (I2C Mode)

Most SSD1306 OLED modules use **I2C**, which requires only 2 communication pins:

* SDA (Data)
* SCL (Clock)

### 📌 Pico to OLED Pin Mapping Table

| OLED Pin | Pico Pin | Pico GPIO | Description                     |
| -------- | -------- | --------- | ------------------------------- |
| VCC      | 3.3V     | —         | Power supply (3.3V recommended) |
| GND      | GND      | —         | Ground                          |
| SDA      | GP2      | GPIO2     | I2C Data Line                   |
| SCL      | GP3      | GPIO3     | I2C Clock Line                  |

!!! warning
    ⚠️ **Do NOT connect OLED VCC to 5V unless your OLED module explicitly supports it.**
    Most SSD1306 OLED displays are designed for **3.3V logic**.

!!! tip
    - Raspberry Pi Pico supports multiple I2C buses.
    - If you want, you can use other pins like `GP4/GP5` for I2C0.

---

## 🧩 Connection Diagram

![Circuit Diagram](./images/ckt_oled_pico.png)
/// caption
fig-Connection Diagram
///

---

## 🛠️ Step-by-Step Setup Instructions

✅ Step 1: Install MicroPython Firmware on Pico

✅ Step 2: Upload SSD1306 OLED Driver Library

MicroPython does not include OLED drivers by default, so we need:

* `ssd1306.py`

**Download Driver**: Download from github : [ssd1306.py](https://github.com/stlehmann/micropython-ssd1306/blob/master/ssd1306.py)

Upload to Pico using Thonny

1. Open Thonny
2. Save the driver content it into Pico as `ssd1306.py`

!!! tip
    Make sure the file is saved inside the Pico filesystem (not your PC).

---

## :open_file_folder: Code


=== "main.py"
    ```python linenums="1"
    from machine import Pin, I2C
    import ssd1306
    import time

    # ----------------------------------------
    # OLED Display Configuration
    # ----------------------------------------
    # I2C1 is used here:
    # SDA -> GP2
    # SCL -> GP3

    i2c = I2C(1, scl=Pin(3), sda=Pin(2), freq=400000)

    # OLED resolution (128x64)
    oled_width = 128
    oled_height = 64

    # Initialize OLED display
    oled = ssd1306.SSD1306_I2C(oled_width, oled_height, i2c)

    # ----------------------------------------
    # Function to display startup message
    # ----------------------------------------
    def startup_screen():
        oled.fill(0)  # Clear display
        oled.text('Welcome to',25,20)
        oled.show()
        time.sleep_ms(250)
        oled.text("Aavishkarah",20,34)
        oled.show()
        time.sleep(2)

    # ----------------------------------------
    # Function to display a counter
    # ----------------------------------------
    def counter_demo():
        count = 0
        while True:
            oled.fill(0)  # Clear display
            
            oled.text("Counter", 0, 0)
            oled.text("Count:", 0, 20)
            oled.text(str(count), 60, 20)
            
            oled.text("Aavishkarah", 25, 50)
            
            oled.show()
            count += 1
            time.sleep(1)

    # ----------------------------------------
    # Function to draw shapes
    # ----------------------------------------
    def shapes_demo():
        oled.fill(0)
        
        # Draw rectangle border
        oled.rect(0, 0, 128, 64, 1)
        
        # Draw filled rectangle
        oled.fill_rect(10, 10, 40, 20, 1)
        
        # Draw horizontal line
        oled.hline(0, 35, 128, 1)
        
        # Draw vertical line
        oled.vline(64, 0, 64, 1)
        
        oled.text("Shapes!", 70, 10)
        oled.text("Demo", 75, 25)
        
        oled.show()
        time.sleep(3)

    # ----------------------------------------
    # Main Program Execution
    # ----------------------------------------
    startup_screen()
    shapes_demo()
    counter_demo()
    ```

=== "ssd1306.py"

    ```
    # MicroPython SSD1306 OLED driver, I2C and SPI interfaces

    from micropython import const
    import framebuf


    # register definitions
    SET_CONTRAST = const(0x81)
    SET_ENTIRE_ON = const(0xA4)
    SET_NORM_INV = const(0xA6)
    SET_DISP = const(0xAE)
    SET_MEM_ADDR = const(0x20)
    SET_COL_ADDR = const(0x21)
    SET_PAGE_ADDR = const(0x22)
    SET_DISP_START_LINE = const(0x40)
    SET_SEG_REMAP = const(0xA0)
    SET_MUX_RATIO = const(0xA8)
    SET_IREF_SELECT = const(0xAD)
    SET_COM_OUT_DIR = const(0xC0)
    SET_DISP_OFFSET = const(0xD3)
    SET_COM_PIN_CFG = const(0xDA)
    SET_DISP_CLK_DIV = const(0xD5)
    SET_PRECHARGE = const(0xD9)
    SET_VCOM_DESEL = const(0xDB)
    SET_CHARGE_PUMP = const(0x8D)

    # Subclassing FrameBuffer provides support for graphics primitives
    # http://docs.micropython.org/en/latest/pyboard/library/framebuf.html
    class SSD1306(framebuf.FrameBuffer):
        def __init__(self, width, height, external_vcc):
            self.width = width
            self.height = height
            self.external_vcc = external_vcc
            self.pages = self.height // 8
            self.buffer = bytearray(self.pages * self.width)
            super().__init__(self.buffer, self.width, self.height, framebuf.MONO_VLSB)
            self.init_display()

        def init_display(self):
            for cmd in (
                SET_DISP,  # display off
                # address setting
                SET_MEM_ADDR,
                0x00,  # horizontal
                # resolution and layout
                SET_DISP_START_LINE,  # start at line 0
                SET_SEG_REMAP | 0x01,  # column addr 127 mapped to SEG0
                SET_MUX_RATIO,
                self.height - 1,
                SET_COM_OUT_DIR | 0x08,  # scan from COM[N] to COM0
                SET_DISP_OFFSET,
                0x00,
                SET_COM_PIN_CFG,
                0x02 if self.width > 2 * self.height else 0x12,
                # timing and driving scheme
                SET_DISP_CLK_DIV,
                0x80,
                SET_PRECHARGE,
                0x22 if self.external_vcc else 0xF1,
                SET_VCOM_DESEL,
                0x30,  # 0.83*Vcc
                # display
                SET_CONTRAST,
                0xFF,  # maximum
                SET_ENTIRE_ON,  # output follows RAM contents
                SET_NORM_INV,  # not inverted
                SET_IREF_SELECT,
                0x30,  # enable internal IREF during display on
                # charge pump
                SET_CHARGE_PUMP,
                0x10 if self.external_vcc else 0x14,
                SET_DISP | 0x01,  # display on
            ):  # on
                self.write_cmd(cmd)
            self.fill(0)
            self.show()

        def poweroff(self):
            self.write_cmd(SET_DISP)

        def poweron(self):
            self.write_cmd(SET_DISP | 0x01)

        def contrast(self, contrast):
            self.write_cmd(SET_CONTRAST)
            self.write_cmd(contrast)

        def invert(self, invert):
            self.write_cmd(SET_NORM_INV | (invert & 1))

        def rotate(self, rotate):
            self.write_cmd(SET_COM_OUT_DIR | ((rotate & 1) << 3))
            self.write_cmd(SET_SEG_REMAP | (rotate & 1))

        def show(self):
            x0 = 0
            x1 = self.width - 1
            if self.width != 128:
                # narrow displays use centred columns
                col_offset = (128 - self.width) // 2
                x0 += col_offset
                x1 += col_offset
            self.write_cmd(SET_COL_ADDR)
            self.write_cmd(x0)
            self.write_cmd(x1)
            self.write_cmd(SET_PAGE_ADDR)
            self.write_cmd(0)
            self.write_cmd(self.pages - 1)
            self.write_data(self.buffer)


    class SSD1306_I2C(SSD1306):
        def __init__(self, width, height, i2c, addr=0x3C, external_vcc=False):
            self.i2c = i2c
            self.addr = addr
            self.temp = bytearray(2)
            self.write_list = [b"\x40", None]  # Co=0, D/C#=1
            super().__init__(width, height, external_vcc)

        def write_cmd(self, cmd):
            self.temp[0] = 0x80  # Co=1, D/C#=0
            self.temp[1] = cmd
            self.i2c.writeto(self.addr, self.temp)

        def write_data(self, buf):
            self.write_list[1] = buf
            self.i2c.writevto(self.addr, self.write_list)


    class SSD1306_SPI(SSD1306):
        def __init__(self, width, height, spi, dc, res, cs, external_vcc=False):
            self.rate = 10 * 1024 * 1024
            dc.init(dc.OUT, value=0)
            res.init(res.OUT, value=0)
            cs.init(cs.OUT, value=1)
            self.spi = spi
            self.dc = dc
            self.res = res
            self.cs = cs
            import time

            self.res(1)
            time.sleep_ms(1)
            self.res(0)
            time.sleep_ms(10)
            self.res(1)
            super().__init__(width, height, external_vcc)

        def write_cmd(self, cmd):
            self.spi.init(baudrate=self.rate, polarity=0, phase=0)
            self.cs(1)
            self.dc(0)
            self.cs(0)
            self.spi.write(bytearray([cmd]))
            self.cs(1)

        def write_data(self, buf):
            self.spi.init(baudrate=self.rate, polarity=0, phase=0)
            self.cs(1)
            self.dc(1)
            self.cs(0)
            self.spi.write(buf)
            self.cs(1)

    ```
---

## 🧠 Code Explanation

Let’s break down what the code does.

---

:point_right: Import Required Libraries

```python
from machine import Pin, I2C
import ssd1306
import time
```

* `Pin`: controls GPIO pins
* `I2C`: creates I2C communication interface
* `ssd1306`: OLED driver library
* `time`: for delay

---

:point_right: Initializing I2C

```python
i2c = I2C(0, scl=Pin(1), sda=Pin(0), freq=400000)
```

This creates an I2C bus:

* Bus ID: `1` (I2C1)
* SCL = GPIO2
* SDA = GPIO3
* Frequency = `400kHz`

!!! note
    I2C speed is typically **100kHz** or **400kHz**.
    SSD1306 works well with 400kHz for faster screen refresh.

---

:point_right: OLED Initialization

```python
oled = ssd1306.SSD1306_I2C(oled_width, oled_height, i2c)
```

This tells MicroPython:

* The OLED resolution is `128x64`
* Communication uses I2C

---

:point_right: Clearing the Screen

```python
oled.fill(0)
oled.show()
```

* `fill(0)` clears the buffer
* `show()` updates the OLED hardware

!!! tip
    OLED updates only after `oled.show()` is called.        

---

:point_right: Displaying Text

```python
oled.text('Welcome to',25,20)
```

* First parameter: text string
* Second: X coordinate
* Third: Y coordinate

---

:point_right: Drawing Shapes

- Rectangle Border

```python
oled.rect(0, 0, 128, 64, 1)
```

* Draws a rectangle border around the screen.

- Filled Rectangle

```python
oled.fill_rect(10, 10, 40, 20, 1)
```

* Draws a solid box.

- Lines

```python
oled.hline(0, 35, 128, 1)
oled.vline(64, 0, 64, 1)
```

Used for UI design and separators.

---

:point_right: Counter Demo (Infinite Loop)

```python
while True:
    ...
```

The display updates every second with a new number.

!!! warning
    Since this loop never ends, it will run until the Pico is reset or unplugged.


---

## :material-chart-bubble:{style="color:#ffaa00"} Simulation

!!! danger "Not able to view the simulation"
    - :fontawesome-solid-laptop: Desktop or Laptop : Reload this page ( ++ctrl+r++ )
    - :fontawesome-solid-mobile: Mobile : Use Landscape Mode and reload the page


<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/456350845011331073" frameborder="2px" width="100%" height="700px"></iframe>


You can simulate Raspberry Pi Pico + OLED using Wokwi.

---

<!-- Advertisement -->
--8<-- "includes/pico-disk-link-cta.md"
--8<-- "includes/pico-iot-cta.md"

---

## 🧩 Extras (OLED Module Details & Documentation)

**SSD1306 OLED Pinout Reference**

| Pin | Meaning                               |
| --- | ------------------------------------- |
| VCC | Power (3.3V / 5V depending on module) |
| GND | Ground                                |
| SDA | I2C Data                              |
| SCL | I2C Clock                             |

!!! note
    Some OLED boards include onboard voltage regulators, but logic may still be 3.3V.
    Always check module datasheet.

---

## 🚀 Advanced Tips & Alternative Approaches

1. 💡 Use I2C0 Instead of I2C1: You can use different GPIO pins
2. 💡 Display Sensor Values (Mini Dashboard)
    Once OLED works, you can display:

    * Temperature (DHT11/DHT22)
    * Soil moisture
    * Ultrasonic distance
    * Potentiometer analog readings

3. Reduce OLED Flicker
    Instead of clearing full screen every time:

    * Update only parts of the display
    * Avoid too frequent `oled.show()`

---

## 🛑 Troubleshooting (Common Issues & Fixes)

### ❌ Issue 1: OLED Screen is Blank

✅ Possible causes:

* Wrong wiring
* Wrong I2C address
* OLED not powered properly

✅ Fix:

* Confirm connections
* Run I2C scan code
* Ensure VCC is connected to **3.3V**

!!! warning
    If you connect VCC incorrectly, OLED may not work or may get damaged.

---

### ❌ Issue 2: `ImportError: no module named 'ssd1306'`

✅ Cause:

* `ssd1306.py` not uploaded to Pico

✅ Fix:

* Upload `ssd1306.py` into Pico root directory using Thonny

---

### ❌ Issue 3: `OSError: [Errno 5] EIO`

✅ Cause:

* Pico cannot communicate with OLED over I2C

✅ Fix:

* Ensure SDA/SCL are correct pins
* Check loose jumper wires
* Try lowering I2C frequency:

```python
i2c = I2C(1, scl=Pin(2), sda=Pin(3), freq=100000)
```

---

### ❌ Issue 4: Text is Cut Off / Not Visible

✅ Cause:

* Wrong coordinates or screen size mismatch

✅ Fix:

* Ensure you set correct resolution:

```python
oled = ssd1306.SSD1306_I2C(128, 64, i2c)
```

## 🧪 Testing I2C Address (Recommended)

Most SSD1306 OLED modules use address:

* `0x3C` (most common)
* `0x3D` (rare)

Use this code to scan:

```python linenums="1"
from machine import Pin, I2C

i2c = I2C(0, scl=Pin(1), sda=Pin(0))
devices = i2c.scan()

print("I2C Devices Found:", devices)

for device in devices:
    print("Device Address (HEX):", hex(device))
```

!!! tip
    If you see `0x3c`, your OLED is detected correctly 🎉

---

## 🏗️ Project Extensions / Next Steps

Once your OLED is working, try these mini projects 🚀:

✅ 1. OLED Temperature Monitor 🌡️

* Connect a DHT11/DHT22 sensor
* Display temperature + humidity

✅ 2. Pico Stopwatch / Timer ⏱️

* Use push buttons for start/stop/reset
* Display time on OLED

✅ 3. IoT OLED Dashboard 🌐

* Use WiFi module Pico (Raspberry Pi Pico W or Pico 2 W)
* Fetch live data (weather, stock price, IoT sensor values)

!!! tip
    These projects make excellent portfolio demos for students and IoT beginners.

---

## 📌 References (Official & Useful Links)

- Raspberry Pi Pico / Pico 2 : [Pin Diagram](../pico2-pico2-w-key-features-pin-config/index.md){target="_blank"}
- Raspberry Pi Pico : [Data Sheet](https://datasheets.raspberrypi.com/pico/pico-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico 2 : [Data Sheet](https://datasheets.raspberrypi.com/pico/pico-2-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico W : [Data Sheet](https://datasheets.raspberrypi.com/picow/pico-w-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico 2 W : [Data Sheet](https://datasheets.raspberrypi.com/picow/pico-2-w-datasheet.pdf){target="_blank"}
- Raspberry Pi Pico Documentation: [Official Docs](https://www.raspberrypi.com/documentation/microcontrollers/raspberry-pi-pico.html)

📄 **SSD1306 Resources**

* SSD1306 Datasheet: [Datasheet](https://www.adafruit.com/datasheets/SSD1306.pdf)
* MicroPython SSD1306 Driver (Official): [GitHub Driver](https://github.com/stlehmann/micropython-ssd1306/blob/master/ssd1306.py)

---

## 🏁 Conclusion

You have successfully interfaced a **128x64 SSD1306 OLED display** with the **Raspberry Pi Pico** using **MicroPython** 🎉. Now you can display text, create UI dashboards, and visualize sensor data in your embedded projects. OLED displays are a powerful upgrade for IoT and maker builds—small but incredibly useful!


