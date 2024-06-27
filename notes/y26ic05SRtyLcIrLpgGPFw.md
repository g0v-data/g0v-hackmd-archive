---
title: 'Project documentation template'
disqus: hackmd
---

IoT tutorial
===
> By Reem Othman [student ID. ro222it]


## Table of Contents

[TOC]

Project description
---

This project is built to measure the user's heart rate using a **KY-039 Heart Rate** Sensor connected to a Raspberry Pi Pico W. We will use microPython to calculate the heart rate data from the sensor and send it to Adafruit IO for visualization. The online table on Adafruit IO shows the user's heart rate on the y-axis and the time of measurement on the x-axis. Adafruit IO also sends a webhook to a specified Discord server if the user's heart rate exceeds a certain value.

The estimated time to build this prototype is 2-5 hours. This time can vary based on your familiarity with the software and hardware.

Objective
---
The objective of this project is to build a device that helps users become more aware of how their heart rate changes while doing office work. Personally, I find this useful because I consume large amounts of caffeine while working on my computer or studying. Additionally, as a student, I often experience a lot of stress during exam seasons, which causes my heart rate to increase drastically. By using this simple prototype, I can monitor my heart rate and receive a webhook on Discord to take a break or do something else to reduce stress and regulate my heartbeat. Since it can be costly to buy a watch to measure my heart rate, it can be more efficient to build a similar device at home. The device can inform you of your heart rate in two ways:

1. By holding the sensor periodically to see your heart rate on the Adafruit table.
2. By improvising and making this simple device into a wearable device (such as a bracelet).

In this tutorial, I will provide you with the information you need to build the device in either way.


List of material
---
First of all, you need to have a computer and the following list of electronic materials:
| Item | Link | Price |
| -------- | -------- | -------- |
| Raspberry Pi Pico W | [Link](https://www.electrokit.com/en/product/raspberry-pi-pico-w/)| 89 SEK|
|   KY-039  | [Link](https://www.electrokit.com/en/pulssensor-ir)     | 36 SEK    |
| Breadboard     | [Link](https://www.electrokit.com/produkt/kopplingsdack-840-anslutningar/) | 69 SEK |
| Jumper wires 40-pin 30cm female/male      | [Link](https://www.electrokit.com/labbsladd-40-pin-30cm-hona/hane?gad_source=1&gclid=CjwKCAjw1emzBhB8EiwAHwZZxceRuC9RwYzFA_ldIs5yNkUaIQre0qvsQuFrd7gUekDZWThxJi9e7BoCkdAQAvD_BwE)     | 49 SEK     |    |
| Jumper wires 20-pin 30cm male/male       | [Link](https://www.electrokit.com/en/labbsladd-20-pin-15cm-hane/hane)     | 29 SEK     |    |
| USB-cable A-male – mini B male 1.8m 5-pin     | [Link](https://www.electrokit.com/en/product/usb-cable-a-male-mini-b-male-1-8m-5-pin/)     | 35 SEK     |
-| -| **Total 307 SEK**|

You need the Raspberry Pi Pico W to secure a power source for your sensor and to process the data from the sensor (KY-039, which will measure your heart rate) and send it to your computer. The breadboard is necessary to connect the sensor with the microcontroller (Raspberry Pi Pico W) using the jumpers. Lastly, you will use the USB cable to connect the Raspberry Pi Pico W to your computer.


Other materials that can be found in any household (note: if you have three female/female jumper wires, then you only need a hair band):

1. A pair of scissors
2. Tape
3. Any hair band you can find




Software
---

The followoing section mentions the software that you will need and what they are used for and their respektive links to download them for free.

* [Visual Studio code](https://code.visualstudio.com/)

First of all you need to have an idetor to write your code. In this totoriel we will use Visual Studio code (VSCode), you can use any editor of choice as long as it has the plugin we will use.

* [PyMakr](https://hackmd.io/@lnu-iot/rkiTJj8O9#Windows-OS)

The PayMakr plugin you can install it as an extention on VSCode, it is used to develop using MicroPython (Which is a virsion of python deticated for programming microcontroller). 

* [Node.js ](https://nodejs.org/en)

Node.js is a framwork that you can use to run JavaScript on your machine envirunment. But we are not goin to use it for that perpose, we only need it so that the PayMakr will work.

Before we move to the naxt section you will need to update the MicroPython firmware by following the steps below.

1. Download the latest MicroPython firmware [here](https://micropython.org/download/rp2-pico-w/) version.
2. Use the smaller end of the USB cable to plug it in the microcontroller (Raspberry Pi Pico W).
3. Hold the BOOTSEL botton (a small white button) on the microcontroller and connect the other end of the USB cable with your computer while holdin the button, the you can realse the button.
4. Now if you open your file system ther should be a spesific storage called RPI-RP2 which is meant to be for the Raspberry Pi Pico W. You will move the uf2 file to that storage.
5. Your board will automaticly disconnect and reconnect. If it does that then you are good to move to the next section.



Uploading code
---

Start with opening VSCode and installing PyMakr from the extentions
by following the stepes illustreted bellow

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_f0d7af46a0d30fcd84ad5de3d8eab997.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719425011&Signature=eXqqCya3R2rCU2LUaISjx9ZItJs%3D)
> Credits: Applied IOT LNU
> 

Then you can connect your microcontroller via the PyMakr. Click the PyMakr icone, your microcontroller should be viwed in the DEVICES section you can click the electricity symbol asocited with you microcontroller then you device will strat. Then you can click the terminal symple to open a new terminal, that terminal also is asocieted with your microcontroller and will previde you some information about the Raspberry Pi Pico W such as the virsion you can also print a string as illustrated in the picture bellow.

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_5cd6f572d0e701bec989086bcd08decc.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719426383&Signature=Zf2hgGch%2F%2FC69geIp7etWvnS0xU%3D)
> Credits: Applied IOT LNU
> 

Now you should be able to create your first project 

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_2ddf837a072e008be3c17010c7b3dae0.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719426383&Signature=XmX2RRnb6k9VuPBO6SarmeNk0N4%3D)

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_e0a1ffc1ca631037ade2a818426e9891.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719426383&Signature=LIaEBmoFi3Ou7kJDXEXVuRZjjAs%3D)

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_07270381e4a011cb6811483ae9184076.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719426383&Signature=vibFFZYvbOhrF%2FPdJTOemVGJgnM%3D)

![](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_0253b59a3537cb47f1779aba21c20e19.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1719426383&Signature=Tsdiigr5FJz9efc4wWcw8sFa1Y8%3D)

> Credits: Applied IOT LNU
> 

Putting everything together
---
Now we need to have our environment running and in order to do that we need to build an   electronic circuit. To build that we will use the matirials in the material list, mainly the raspbery pi pico, the ky-039 sensor, two male/male jumpers, three female/male jummpers and the breadbord. It worth noting that the illustration below only shows how to connect the electronic compnents to the breadboard without connecting the microcontrollers body to the bredboard and that is because we are going to use the microcontroller and the sensor on their on later. 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_172189784e7e6bdd8b0f62352481a7bc.png)

1. As illustrated in the image above you will connect the sensor to the breadboard by placing its three pins in the breadbord between the points 42-44.
2. Once done you will use a female/male jummper to connect the pin noted with S to the pin number 32 on you microcontroller, which an ADC pin that stands for analoge to digital convertion. Because our sensor registers analog signals we need to convert these signals to digital signals so that the computer can understand it and make use of it, and thats posible thanks to the ADC pins on the microcontriller.
3. Use two male/male jumpers to connect the the midel pin ans


###### tags: `Templates` `Documentation`
