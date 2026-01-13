---
title: 'Learn DHT11 & DHT22 Interfacing with Arduino Nano – Step-by-Step Guide'
description: Arduino Nano DHT11 and DHT22 tutorial for real-time temperature and humidity monitoring with hardware setup, code, and Wokwi simulation.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-12-19
published_date : 2026-01-12
# prefer light image
banner_image : assets/blogs/arduino-nano/dht_11_22.png
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


![DHT 11 / 22](./../../../assets/blogs/arduino-nano/dht_11_22.png)

???+ Abstract "Table of Contents"

    [TOC]


## Abstract

In this article, we will learn how to interface the DHT11 / DHT22 temperature and humidity sensor with the Arduino Nano. These sensors are widely used in IoT, weather monitoring, HVAC systems, and smart agriculture projects.

We will cover the hardware connections, understand how the sensor works, write the Arduino program, and test the setup using real hardware or Wokwi simulation.

## :compass: Pre-Request

- OS : Windows / Linux / Mac / Chrome
- Arduino IDE 

## Hardware Required

<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"


- Arduino Nano. 
- DHT11 or DHT22 sensor
- BreadBoard.
- Mini USB Cable.
- Connecting wires.
- 5V DC power supply (Optional)

| Components | Purchase Link |
| -- | -- |
| Arduino Nano | [link](#) |
| DHT 11 | [link](#) |
| DHT 22 | [link](#) |
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

### Understanding the DHT11 / DHT22 Sensor

The **DHT sensors** measure:

* **Temperature**
* **Relative Humidity**

They use a **single-wire digital communication protocol**, making them very easy to interface with Arduino.

### Differences

| Feature           | DHT11    | DHT22           |
| ----------------- | -------- | --------------- |
| Temperature Range | 0–50 °C  | −40 to 80 °C    |
| Humidity Range    | 20–80 %  | 0–100 %         |
| Accuracy          | Moderate | High            |
| Cost              | Low      | Slightly higher |

---

## Sensor Pinout

Most DHT modules have **3 pins**:

| Pin  | Function            |
| ---- | ------------------- |
| VCC  | Power (3.3 V / 5 V) |
| DATA | Data Output         |
| GND  | Ground              |


### Connection Table

#### DHT Sensor → Arduino Nano

| DHT Pin | Arduino Nano |
| ------- | ------------ |
| VCC     | 5V           |
| DATA    | D2           |
| GND     | GND          |


!!! Note
    💡 If using a bare DHT sensor, connect a **10 kΩ pull-up resistor** between VCC and DATA.

![Circuit Diagram](./images/ckt.png)
/// caption
fig-Connection Diagram
///

## :open_file_folder: Code


!!! info
    Install the **DHT Sensor Library** from Arduino Library Manager.



```arduino linenums="1"

#include <DHT.h>

#define DHTPIN 2        // Data pin connected to Arduino Nano
#define DHTTYPE DHT22  // Change to DHT11 if using DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
Serial.begin(9600);
dht.begin();
}

void loop() {
float humidity = dht.readHumidity();
float temperature = dht.readTemperature();

if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
}

Serial.print("Humidity: ");
Serial.print(humidity);
Serial.print(" %  |  ");

Serial.print("Temperature: ");
Serial.print(temperature);
Serial.println(" °C");

delay(2000);
}




```


### Code Explanation

Let’s break down the Arduino sketch **line by line** to clearly understand how the DHT22 works with the Arduino Nano.

:point_right: Imports


```cpp linenums="1"
#include <DHT.h>

```

- `DHT.h`
    This library provides all the functions needed to communicate with DHT sensors, such as reading temperature and humidity values.
- 💡 These libraries hide the low-level DHT22 complexity and make sensor interface simple.

:point_right: Define Sensor details

```cpp linenums="3"
#define DHTPIN 2        // Data pin connected to Arduino Nano
#define DHTTYPE DHT22  // Change to DHT11 if using DHT11

DHT dht(DHTPIN, DHTTYPE);
```

* Sensor type connected is `DHT22`
* `D2` → connected to DHT22 Signal pin
* Create a DHT sensor object named `dht`, using the defined pin and sensor type. All sensor readings will be taken using this object.

```cpp linenums="8"
void setup() {
    Serial.begin(9600);
    dht.begin();
}

void loop() {
    float humidity = dht.readHumidity();
    float temperature = dht.readTemperature();

    if (isnan(humidity) || isnan(temperature)) {
        Serial.println("Failed to read from DHT sensor!");
        return;
    }

    Serial.print("Humidity: ");
    Serial.print(humidity);
    Serial.print(" %  |  ");

    Serial.print("Temperature: ");
    Serial.print(temperature);
    Serial.println(" °C");

    delay(2000);
}
```

* `dht.begin()` starts sensor communication.
* `readHumidity()` and `readTemperature()` get real-time data.
* Data is displayed on the **Serial Monitor** every 2 seconds.

!!! tip "Common Issues & Troubleshooting"
    | Issue               | Solution                |
    | ------------------- | ----------------------- |
    | No readings         | Check DATA pin number   |
    | NaN values          | Check sensor type       |
    | Sensor not detected | Ensure pull-up resistor |
    | Wrong values        | Use correct DHT type    |


---

## :material-chart-bubble:{style="color:#ffaa00"} Simulation

!!! danger "Not able to view the simulation"
    - :fontawesome-solid-laptop: Desktop or Laptop : Reload this page ( ++ctrl+r++ )
    - :fontawesome-solid-mobile: Mobile : Use Landscape Mode and reload the page


<iframe style="height:calc(100vh - 200px); border-color:#00aaff;border-radius:1rem;min-height:400px" src="https://wokwi.com/projects/452947149063387137" frameborder="2px" width="100%" height="700px"></iframe>

<!-- Advertisement -->
--8<-- "includes/arduino-link-cta.md"

--8<-- "includes/nano-craft-cta.md"

---

## :material-web-plus: Extras

### Components details

- Arduino Nano [Data Sheet](../blink-an-led-on-arduino-nano/files/nano-datasheet.pdf){target="_blank"}
- DHT 11 Sensor [Data Sheet](https://www.mouser.com/datasheet/2/758/DHT11-Technical-Data-Sheet-Translated-Version-1143054.pdf){target="_blank"} 

### Modules / Libraries Used

- DHT.h
    - Arduino library for DHT11, DHT22, etc Temp & Humidity Sensors.
    - [More info](https://www.arduinolibraries.info/libraries/dht-sensor-library){target="_blank"} 
    - [Github Source Code](https://github.com/adafruit/DHT-sensor-library){target="_blank"} 
  
---

## Conclusion

Interfacing a **DHT11 or DHT22 sensor with Arduino Nano** is one of the easiest ways to build a **temperature and humidity monitoring system**. With only one data wire, the sensor provides reliable environmental data that can be used in **IoT dashboards, weather stations, greenhouses, and smart homes**.

Using **Wokwi simulation**, you can test and debug your project even without physical hardware, making this setup perfect for **learning, teaching, and prototyping**.