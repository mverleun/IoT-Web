---
title: IoT Essentials learning objectives
permalink: /docs/Learning-Objectives/IoT-Essentials-learning-objectives/
---
Learning objectives IoT Essentials

What do we want people to know at an 'Essentials' level exam?

The IoT Landscape
=================

There are many ways to visualize the IoT landscape. IoT solutions often
start with some sensors that transmit data to the cloud where it is
visualized on a dashboard.

Actuators are introduced later on as well as is the storage of data, maybe even 'big data'.

The figure below identifies 7 elements, but just as with the OSI model,
these elements can be combined into a single device. As a result the 7
elements are not always clearly visible.

![](/img/IoT_Components.png)

In order to identify what is important to know, what is nice to now etc.
we need to explore the characteristics of the areas in more detail.

1 Sensors, actuators and micro-controllers
--
Sensors are collecting information, such as temperature, vibrations,
hart beat rate's etc. And that is all the do, they do not initiate an
action, they share the information so that decisions can be made either
at the level of the gateway/controller, or even in the cloud. Actuators
perform an action, e.g. a light get's switched on, the speed of a motor
is adjusted etc. They are often connected to micro-controllers such as
Arduino's, ESP8266 etc.

From an electronics point of view there are many way's to connect
sensors and actuators. There are analogue sensors and digital sensors.
The same goes for actuators.

Analog sensors and actuators
--
Analog sensors change the voltage that is fed into the micro-controller.
The micro-controller reads this value and converts it to a digital
value.

With analogue actuators the micro-controller sends an analogue value
which determines the behavior of the actuator. This could be used to
control the intensity of a lamp etc.

Digital Sensors and actuators
--
#### On/Off
Digital sensors use a variety of techniques to send information to the
micro-controller. This can be as simple as a switch (a sensor for
keypresses) that sends a digital high (1, true) or low (0, false)
signal.

Digital actuators receive digital information from the micro-controller
and will respond with an on/off action.

#### 1-Wire
A bit more complex is the usage of a 1-wire sensor. Here the sensor
sends sequences of digital high and low values that have to be received.
After reception of the complete sequence the micro-controller can
interpret the information. A well know example is the DHT-11 temperature
and humidity sensor.

Actuators received similar information from the micro-controller and act
according to the information received.

#### I^(2)C
I^(2)C devices are also known as I2C. The I^(2)C devices are connected to a digital bus system which consists of 2 wires for exchanging information. One is a clock signal and the clock-rate determines the speed at which information is exchanged. The other one carries the actual information. Device connected to the I2C bus have an address on this bus by which they can be identified.

#### Other serial protocols
There are other serial protocols that can be used to exchange
information or instructions between a micro controller and a device.
Examples are RS232 and RS422.

2 Communication between controller and gateway
---

At the level of the Sensors and Actuators we do not have IP addresses!
In order to make the information available to the internet IP addresses
are required. The role of the gateway is to convert the information from
sensors into something that has an IP address and vice versa for
actuators.

Vendors often use the word 'bridge' in their products which is
actually a gateway.

The connectivity between a gateway and the device can be hardwired, but
also be wireless. Wireless protocols often used are bluetooth, zigbee,
z-wave and LoraWan. Of course there are differences between the
protocols. Some are very energy efficient, some can transmit data over
long distances. Some can build mesh networks others can't. There is
also a difference in bandwidth and reliability of the wireless
connection. Most of these connections are not permanent, but ad-hoc
connections.

Information can be exchanged periodically, but what is the point of
repeating the same information if nothing has changed? Often it is
better in terms of bandwidth, power consumption of communication cost to
only exchange information when something has changed.

3 Gateways
----

Gateways ar the IP endpoints for sensors and actuators. They exchange
information with the cloud but also can contain logic to make decisions
and initiate actions. In that sense they are controllers as well.

Gateways can use any IP based protocol to communicate with the cloud.
Two popular protocols are HTTP Rest and MQTT. Sometimes gateways want to
communicate with each other directly to avoid as much latency as
possible or to be able to continue to function if the connection to the
cloud is (temporay) lost. COAP is a protocol that can be used for this
purpose.

Raspberry Pi's are great devices to be used for this purpose, but the
ESP8266 was originally designed to be a gateway as well, allowing
devices to communicate via RS232 to the ESP8266 which would than
'bridge' this information to WiFi.

4 Internet connectivity
-----------------------

The connectivity with the internet is again a range of techniques. DSL, Fiberoptics but also wireless connections form the back bone of the internet. The general expectation is that the internet is 'always on', but is it? If not, think about planes, cars driving into tunnels, ships on the ocean, the gateway might require that information is temporary queued.

5 Cloud
-------

In the cloud many technologies are used to provide services. Many are beyond the scope of this Essentials course. There are two services that should be know as they are popular and open service to exchange
information. These are the HTTP Rest interface and the MQTT broker. A good understanding of the MQTT protocol and its levels of QoS are essential.

A basic understanding of securing theses protocols is also important to know.

6 Data-center networks
----------------------

When designing the client side of IoT solutions it's not necessary to understand how data-centers manage and optimize their internal network infrastructure.

