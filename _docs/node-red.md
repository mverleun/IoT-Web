---
title: Node RED
permalink: /docs/node-red/
---
[Node RED](https://nodered.org) is installed on a Rasberry Pi by default.
It makes it easy to design flows such as this one:
![](/img/Node-RED/Node-RED___node-red_marcoach_nl.png)

# Creating the flow
This node consists of two input nodes and two output nodes. The input nodes are labeled 'inject' and 'mqtt', the output nodes are labeled 'debug' and 'mqtt'.
Locate them on the left side, drag them into the flow and connect them as shown.
The blue circles indicate that the flow is not deployed yet, the red triangles are indicators that these nodes require configuration.

# Configuring the nodes
Double click on one of the 'mqtt' nodes and you'll see the configuration screen. You'll see a screen like this: ![](/img/Node-RED/Node-RED__mqtt-node.png)

Use the pencil on the right to configure which mqtt broker you'll be using. To start just enter the IP address of the mqtt broker and leave all other settings as they are.

The next thing to do is to enter a topic. We'll use the topic 'mqtt/message'. Leave all other settings as they are. When your done, click on 'Done'

Repeat these steps for the other mqtt node as well.

When you done you've got a mqtt node that subscribes to the topic 'mqtt/message' and one that publishes to this topic.

# Deploying the nodes
By now the red triangles should have disappeared, but the blue circles are still there. It's time to deploy the flow which will activate the nodes.
Click on 'Deploy' in the upper right corner. If everything is configured well you'll see a small green circle underneath the mqtt nodes indicating that these nodes are connected to the mqtt broker.

# Testing the MQTT broker
On the right side select the 'debug' tab to activate this. Any information received by the debug node will be shown here.
The input node has not received anything yet to pass on to the debug node, so for the time being there's nothing to display.

Click on the pad which is on the left of the inject node (labeled timestamp) to inject the current date and time into the mqtt output node.

The actual date and time will be published on the topic 'mqtt/messsage' by the mqtt output node.
As soon as the message is received by the broker it will send the received information to the mqtt input node.
In turn this one will forward it to the debug node. If all goes well you should see the current date and time in the debug area of Node RED.

Congratulations, you've got a working MQTT broker.

Note that you didn't have to configure anything on the MQTT broker. Since no authentication is required and no ACL's are configured you can freely publish on any topic.

The next step is to connect sensors and actuators to the broker establish a communication path between them.

Keep in mind that with the current setup more than one client can publish information to the same topic. At the same time, more than one client can subscribe to the same topic simultaneous.