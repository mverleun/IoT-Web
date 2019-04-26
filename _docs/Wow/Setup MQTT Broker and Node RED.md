[Main document](README.md)
# Setting up a MQTT Broker and Node RED

The easiest MQTT broker to setup is Mosquitto. 
Mosquitto can be run inside a Docker container but a native installation is also possible.

To simplify the setup a script is provided to make the setup easy. This scripts are ment to run on a Raspberry Pi with a fresh installation of Raspbian.


* Login as the user `pi` on a Raspberry Pi with a fresh installation of Raspbian. 
* Open a terminal session
* Enter the following commands:

```bash
git clone https://github.com/mverleun/Wow
cd Wow
./setup.sh
```

This will install Mosquitto, Node RED and some additional nodes for Node RED.hb[
It will also install a default flow for Node RED that will connect to the locally running MQTT broker.

At the end it will display the IP address of the system. This information is needed to configure the Owntracks apps on the smartphones. 

[Main document](README.md)
