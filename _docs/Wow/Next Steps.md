[Main document](README.md)
# Next Steps

Let's hope that the students now are keen to understand how things work. There are several topics worth investigating:

## The MQTT protocol itself. 
There are some good resources such as this [learning page from Sparkfun](https://learn.sparkfun.com/tutorials/introduction-to-mqtt/all) and [Steves Internet Guide](http://www.steves-internet-guide.com/mqtt/).

Maybe [Python programming](http://www.steves-internet-guide.com/python-mqtt-publish-subscribe/) is worth exploring?

## Securing Mosquitto
Securing the MQTT protocol is interesting as well. How it's done depends on the broker. In this setup Mosquitto is used.
ACL's are discussed here:[mosquitto.conf](https://mosquitto.org/man/mosquitto-conf-5.html)
SSL Security is discussed on many pages, such as this one which uses [Let's Encrypt](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-the-mosquitto-mqtt-messaging-broker-on-ubuntu-16-04), or this one using [Self signed certificates](https://dzone.com/articles/mqtt-security-securing-a-mosquitto-server)

## Diagnosing MQTT problems
There are many tools that you can use to diagnose MQTT. Well know tools include [mqtt-spy](https://github.com/eclipse/paho.mqtt-spy) and [MQTT Explorer](https://mqtt-explorer.com).

## Node RED
Has it's own page: [www.nodered.org](https://nodered.org).

## Docker
Both Mosquitto and Node RED can be run in Docker containers. The latest Raspberry Pi's are great to learn container basics and more. If you go all the way you can build your own cluster.
Check this [blog](https://blog.docker.com/2019/03/happy-pi-day-docker-raspberry-pi/) to get started.

## Linux
The more we discover, the closer we get to the OS (Raspbian) which is a Linux based OS.
Managing the Mosquitto and Node RED services requires knowledge about service managemet.

Updating the server requires OS knowledge and installing software as well.

A good definition of usefull (required?) skills for novices are defined by LPI with the [Linux Essentials](https://www.lpi.org/our-certifications/exam-010-objectives) exam as the proof of the pudding.

[Main document](README.md)
