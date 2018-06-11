---
title: Component overview
permalink: /docs/overview/
---
To get an understanding of what the IoT Kit is, or isn't, have a look at the picture below.

![Overview](/img/IoT-Shield/Overview.png)

It show's 3 workplaces with IoT Devices. These are connected via WiFi to a private cloud. This private cloud could be running on a cluster of Raspberry Pi's.
It's not difficult to build a 'Docker swarm' on a cluster of Raspberry Pi's which run a variety of services, such as a MQTT broker, Grafana for dashboards, etc.

The second image show more details of the components on the workplace.
![Overview](/img/IoT-Shield/Detailed-overview.png)
Each Wemos D1 mini controller can be equipped with a variety of shields which allows for flexibility when developing solutions. For each shield there is a matching firmware that remotely can be installed.
This allows for a lot of different scenarios with a limited number of controllers.

The Raspberry Pi has a [shield](/docs/raspberry-pi) that has the sensors and actuators needed to get the 'real' IoT experience and can be used standalone, without the Wemos D1 mini controllers.

