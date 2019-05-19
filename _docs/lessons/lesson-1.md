---
permalink: /docs/lesson-1/
title: "Lesson 1: Installing Raspbian"
---
When looking for firmware don't forget to check the following projects:
[sonoff/tasmota](https://github.com/arendst/Sonoff-Tasmota/tree/development/sonoff),
[espeasy](https://www.letscontrolit.com/wiki/index.php/ESPEasy) and
[espurna](https://bitbucket.org/xoseperez/espurna).

They are universal firmwares that can do multiple things. Even though they're not difficult to use, they all have their own mqtt topics, data formats und update procedures making them less intuitive. Also their source code has grown over time, making it less easy to study it in a short time.

They may provide what you need, or can be used as inspiration for your own projects.

## Multiple firmwares
Instead of creating a great universal firmware that supports a multitude of shields this project consists of dedicated firmwares for a specific task.

This can be done with both the homie framework as well as with ESPHomelib. Homie requires programming in C, ESPHomelib does not. Both frameworks require PlatformIO to build the firmware.

## Option 1: Homie with PlatformIO
Development of the firmwares is done using [PlatformIO](https://platformio.org). This is a great open source IDE that supports a wide variety of boards. All the examples mentioned on this site assume that directories are structured according to the structure of this
platform.

When including external libraries this is often done via the file
`platformio.ini`. Each firmware has its own copy of this file.

### Initial configuration of the firmware

When the device has enough storage capacity the configuration can be done easily through a web browser. Each freshly flashed device will start as an access-point where you can connect to. Simply fill in the required information and the device is ready for use.

It is also possible to create a config file in JSON format and upload it to the device. An example file is provided in the directory `data/homie` of the downloaded source-code. Rename `config.json.example` into `config.json` and modify the settings to match your configuration.

A typical `config.json` file looks like this:

```
{
  "wifi":{
    "ssid":"<Your SSID>",
    "password": "<Password>"
    },
  "mqtt":{
    "host":"<Your MQTT Server",
    "port":1883,
    "base_topic":"devices/",
    "username": "<mqtt username>",
    "password": "<mqtt password>",
    "auth":true
  },
  "name":"Sensor x",
  "ota":{
    "enabled":true
    },
  "device_id":"wemos-x"
}
```

This is an example where MQTT authentication is required, which is recommended.
If you don't want to use authentication you can use the following as a template:

```
{
  "wifi":{
    "ssid":"<Your SSID>",
    "password": "<Password>"
    },
  "mqtt":{
    "host":"<Your MQTT Server>",
    "port":1883,
    "base_topic":"devices/"
  },
  "name":"Sensor x",
  "ota":{
    "enabled":true
    },
  "device_id":"wemos-x"
}
```

>   The base_topic setting normally is `"homie/"`. Make sure to be consistent when changing the value to something else.

Once the device is configured it is possible to change them via MQTT. Detailed configuration instructions can be found in the homie documentation.

### First-time flashing
If you want to upload the `config.json` file to start with configured devices you'll have to upload the files into the spiffs filesystem first. This can be done from within platformio by running the command `pio run -t uploadfs`.

When the files have been uploaded you can upload the firmware. From the terminal you can run the command `pio run -t upload`.

Afterwards the device restarts and connects to the WiFi. When this is done the device will connect to the configured MQTT server.

## Option 2: ESPHomelib with yaml config file
When using ESPHomelib it is possible to generate the source-code automatically. Building the firmware still requires that PlatformIO is installed, but it is invisible to the novice user.

The approach is slightly different. For each controller you'll have to create a config file. Each config file consists of multiple sections where you can configure the Wi-Fi settings, the MQTT broker and a, unique, name for the device.

The other sections describe the hardware. You'll have to specify the controller you're using, the sensors or actuators you're connecting to the controller and you have the ability to influence the behaviour of this device. 

This is very powerful and allows automation to take place on a device, but it also allows to do conversions (Fahrenheit to Celsius etc.), influence reporting intervals, calculate averages and much more.

An example config file could look like this:

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
    # the following name will be added to the MQTT base topic
    name: "WiFi"
    update_interval: 10s
  # The BH1750 sensor by default uses address 0x23
  # Every 1 second a new sample is taken
  - platform: bh1750
    # the following name will be added to the MQTT base topic
    name: "Brightness"
    address: 0x23
    update_interval: 1s
    
  # All values are reported to the MQTT topic(s) created in the sensor
  # section where the topic has '/state' appended to it.
  # In this example:
  # devices/wemos_1/WiFi/state
  # devices/wemos_1/Brightness/state
```

Let's assume that the name of this file is `wemos_1.yaml`. Once you've created this file compiling and uploading is as easy as running the command:

`$ esphomeyaml wemos_1.yaml run`

### First-time flashing
The very first time you flash ESPHomelib firmware you have to connect the device via USB.
Subsequent firmware uploads can be done via the network as well. If the device is in the same network it will be discovered automatically, otherwise it's IP address has to be specified.
