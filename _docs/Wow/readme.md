
# The power of Wow...

Learning Linux is encouraged by many vendors. Even Microsoft encourages students to learn Linux.

But learning Linux can be dull. There is a lot to learn, but the beginning is often not very inspiring.

In order to motivate students I believe in the Wow effect... Have students participate in a quick demonstration to trigger their eagerness to learn how it is done.

My favorite is to use an app on their smartphone called [Owntracks](https://owntracks.org). It's a free app available in [Google Play](https://play.google.com/store/apps/details?id=org.owntracks.android) and the [Apple Appstore](https://itunes.apple.com/us/app/mqttitude/id692424691). 
This app is able to send location information via the MQTT protocol to a MQTT broker (MQTT server). It also receives information from others connected to the same broker like shown below.

![](https://owntracks.org/booklet/guide/images/owntracks-iotconf-arch.png)

It's often a magical moment! On the smartphone they'll see a map revealing their location and the location of others: ![](https://owntracks.org/booklet/images/ipad-public-map.png) 

This wow effect can be avoided by using the proper access control settings of course, but hey, where is the fun in that?

Once you've got this up and running its time to discuss privacy and security. 
Things you could discuss are using a public MQTT broker versus a private one. Or the need to encrypt the connection using SSL.

The official documentation, which is quite extensive, can be found [here](https://owntracks.org/booklet/).

You can use a public MQTT broker or setup your own.
Public brokers are the least secure and may not always be available. You could use one of the following:

| Broker | Port|
| --- | --- |
| mqtt.iot-kit.nl | 1883 |
| broker.hivemq.com | 1883 |
| test.mosquitto.org | 1883 |
| iot.eclipse.org | 1883 |

When using a public broker you could also see the locations of others, anywhere around the world. ;-)

You could also setup your own and use that one. It's not difficult but you have to make sure that all students can reach your broker.

Just use one of the following guides to get things going:

* [Howto Setup your own server](Setup MQTT Broker and Node RED.md)
* Configure Owntracks on iOS device
* Configure Owntracks on Android device
* [Start the Demo](Start Demo.md)
* [Problem solving](Problem Solving.md) 
* [Next steps](Next Steps.md)


 

