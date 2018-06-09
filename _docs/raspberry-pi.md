---
title: Raspberry Pi
permalink: /docs/raspberry-pi/
---
The Raspberry Pi is an important component within the concept of the IoT Kit.
It's powerfull enough to host service's like MQTT, Node RED and more. But it can also be extend with direct connected sensors and actuators. And even better, there any many programming languages available, so anyone can pick their favorite language when you want to program the I/O's yourselves instead of using Node RED.

# RPI IoT Shield
I can't call it a HAT, because it doesn't meet the official specs of a HAT, so I call it a shield.

When working with the Raspberry Pi we experienced many problems with breadboards: loose contacts, misplaced contacts, LED's inserted wrong are a few of them.

Not everybody wants to troubleshoot electronic problems instead of program errors so we decided to eliminate as much of these variables as possible while still keeping it simple.

The result is a shield with a few switches, a couple of LED's in various colours, a light sensor and a temperature/humidity sensor. These are the same components we use for the firmwares mentioned later.
No advanced electronic circuits, but the simplicity that you would also seek when using breadboards, but without the hassle mentioned earlier.

It looks like this: ![RPI IoT Shield](/img/IoT-Shield/IoT-Shield.png)

In my experience these are all the components required to do a proper introduction of IoT concepts.

The IoT Shield can be used with Node RED, but programming it in Python is also possible. Do you want to use another programming language? Feel free to do so, if your favorite programming language can be used with a breadboard it can be used with the IoT Shield as well.

# Jupyter Notebooks
If you're not familiar with these notebooks you're in for a pleasant surprise. [Jupyter notebooks](https://jupyter.org) allow you to combine documentation with executable code, all within the same notebook. The call it interactive computing.

This can be used to write snippets of code with explaining text. This snippets can be executed. The students get immediate feedback on their programming skills!

Notebooks can be exported and imported as well. This allows for easy sharing between students, or it can be used to hand in their homework.
