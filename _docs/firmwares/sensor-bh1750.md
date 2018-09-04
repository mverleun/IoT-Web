---
title: Sensor BH1750 (Lightsensor)
permalink: /docs/sensor-bh1750/
---
## Homie based firmware

Ready to use firmware is available for download at the [releases](https://github.com/mverleun/IoT-devices/releases) page.
The sourcecode is available [here](https://github.com/mverleun/IoT-devices). 

If you study the code then you'll notice that only when a value changes a MQTT message is sent. It is not done at fixed intervals!

> The text below is directly imported from the github project page. It is the same as the README.md document found there.

<!-- load remote readme file from github -->
{% remote_markdown https://raw.githubusercontent.com/mverleun/IoT-devices/master/Sensor-BH1750/README.md %}

## ESPHomelib based firmware

In order to get the same behaviour with this firmware as you would get with the homie based firmware the configuration file has to be extended a bit. 
Without these extensions the firmware would only send a MQTT update after 15 sensor readings of which the average is calculated. 
This is basically a fixed interval.

```
esphomeyaml:
  name: wemos_1
  platform: ESP8266
  board: d1_mini

wifi:
  ssid: '<SSID>'
  password: '<PASSWORD>'

mqtt:
  broker: '<mqtt.example.com>'
  port: 1883
  # username: '<mqtt_user>'
  # password: '<mqtt_password>'
  # Start all MQTT published topics with the following prefix, make sure there is no trailing /
  topic_prefix: 'devices/wemos_1'

# Enable logging
logger:

ota:
  password: '<OTAPASSWORD>'

# The BH1750 sensor is an I2C sensor, so first prepare the 
# controller to talk to I2C sensors!
i2c:
  sda: D1
  scl: D2
  scan: False
  
sensor:
  # Wifi is a builtin sensor
  - platform: wifi_signal
    name: "WiFi Signal Sensor"
    update_interval: 10s
  # The BH1750 sensor by default uses I2C address 0X23
  # Every 1 second a new sample is taken
  - platform: bh1750
    address: 0x23
    update_interval: 1s
    name: "Brightness"
    filters:
      - filter_nan:
      - sliding_window_moving_average:
          window_size: 1
          send_every: 1
      - unique:

```

Let's look at this in a bit more detail:
`update_interval` tells the device to sample the environment every second. This sample is fed into the `filters` section. `filter_nan` removes samples where an invalid reading has been done. The `sliding_window_moving_average` part tells that no averages have to be calculated and that every calculated value has to be sent via MQTT.
This would result in a value being published every second, even if the value hasn't changed since the previous publication. This would flood the MQTT broker...

This is where `unique` comes into play. Only if a value has changed it is processed! So the MQTT broker is not flooded with messages!

In a real world you probably want to increase the window_size and average out a couple of samples.

Once you've got the file type `esphomeyaml wemos_1.yaml run` and watch the show:

```
INFO [esphomeyaml.config] Reading configuration...
INFO [esphomeyaml.__main__] Generating C++ source...
INFO [esphomeyaml.__main__] Compiling app...
INFO [esphomeyaml.__main__] Running:  platformio run -d wemos_1
*****************************************************************************************************************************
Obsolete PIO Core v3.6.0 is used (previous was 3.6.1a1)
Please remove multiple PIO Cores from a system:
http://docs.platformio.org/page/faq.html#multiple-pio-cores-in-a-system
*****************************************************************************************************************************
Processing wemos_1 (platform: espressif8266; board: d1_mini; framework: arduino)
-----------------------------------------------------------------------------------------------------------------------------
LibraryManager: Installing esphomelib
...
... Many lines omitted
...
Linking .pioenvs/wemos_1/firmware.elf
Retrieving maximum program size .pioenvs/wemos_1/firmware.elf
Checking size .pioenvs/wemos_1/firmware.elf
Building .pioenvs/wemos_1/firmware.bin
Memory Usage -> http://bit.ly/pio-memory-usage
Memory Usage -> http://bit.ly/pio-memory-usage
DATA:    [=====     ]  47.3% (used 38748 bytes from 81920 bytes)
PROGRAM: [===       ]  33.5% (used 350291 bytes from 1044464 bytes)
=============================================== [SUCCESS] Took 34.12 seconds ===============================================
INFO [esphomeyaml.__main__] Successfully compiled program.
INFO [esphomeyaml.__main__] Uploading binary...
INFO [esphomeyaml.espota] Starting on 0.0.0.0:39548
INFO [esphomeyaml.espota] Upload size: 354432
INFO [esphomeyaml.espota] Sending invitation to wemos_1.local 

INFO [esphomeyaml.espota] Authenticating...
INFO [esphomeyaml.espota] OK
INFO [esphomeyaml.espota] Waiting for device...
Uploading: [============================================================] 100% Done...

INFO [esphomeyaml.espota] Waiting for result...
INFO [esphomeyaml.espota] Result: OK
INFO [esphomeyaml.__main__] Successfully uploaded program.
INFO [esphomeyaml.mqtt] Starting log output from devices/wemos_1/debug
[20:28:10][I][mqtt.client:132]: MQTT Connected!
[20:28:10][C][sensor.bh1750:031]: Setting up BS1750...
[20:28:10][C][sensor.bh1750:032]:     Address: 0x23
[20:28:10][C][sensor.bh1750:047]:     Resolution: 0.5
[20:28:10][C][component:239]:     Update interval: 1000ms
[20:28:10][C][component:239]:     Update interval: 10000ms
[20:28:10][C][sensor.mqtt:025]: Setting up MQTT Sensor 'Brightness'...
[20:28:10][C][sensor.mqtt:027]:     Expire After: 3s
[20:28:10][C][sensor.mqtt:029]:     Unit of Measurement: 'lx'
[20:28:10][C][sensor.mqtt:030]:     Accuracy Decimals: 1
[20:28:10][C][sensor.mqtt:031]:     Icon: 'mdi:brightness-5'
[20:28:10][C][sensor.mqtt:025]: Setting up MQTT Sensor 'WiFi Signal Sensor'...
[20:28:10][C][sensor.mqtt:027]:     Expire After: 450s
[20:28:10][C][sensor.mqtt:029]:     Unit of Measurement: 'dB'
[20:28:10][C][sensor.mqtt:030]:     Accuracy Decimals: 0
[20:28:10][C][sensor.mqtt:031]:     Icon: 'mdi:wifi'
[20:28:10][C][sensor.mqtt:033]:     Unique ID: 'dc4f221d8b7a-wifisignal'
[20:28:10][I][application:090]: Running through first loop()
[20:28:10][D][sensor.mqtt:091]: 'WiFi Signal Sensor': Pushing out value -57.000000 with 0 decimals of accuracy
[20:28:10][I][application:106]: First loop finished successfully!
[20:28:10][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:10][D][sensor.mqtt:091]: 'Brightness': Pushing out value 0.000000 with 1 decimals of accuracy
[20:28:11][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:12][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:13][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:14][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:15][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:16][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx
[20:28:17][D][sensor.bh1750:091]: 'Brightness': Got illuminance=0.0lx

```

As you can see the firmware is uploaded automatically and there is also logging on the screen to show what is actually happening!

Much easier than the homie framework wouldn't you agree?
