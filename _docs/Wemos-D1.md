---
title: Wemos D1 mini
permalink: /docs/wemos-d1/
---
A controller that I like to use for IoT exercises is the ESP8266 based [Wemos D1 mini](https://wiki.wemos.cc/products:d1:d1_mini).
It has a USB connector that regulates the voltage of the device as well as all the required signalling to switch the device from operational mode into flash mode and vice versa.
They've got WiFi integrated and are really cheap if you buy them from the proper source. Use your favourite search engine to find a cheap supplier.

# Shields
There are many shields available for the Wemos D1 mini. You can buy them from the vendor mentioned above, or again, use your search skills on the internet to scout for them. There are many (Chinese) suppliers that sell this shields.
Popular shields to use are the ones with a:

* DHT-11 temperature and humidity sensor (I use the one where the data is transferred via pin D4 and not the I2C one.
* TB 16612 Motor driver. Note that this requires some additional work to flash the proper (working) firmware into the motor-driver. 
* BH 1750 light sensor. This requires a bit of DIY but this is not really difficult.
* HC-SR04 ultrasonic range meter. Again, a bit of DIY is required.

# Firmware
For each shield there is dedicated firmware written to handle that particular shield. This allows the code to be clean and compact.
The first time you load firmware from this project you'll have to connect the device via USB. Once you've got the firmware up and running and have the device connected to the MQTT broker firmware changes can be done remotely. Either use *homie ota* or a command-line tool to do this.

When changing shields you'll also have to change the firmware of the device to match them. 

# Mounting
If you want to mount the Wemos D1 mini you can have a look at this 3D design: [WEMOS D1 Mini Bumper Mount](https://www.thingiverse.com/thing:1848391)
It's easy to click the Wemos in it and you can remove it just as easy.
![](https://cdn.thingiverse.com/renders/37/21/52/b6/91/8fca6309c9e327e14d66e005eca00aef_preview_featured.jpg)


