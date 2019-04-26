[Main document](README.md)
# Problem Solving

This demo is pretty 'foolproof'. But as we all know things can still go wrong.

The majority of the issues are probably related to typo's on the smartphones and other network issues.

Make sure that the smartphones can connect to port 1883, which is the MQTT port. Check the firewall and routers. 

* Sometimes smartphones connect to a guest network that is not allowed to reach the network on which the MQTT is configured.
* Check the logging of the MQTT broker. Open a terminal on the Raspberry Pi and type ```tail -f /var/log/mosquitto/mosquitto.log```. You should see messages indicating new connections are setup.
* A more difficult one to troubleshoot are clients which have the same id. Since MQTT clients can be mobile they can not be recognized with the IP address. This could change often. The only identifier that can be used is the client's name. This has to be unique. What could happen is that two students use their initials in the Owntracks configuration and they happen to share the same initials, e.g. Mark Williams and Marina Winter. This will result in seemingly random disconnects which are visible in the logfile.

[Main document](README.md)
