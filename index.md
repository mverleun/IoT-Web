---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: docs
---
# IoT for education

In education you want focus on learning objectivs and not be distracted by avoidable side effects.
It's about the **big picture** where a lot of skills are required. 

Teaching IoT is more than doing some programming in Python or C(++) to read sensor values or turn a LED on.
It's about sensors, microcontrollers, information storage, etc. It's also about connectivity, bluetooth, wifi, LoraWan and more. Roughly we identify 7 areas:
![IoT Components](https://raw.githubusercontent.com/mverleun/IoT-devices/master/Documentation/Images/IoT_Components.png)

Often devices cover multiple areas, the above image is meant to show the diversity of skills required to master IoT accross the board.

When working with novice students who who are not fully skilled it's important to make IoT easy accessible.

So no breadboards with loose or misplaced wires and sensors, but a robust collection of controllers, with shield, that are affordable hardware and interchangable.

An aspect often overlooked is the ability to update IoT devices remotely, sometimes in great quantities.

## ESP8266
The ESP8266 is a great controller for these kind of devices. It's cheap, has WiFi connectivity and there are many shields available with sensors.

The [homie convention](https://github.com/homieiot/convention) establishes a standard for IoT devices and is rapidly adopted as such. It also allows to update many devices at once for ESP8266 based devices. (If there is enough storage available).

The homie convention is available for ESP8266 based devices, but also as a Python framework. It avoids a lot of coding which results in clean firmwares that are easy to understand, even for novice students whilest meeting the earlier mentioned requirments.

## Wemos D1 Mini
Most of the firmwares are designed for the Wemos D1 Mini. The Wemos D1 Mini devices are easy to flash because they already have a micro USB connector on board. They also have enough storage to allow OTA updates. Their low price is an advantage as well as the ability to change the shields.

### Shields
There are many shields available for the Wemos D1 Mini. But DIY is also possible and not hard to do. 
Depending on the type of sensor or actuator 3 to 4 connections are required to connect it to the device.

## Python based homie
A python based example is also provided. The example simply sends keypresses from the keyboard to a MQTT topic, use it as a kind of remote control.
