---
title: Homie
permalink: /docs/homie/
---
[Homie](https://github.com/marvinroger/homie-esp8266/) is developed by Marvin Roger. It provides a great framework for ESP8266 based IoT devices. 

The concept of homie has been extended to other environments as well. This allows you to create python applications that conform to the homie standard, creating a homogeneous environment.

Using homie allows us to keep the source code of our sensors and actuators focussed on accomplishing their tasks and not waste time on writing code to interact with the MQTT server directly.

Configuration management is also handled by this framework and it allows remote updates OTA (Over The Air)(ESP8266 Only).

This is great if you rapidly want to change firmware on a device to change it task, e.g. when you attach a different shield.
