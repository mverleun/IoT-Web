---
title: ESPHomelib
permalink: /docs/esphomelib/
---
This is by far the easiest framework I've seen sofar. [ESPHomelib](https://esphomelib.com/esphomeyaml/index.html) is developed by Otto Winter. It provides a great framework for ESP8266 and ESP32 based IoT devices. 

It is a framework that can be programmed low level, but also high level.
When using the high level all that is required is a simple configuration file in yaml format, which makes it very usable in education if students are not familiar (yet) with programming.

To use the BH-1750 light sensor one could write the following information in a file named `wemos_1.yaml`:

```
esphomeyaml:
  name: wemos_1
  platform: ESP8266
  board: d1_mini

wifi:
  ssid: '<SSID>'
  password: '<PASSWORD>'

mqtt:
  broker: 'mqtt.example.com'
  port: 1883
  # Remove # below if authentication is required
  # username: 'mqtt-user'
  # password: 'mqtt-password'
  topic_prefix: 'devices/wemos_1'

# Enable logging
logger:

ota:
  password: 'OTA PASSWORD'

### Hardware configuration starts here

# The BH-1750 is an I2C device. First configure which pins we use on the ESP8266.
i2c:
  sda: D1
  scl: D2
  scan: False

# Next configure the sensors
sensor:
  # Wifi Signal is an internal sensor.
  - platform: wifi_signal
    name: "WiFi Signal Sensor"
    update_interval: 10s
  # The BH1750 sensor by default uses address 0x23
  # Every 1 second a new sample is taken
  - platform: bh1750
    name: "Wemos_1 Brightness"
    address: 0x23
    update_interval: 1s
```

Once you've created this file compiling and uploading is as easy as running the command:

`$ esphomeyaml wemos_1.yaml run`

This will create the proper sourcecode, compile this sourcecode and upload the created firmware to the controller, either via USB or OTA (Over The Air).
