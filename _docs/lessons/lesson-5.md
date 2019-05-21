---
permalink: /docs/lesson-5/
title: "Lesson 5: Building a dashboard"
---

# Objectives
- Create a dashboard using Node RED
- Use PubSub mechanism to work with actual status

# Create a dashboard
Before we continue make sure that you have completed lesson 4. Especially the last part where you started to work on the I2C node.

In lesson 4 we learned how to read information from a sensor and this information was made visible using a debug node.
This time we will transmit the information to a mqtt broker. In order to be able to distinguish the information you'll have to use a unique topic on which you publish the information.

In the next examples I'll be using the number 17. This number can be replaced by any other number, as long as it is unique. Check with other students who will be using which number.

Replace the debug node from lesson 4 with two other nodes. The first one is the rbe node, the second one is the mqtt output node.

Configure to output node to publish to topic `sensors/node-17` where you replace 17 with your own number. 

![](/img/lessons/lesson-5/flow.png)

Deploy this flow and your readings are send to the mqtt broker.

Create a new flow by clicking on the plus '+' symbol.
On the left side select a mqtt input node and connect it to a gauge. Use the filter to search for them.

The settings of the mqtt input node are as follows: 

- Server: mqtt.iot-kit.nl
- Topic: sensors/node-17 (Replace 17 with your number)

The gauge requires a bit of work to get it up and running, but it is worth it.

Double click on the gauge which opens the following screen:
![](/img/lessons/lesson-5/gauge-1.png)

Click on the pencil behind Group to create a new group.
This will present you with the following screen:
![](/img/lessons/lesson-5/gauge-2.png)

Now you have to click on the pencil to create a tab:
![](/img/lessons/lesson-5/gauge-3.png)

If you want, you can change settings. But for now it is okay to click on 'Add' and 'Done' to get back to the flow editor.

If all is well you can go ahead and deploy the flow.
Open a second tab in the browser with the url http://localhost:1880/ui and press enter.
![](/img/lessons/lesson-5/browser.png)

You should see something like this:
![](/img/lessons/lesson-5/dashboard.png)

As you can see the scale is a bit off. Try to correct this yourself.
