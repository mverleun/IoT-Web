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

When working with MQTT information is pushed to the broker. In turn the broker will forward the information to any device that is interested in this information. The information is categorized in topics.

Instead of the term 'pushing' we talk about 'Publishing'. And the interest in certain information is indicated by 'Subscribing' to a topic.
This is also known as a 'PubSub' system.

## Adding elements to the flow
Add a second'rpi gpio' input node to the existing flow. This time it is connected to GPIO18 and is the name 'Switch 2'. Again we have a 'pull down' resistor.
![](/img/lessons/lesson-3/switch-2.png)
Then connect a 'MQTT output' node to 'Swich 2' and double click on the purple node.

First of all we need to enter a new 'Server'. Click on the pencil and fill in the forms:
All you need to enter is the name of the 'Server' which is 'mqtt.iot-kit.nl'. ![](/img/lessons/lesson-3/mqtt-output-1.png)
When done click on 'Add' and fill in the rest.
In the 'Topic' field you enter 'switches/switch-2': ![](/img/lessons/lesson-3/mqtt-output-2.png)
When done click on 'Done' and then 'Deploy'.
Make sure that the MQTT node shows 'connected'.

If that goes well add a MQTT input node and configure it with the same broker and topic: ![](/img/lessons/lesson-3/mqtt-input-1.png)
Add an 'rpi output' for the LED. (GPIO17, LED 7) ![](/img/lessons/lesson-3/mqtt-input-2.png)

Deploy this flow and see what happens...

The first person that presses 'Switch 2' will turn on the LED on all connected systems!

And the first one to release the button will turn all LED's off.

You can see what is happening if you add a 'debug output' node like this: ![](/img/lessons/lesson-3/debug.png)
Make sure you select the 'debug' output column on the right side.

## Debugging MQTT

Sometimes it is difficult to troubleshoot MQTT problems. Especially if you do not have access to the MQTT broker.

By installing some commandline tools debugging becomes a bit less difficult. Install them by entering the following commands:

```bash
sudo apt update
sudo apt install mosquitto-clients
```

Once you are done you can use the commandline tools to publish information to a topic or subscribe to one.
In the following example we'll subscribe to a wildcard topic, which show a lot of information.

If you want to learn more about MQTT I recommend [this](https://mosquitto.org/man/mqtt-7.html) page.

Assuming that we are still using the same broker enter the following on the command line:

```bash
mosquitto_sub -h mqtt.iot-kit.nl -v -t '#'
```

Everytime somebody presses Switch 2 you'll get a notification on your screen. ![](/img/lessons/lesson-3/mosquitto_sub.png)

