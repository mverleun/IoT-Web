---
permalink: /docs/lesson-2/
title: "Lesson 2: Check hardware"
---

# Objectives
- Connect hardware
- Test hardware


# Connect hardware
In order to be able to do some things we need to connect hardware. In short we'll be using the following pins on the GPIO header of the Raspberry Pi as follows:

| Pin | Name (BCM) | Purpose |
| --- | --- | --- |
| 29  | GPIO5  | Switch 1 |
| 12  | GPIO18 | Switch 2 |
| 31  | GPIO6  | LED 1 |
| 12  | GPIO18 | LED 2 |
| 13  | GPIO27 | LED 3 |
| 15  | GPIO22 | LED 4 |
| 16  | GPIO23 | LED 5 |
| 18  | GPIO24 | LED 6 |
| 11  | GPIO17 | LED 7 |
| 36  | GPIO16 | DHT-11 |
| 3   | GPIO2  | I2C-SDA |
| 5   | GPIO3  | I2C-SCL |

Be carefull with the names and numbers. There are different numbering schemes. We use the BCM scheme here.

![](/img/lessons/lesson-2/hardware-schema.png)

In order to avoid connectivity and wiring errors I'll use a shield that has all the wiring on it.
It's called a IoT shield and the specs are on github.


# Test hardware

We do some basic testing with Node RED.

In order to create the test setup it is important to notice that switches function as input devices.
LED's function as output devices.

Let's wire them together. In the Node RED interface click on all the triangles on the left side until the majority of them are closed. It should look similar to this: ![](/img/lessons/lesson-2/node-red.png)

Drag an input node and an output node into the editor. Connect them using a virtual wire. ![](/img/lessons/lesson-2/flow-step-1.png)

Double click on the input node and select the corresponding pin (GPIO5, pin 29).
Change the resistor setting into 'pulldown'.
Finally enter a name, 'Switch 1'. Click on 'Done' when ready. ![](/img/lessons/lesson-2/flow-step-2.png)

Do the same with the output. Select Pin 31 (GPIO6), set type to 'Digital output' and name to LED 1. Click 'Done' when ready.
![](/img/lessons/lesson-2/flow-step-3.png)

Finally activate the flow by clicking on 'Deploy' in the upper right corner.

Press the switch. If all goes well de LED will light up when the switch is pressed. 

The status of both the switch and the LED is shown as well: ![](/img/lessons/lesson-2/flow-step-4.png)


This can be repeated for all connected switches and LED's.

# Python test
If you want you can test all sensors easily with a few lines of python.

First you need to install some software. Open a terminal and enter the following commands:

```bash
sudo pip install Adafruit_DHT
git clone https://github.com/mverleun/IoT-Devices
```

This will install and download the required files. Next step is to launch the python scripts. Enter the following commands in the terminal to get them running:

```bash
cd ~/IoT-Devices/Python
./LEDs-and-switches.py
./Light-sensor.py
```

Have fun.

# Troubleshooting

What if things go wrong?
LED's only work if the are connected properly. If not try to reverse the pins.
Also make sure that you use the proper wiring scheme. There are several scheme's and if you use the wrong one you'll be connecting to the wrong pins.

Make sure that you are not running multiple programs at the same time. What if one program tries to turn a switch on while the other wants to turn it off?

