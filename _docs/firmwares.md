---
title: Firmwares
permalink: /docs/firmwares/
---
When looking for firmware don't forget to check the following projects: [sonoff/tasmota](https://github.com/arendst/Sonoff-Tasmota/tree/development/sonoff), [espeasy](https://www.letscontrolit.com/wiki/index.php/ESPEasy) and [espurna](https://bitbucket.org/xoseperez/espurna). 

They are universal firmwares that can do multiple things. Even though they're not difficult to use,
they all have their own mqtt topics, data formats und update procedures making them less intuitive.
Also their source code has grown over time, making it less easy to study it in a short time.

They may provide what you need, or can be used as inspiration for your own projects.

## Multiple firmwares
Instead of creating a great universal firmware that supports a multitude of shields this project consists of dedicated firmwares for a specific task.

If new shields are added it is easy to create the firmware because of the homie framework.

## Initital configuration of the firmware
When the device has enough storage capacity the configuration can be done easilty through a web browser. Each freshly flashed device will start as an accesspoint where you can connect to. 
Simply fill in the required information and the device is ready for use.

It is also possible to create a config file in JSON format and upload it to the device. An example file is provided in the directory `data/homie`. Rename `config.json.example` into `config.json` and modify the settings to match your configuration.

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
This is an example where MQTT authentication is required, which is recommended. If you don't want to use authentication you can use the following as a template:

```
{
  "wifi":{
    "ssid":"<Your SSID>",
    "password": "<Password>"
    },
  "mqtt":{
    "host":"<Your MQTT Server",
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
> The base_topic setting normally is `"homie/"`. Make sure to be consistent when changing the value to something else. 

Once the device is configured it is possible to change them via MQTT. Detailed configuration instructions can be found in the homie documentation. 


