# How to use XBee Modules As Transmitter & Receiver - Arduino Tutorial 

## Introduction: How to Use XBee Modules As Transmitter & Receiver - Arduino Tutorial 

https://www.instructables.com/How-to-Use-XBee-Modules-As-Transmitter-Receiver-Ar/



[![How to Use XBee Modules As Transmitter & Receiver - Arduino Tutorial](https://content.instructables.com/ORIG/F4R/5U97/ILWLB0CU/F4R5U97ILWLB0CU.jpg?auto=webp&frame=1&crop=3:2&width=600&height=1024&fit=bounds&md=30aa744f69e574af4aa0e543805f145f)](https://content.instructables.com/ORIG/F4R/5U97/ILWLB0CU/F4R5U97ILWLB0CU.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=30aa744f69e574af4aa0e543805f145f)

[![How to Use XBee Modules As Transmitter & Receiver - Arduino Tutorial](https://content.instructables.com/ORIG/FW8/DF3K/ILWLB0ED/FW8DF3KILWLB0ED.jpg?auto=webp&frame=1&crop=3:2&width=600&height=1024&fit=bounds&md=f9ce90da9307ce864a7db8b791a26f0c)](https://content.instructables.com/ORIG/FW8/DF3K/ILWLB0ED/FW8DF3KILWLB0ED.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=f9ce90da9307ce864a7db8b791a26f0c)

In this tutorial we will use two xBee (series 1) modules with the Arduino uno board. We will configure them to act as a receiver and transmitter to control the brightness of an LED wirelessly by using one potentiometer.

The xBee - series 1 - modules take the 802.15.4 stack (the basis for Zigbee) and wrap it into a simple to use serial command set. These modules allow a very reliable and simple communication between micro controllers, computers or other systems by using just a serial port! They can communicate up to 300 Ft (~100m), they have 2.4GHz frequency , use the 802.15.4 protocol and have data rate up to 250kbps. They have also a 1mW wire antenna on them. They supports Point to point and multi-point networks.

So, let's get started!



## Step 1: What You Will Need

[![What You Will Need](https://content.instructables.com/ORIG/FNS/PEYF/ILWLB0E6/FNSPEYFILWLB0E6.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=285b905902d29fc1102e36f5787e7515)](https://content.instructables.com/ORIG/FNS/PEYF/ILWLB0E6/FNSPEYFILWLB0E6.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=285b905902d29fc1102e36f5787e7515)

For this tutorial you will need:

- 2x Arduino uno boards
- 2x xBee series 1 modules
- 2x XBee Explorer Regulated boards
- XBee Explorer USB
- 220 Ohm resistor, led
- potentiometer (e.g. 2k)
- 2x breadboards
- some breadboard cables



## Step 2: XCTU - Setup Your XBee Modules

[![XCTU - Setup Your XBee Modules](https://content.instructables.com/ORIG/FKV/GAOA/ILWLB0CR/FKVGAOAILWLB0CR.png?auto=webp&frame=1&width=899&fit=bounds&md=01c1ddafc946e27cf136ee02ceccd10f)](https://content.instructables.com/ORIG/FKV/GAOA/ILWLB0CR/FKVGAOAILWLB0CR.png?auto=webp&frame=1&width=1024&fit=bounds&md=01c1ddafc946e27cf136ee02ceccd10f)

[![XCTU - Setup Your XBee Modules](https://content.instructables.com/ORIG/FDL/VOR6/ILWLB0CQ/FDLVOR6ILWLB0CQ.png?auto=webp&frame=1&width=301&fit=bounds&md=c7052441572191db217b730d1d1abee7)](https://content.instructables.com/ORIG/FDL/VOR6/ILWLB0CQ/FDLVOR6ILWLB0CQ.png?auto=webp&frame=1&width=1024&fit=bounds&md=c7052441572191db217b730d1d1abee7)

[![XCTU - Setup Your XBee Modules](https://content.instructables.com/ORIG/FM6/C1SX/ILWLB0E1/FM6C1SXILWLB0E1.jpg?auto=webp&frame=1&crop=3:2&width=301&height=1024&fit=bounds&md=9b4f6a93cc3db41fd3a818aad846207f)](https://content.instructables.com/ORIG/FM6/C1SX/ILWLB0E1/FM6C1SXILWLB0E1.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=9b4f6a93cc3db41fd3a818aad846207f)

[![XCTU - Setup Your XBee Modules](https://content.instructables.com/ORIG/F9L/I3ER/ILWLB89D/F9LI3ERILWLB89D.jpg?auto=webp&frame=1&crop=3:2&width=301&height=1024&fit=bounds&md=40384b15f301216e925b7b85756f55c5)](https://content.instructables.com/ORIG/F9L/I3ER/ILWLB89D/F9LI3ERILWLB89D.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=40384b15f301216e925b7b85756f55c5)

Download the XCTU software from [here](http://www.digi.com/products/xbee-rf-solutions/xctu-software/xctu).

Run the program and connect the XBee Explorer USB board with your computer. Click on the "Discover devices" icon to add your xBee in the XCTU software. 

Now click on it (first image above) and set the CH field to e.g. "C" and the ID field to e.g. "1001". These values must be the same to all xBee modules to communicate with each other. Now as this xBee will be our transmitter, set the CE field as "Coordinator". If the baud rate isn't set to 9600bps, change it to this value.

Now click the "Write" button to save the changes in your xBee module.

Disconnect the xBee explorer board from your computer and connect the other xBee module on it. 

Connect the explorer board with your computer again and follow the same procedure (second image above) but this time set the CE field as "End device". 

Finally the configuration for our xBees must be:

For xBee transmitter:

- CH: C
- ID: 1001
- CE: Coordinator
- Baud rate: 9600 bps

For xBee receiver:

- CH: C
- ID: 1001
- CE: End point
- Baund rate: 9600 bps

## Step 3: The Code

Here's the "xBee Transmitter" code, embedded using Codebender! Try downloading the Codebender [plugin ](https://codebender.cc/static/walkthrough/page/1)and clicking on the "Run on Arduino" button to program your Arduino board with this sketch. And that's it, you've programmed your Arduino uno board with this sketch!

And here's the "xbee Receiver" code, connect the second Arduino uno board with your computer and press the "Run on Arduino " button.

## Step 4: The Circuit

[![The Circuit](https://content.instructables.com/ORIG/FOX/KKGD/ILWLB657/FOXKKGDILWLB657.png?auto=webp&frame=1&crop=3:2&width=900&fit=bounds&md=e3c5d2fdd6f35809a2a64b6dcee66eae)](https://content.instructables.com/ORIG/FOX/KKGD/ILWLB657/FOXKKGDILWLB657.png?auto=webp&frame=1&width=1024&fit=bounds&md=e3c5d2fdd6f35809a2a64b6dcee66eae)

[![The Circuit](https://content.instructables.com/ORIG/FVW/VSO5/ILWLB64Q/FVWVSO5ILWLB64Q.png?auto=webp&frame=1&crop=3:2&width=300&fit=bounds&md=34c0d3f0d396023877f7bc41a27e70ce)](https://content.instructables.com/ORIG/FVW/VSO5/ILWLB64Q/FVWVSO5ILWLB64Q.png?auto=webp&frame=1&width=1024&fit=bounds&md=34c0d3f0d396023877f7bc41a27e70ce)

[![The Circuit](https://content.instructables.com/ORIG/F4D/F0BZ/ILWLB0E7/F4DF0BZILWLB0E7.jpg?auto=webp&frame=1&crop=3:2&width=300&height=1024&fit=bounds&md=4a9eb5737bebd30c850c52632283252b)](https://content.instructables.com/ORIG/F4D/F0BZ/ILWLB0E7/F4DF0BZILWLB0E7.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=4a9eb5737bebd30c850c52632283252b)

[![The Circuit](https://content.instructables.com/ORIG/F18/N7S2/ILWLB0E9/F18N7S2ILWLB0E9.jpg?auto=webp&frame=1&crop=3:2&width=300&height=1024&fit=bounds&md=ccaaa8e103d4c2c5f3d1db0fefdac2b1)](https://content.instructables.com/ORIG/F18/N7S2/ILWLB0E9/F18N7S2ILWLB0E9.jpg?auto=webp&frame=1&width=1024&height=1024&fit=bounds&md=ccaaa8e103d4c2c5f3d1db0fefdac2b1)

The connections are pretty easy, see the above image with the breadboard circuit schematics. Power on both Arduino uno boards and try to fade the led by turning the potentiometer. 



## Step 5: Well Done!

[![Well Done!](https://content.instructables.com/ORIG/FHQ/1YLR/ILWLB71O/FHQ1YLRILWLB71O.png?auto=webp&frame=1&width=1024&fit=bounds&md=8020ddc0a76893e7d3836d6001aebf04)](https://content.instructables.com/ORIG/FHQ/1YLR/ILWLB71O/FHQ1YLRILWLB71O.png?auto=webp&frame=1&width=1024&fit=bounds&md=8020ddc0a76893e7d3836d6001aebf04)

You have successfully completed one more "How to" tutorial and you learned how to fade an LED wirelessly by using the xBee S1 modules. 

