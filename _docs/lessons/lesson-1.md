---
permalink: /docs/lesson-1/
title: "Lesson 1: Prepare Raspberry Pi"
---

# Objectives
- Install Raspbian
- Connect to a network
- Enable Node RED

# Install Raspbian

There are many sites where the installation of Raspbian is covered. The official installation guide for the Raspberry Pi is: [https://www.raspberrypi.org/documentation/installation/installing-images/](https://www.raspberrypi.org/documentation/installation/installing-images/).
Follow their guide to prepare the SD card for the Rasberry Pi. It's recommended to use a SD card with at least 16 Gb of storage capacity.
Make sure to download the 'full' version with all the recommended software.

# Connect to a network

IoT is about connected devices. Connect your Raspberry Pi to a network. You can use an UTP cable or connect via WiFi. It does not really matter as long as there are no blocking routers or firewalls.

To connect to WiFi click in the upper left corner on the network symbol:
![](/img/lessons/lesson-1/1-network.png)

A dropdown list will appear with all the discovered networks. Select the one that you want to connect to and click on it.

If the network is secured you will be prompted for credentials:
![](/img/lessons/lesson-1/2-wifi.png)

Please enter the credentials and open a terminal by clicking on the terminal icon in the menu bar.

Once the terminal is open enter the command `sudo raspi-config` and press enter:
![](/img/lessons/lesson-1/3-raspi-config.png)

Navigate the menu's to enable I2C:
![](/img/lessons/lesson-1/4-interfacing-options.png)
![](/img/lessons/lesson-1/5-i2c.png)

I2C is a communication technique that allows certain electronic components to communicate with others.


# Node RED
Node RED is installed by default but it is not enabled yet. Enter the following command to enable it:

```bash
sudo systemctl enable --now nodered.service
```
![](/img/lessons/lesson-1/node-red.png)

If you know the ip address of you Raspberry Pi you should be able to connect to Node RED from any workstation that has network access by entering the url `http://<ip address raspberry pi>:1880/`. 

We will use the webbrowser on the Raspberry Pi itself.
The url we use is `http://localhost:1880/`
![](/img/lessons/lesson-1/node-red-browser.png)


