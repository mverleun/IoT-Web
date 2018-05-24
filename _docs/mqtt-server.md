---
title: MQTT Server
permalink: /docs/mqtt-server/
---
I use [Mosquitto](https://mosquitto.org) but any other MQTT server will do. If you want to, you can use a public MQTT broker on the internet, but I advise against it.

In production you want to secure the communication with the MQTT broker with SSL, but in a learning environment this could add an additional layer of complexity that is undesired.
The same goes for ACL's (Access Control Lists) that determine who can subscribe and/or publish to which topics.

If you perform a default installation of Mosquitto on a Raspberry Pi (yes, its more than powerfull enough) it will work out of the box without ACL's and without SSL.

In a controlled environment this is a good start for students to work on their understanding of the MQTT protocol.
They will realize soon the value that ACL's provide and probably will ask for them(https://mosquitto.org) but any other MQTT server will do. If you want to, you can use a public MQTT broker on the internet, but I advise against it.

In production you want to secure the communication with the MQTT broker with SSL, but in a learning environment this could add an additional layer of complexity that is undesired.
The same goes for ACL's (Access Control Lists) that determine who can subscribe and/or publish to which topics.

If you perform a default installation of Mosquitto on a Raspberry Pi (yes, its more than powerfull enough) it will work out of the box without ACL's and without SSL.

In a controlled environment this is a good start for students to work on their understanding of the MQTT protocol.
They will realize soon the value that ACL's provide and probably will ask for them.