Developers of IoT solutions should be aware that a single MQTT broker can be a single point of failure and might want to consider the need for high availability solutions.

7 Apps and dashboards
---------------------

Apps and dashboards are back in the realm of the IoT solution designer. Dashboards can be used to control actuators or report the value of sensors. Applications can be written to automate processes where control
logic determine what actuators should do based on the values of sensors or other criteria such as time controlled logic.

Note that some solutions embed this control logic in the gateway to be independent of internet connectivity.

# Programming skills
When building IoT solutions programming skills can be very useful. There are solutions, e.g. Node RED, where programming is not required to build an IoT solution..

There are many programming languages that are used to build end-to-end solutions. Often a solution consists of multiple languages, e.g. C++ for the micro-controller, Python on the gateways and Java, Go and PHP for dashboards and apps in the datacenter.

When developing learning material programming is quite likely required to complete exercises. Clear instructions have to be provided.
# General security and privacy awareness
IoT devices can be abused for malicious practices if they are not secured correctly. A change in usage of electricity can be used to determine the absence of people in their homes for instance.

Presence detection is often used, but might interfere with someones privacy if people are tracked without their consent.

When storing (big) data many privacy rules and regulations require that only relevant data is collected with the proper consent and that this
information is destroyed once it is no longer needed for the purpose it was collected for.

To protect someones privacy data can be anonymized which is something that should be considered for any IoT solutions.

Default account names and passwords are another area of concern. Security has to be built-in by design and the obligation to change at least the default password is a minimum that should be done.

Furthermore it's not unreasonable to expect that IoT devices will require security updates at some point in time. Even if the programmer has done a perfect job, it could be that a vulnerability in a protocol has to be addressed. This means that IoT solutions should implement some kind of update strategy. This could be a user downloading an update and performing certain actions to install the update, but I could also be a
remote update mechanism where updates are pushed to devices.

# Monitoring devices
Traditional monitoring solutions often periodically try to connect to a service to see if this service is available. With IoT devices this is not always possible and/or desirable.

When IoT devices are mobile there IP address can change making it difficult to connect to them. Firewalls can be other obstructing mechanisms which make monitoring more challenging.

But even without these factors devices are often behind a gateway and have no IP address themselves. The gateway is the connection point to the internet (IP) world.

If a device does not send periodic updates of information then signaling based on absence of updates can't be done either. With MQTT devices it is possible to use the LWT messages to monitor the devices.

# Learning Objectives
Given the IoT landscape described above I propose the following learning objectives:

### Sensors, actuators and micro-controllers

Students should be able to describe commonly used electronic techniques that are used to connect sensors and actuators:

-   I^(2)C
-   1-Wire
-   RS232
-   Hardwiring (Digital and analogue)

Students should be able to identify sensors and actuators and explain their roles.

Students should understand the following criteria when selecting a micro-controller:

-   Power usage
-   CPU power
-   Memory
-   Interfaces available (both in types and quantity)
-   Connectivity method to gateway (wired, bluetooth, LoraWan, LTE)

### Communication between controller and gateway

Students should be able to explain the advantages and limitations of the following communication techniques between micro-controllers and gateways in terms of bandwidth, distance, power consumption, transmission frequencies and meshing abilities:

-   Bluetooth
-   Zigbee
-   Z-Wave
-   UTP
-   LoraWan

Note that frequencies may differ per region.

### Gateways

Students should be able to explain the role of the gateway.

Students should be able to identify at least the following protocols that are used by gateways:

-   COAP
-   HTTP Rest
-   MQTT

Students should be able to explain how the MQTT protocol works, they should be familiar with the following terms:

-   QoS
-   Publish and subscribe
-   Birth and LWT messages
-   Client identifier
-   Retained messages
-   Topics
-   Payload

Students should be able to explain the benefits of using authorization and authentication in combination with ACL's on a MQTT broker.

Students should demonstrate the meaning of MQTT being payload agnostic.

### Internet connectivity

Students should be able to explain the difference between encrypting network connections and encrypting the payload of messages that are exchanged.

Students should show awareness that IP addresses are not always fixed when using mobile devices and be able to identify these scenarios.

Students should be aware that network congestion can occur due to the number of devices that simultanously connect.

Students should be able to demonstrate awareness of round-trip times and latency and how this can affect IoT solutions.

### Cloud

Students should be able to identify single point of failures.

### Apps and dashboards

Students should be able to decide when logic is implemented in the cloud and when it's better to implement control logic in the gateway device.

Students should be familiar between open loop and closed loop control systems.

Students should be familiar with the differences between event driven (push) versus polling data collection.

Students should be able to distinguish different ways of exchanging information

-   JSON formatted
-   Plain text, numbers, booleans
-   HTTP Rest protocol

Students should be able to explain how historic data-sets can be achieved using different DB types: Elastichsearch, InfluxDB etc.

### Security and privacy

Students should demonstrate a global understanding of common  techniques to protect data:

-   Anonymizing
-   Encrypting
-   Limiting access to data

Students should be aware of data in transit and the difference between securing a connection and securing data end-to-end.
