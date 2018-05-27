---
title: Owntracks
permalink: /docs/owntracks/
---
Once you've got the MQTT broker and Node RED up and running you can use the following Node RED flow for a quick and easy success.

This flow subscribes to the topic `owntracks/<user>/<name smartphone>`, formats the received data and publishes the location of the smartphone on a worldmap.

Simply copy the JSON text and paste it in Node RED. You probably will have to install some additional nodes in Node RED to get the flow working.

```
[
    {
        "id": "d0f73e8c.17097",
        "type": "mqtt in",
        "z": "bd605c6a.b82258",
        "name": "MQTT Broker",
        "topic": "owntracks/<user>/<name smartphone>",
        "qos": "0",
        "broker": "2b5a558d.d91ea2",
        "x": 190,
        "y": 100,
        "wires": [
            [
                "47c512e0.37718c"
            ]
        ]
    },
    {
        "id": "47c512e0.37718c",
        "type": "owntracks",
        "z": "bd605c6a.b82258",
        "x": 427,
        "y": 99,
        "wires": [
            [
                "a141a421.8e3888"
            ]
        ]
    },
    {
        "id": "a141a421.8e3888",
        "type": "worldmap",
        "z": "bd605c6a.b82258",
        "name": "",
        "lat": "52.0263009",
        "lon": "5.5544309",
        "zoom": "",
        "layer": "OSM",
        "cluster": "",
        "maxage": "30",
        "x": 706,
        "y": 98,
        "wires": []
    },
    {
        "id": "2b5a558d.d91ea2",
        "type": "mqtt-broker",
        "z": "",
        "name": "MQTT Broker",
        "broker": "127.0.0.1",
        "port": "1883",
        "clientid": "",
        "usetls": false,
        "compatmode": true,
        "keepalive": "60",
        "cleansession": true,
        "willTopic": "",
        "willQos": "0",
        "willRetain": "false",
        "willPayload": "",
        "birthTopic": "",
        "birthQos": "0",
        "birthRetain": "false",
        "birthPayload": ""
    }
]
```
The next thing is to install an app with the name Owntracks from the Apple Appstore or from Google Play.
Configure it to use the same MQTT broker as where this flow is connecting to, enter a user name and an identier for the device.
If all is done well you should be able to track the locations of all the smartphones.
