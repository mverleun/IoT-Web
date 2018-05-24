---
layout: page
title: About
permalink: /about/
---

Iot Kit for Education is a project started by MarCoach (www.marcoach.nl).

It's largely based on the [homie iot convention](https://github.com/homieiot/convention/). The homie iot convention and framework are designed and maintained by Marvin Roger.
The primary devices used are Wemos D1 mini's, which are ESP8266 based devices. They're affordable
and have builtin WiFi.

[Homie OTA](https://github.com/jpmens/homie-ota) is used to remotely manage the devices and change their firmware. It's written by J.P. Mens

Other important components of the IoT Kit for Education are the Mosquitto MQTT server to exchange messages, Node RED as an easy to use visual editor to create workflows.
Data is stored in an Influx database and dashboards can be created with Grafana.
