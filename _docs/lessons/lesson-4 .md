---
permalink: /docs/lesson-4/
title: "Lesson 4: More Node RED"
---

# Objectives
- Understand a bit more about Node RED
- Install additional nodes

# Understanding Node RED
Node RED allows us to create workflows without programming. No coding skills are required (but they are allowed!).

Everything that happens is event driven. Node RED comes with quite some nodes, but there are many more nodes that you can download.

Let's explore a few nodes. 
A nice node is the 'delay' node. You can find it quick by using the search field in the upper left corner. ![](/img/lessons/lesson-4/delay-1.png)

Place the delay node between Switch 1 and LED 1 like shown in this picture and click Deploy.![](/img/lessons/lesson-4/delay-2.png)
As you would expect, everything is becoming a bit slow.

Another node, used frequently, is the inject node. It can be used as a trigger to start a flow.

If you want to do some coding you can use the node with the name function.

Extending the available nodes can be done using the command line. There is a huge catalog at [https://flows.nodered.org](https://flows.nodered.org/) Check it out and also read the instructions on how to install the nodes. Some have specific requirements!

An interesting node to install is the [worldmap](https://flows.nodered.org/node/node-red-contrib-web-worldmap) node. 

Another interesting one is this [dashboard](https://flows.nodered.org/node/node-red-dashboard) node. 

One that we do need is the I2C node to be able to read information from the light sensor.

Install these nodes now by entering the following commands:

```bash
cd ~/.node-red
npm install node-red-dashboard
npm install node-red-contrib-web-worldmap
npm install node-red-contrib-frequency-meter
npm install node-red-contrib-i2c

sudo systemctl restart nodered
```
You probably will have to refresh the content of the browser too.

## I2C node

This node requires some technical knowledge (or great Google skills). I2C is one of many techniques used by manufacturers to have components talk to each other.

Here we need the I2C node to be able to talk to a light sensor. 
Drag a 'I2C in' node into the editor and double click it. Fill in the following information:

- Address: 35
- Command: 16
- Bytes: 2


![](/img/lessons/lesson-4/i2c.png)
Activate this I2C node with a inject node that is set to trigger each second: 
![](/img/lessons/lesson-4/trigger.png)

The output from the I2C node is connected to a 'Change' node. The information is changed according to an expression which has to be filled in. ![](/img/lessons/lesson-4/change.png) The complete expression is:
```
$round((payload."1" + (256 * payload."0"))/1.2,2)
```
Complete this flow with a debug node: ![](/img/lessons/lesson-4/flow.png) and click on Deploy.

Next challenges:
- Replace the debug node with a MQTT ouput node.
- Only publish a new value if it is different from the previous one. (Hint: use RBE node)

## Manage palette
It is also possible to manage the installation of additional nodes via the GUI. See the following drop down menu: ![](/img/lessons/lesson-4/palette.png) 



