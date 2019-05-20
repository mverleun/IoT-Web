---
permalink: /docs/lesson-3/
title: "Lesson 3: Connect to MQTT broker"
---

# Objectives
- Connect to MQTT broker
- Learn about topics

- Requirements: Working MQTT broker or public MQTT broker.

# Connect to MQTT broker
This time we'll be using Node RED once again.
Instead of controlling the LED's locally we want to use MQTT to send requests over the network. These requests in turn will turn the LED's on and off (If properly configured).

In this example I'll be using the public MQTT broker mqtt.iot-kit.nl
Feel free to host and use you own.

WARNING: We're using a public broker and we are not going to secure the network connection (yet). Please be careful.


