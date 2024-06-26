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



Putting everything together
---

Start with opening VSCode and installing PyMakr from the extentions
by following the stepes illustreted bellow

![]



###### tags: `Templates` `Documentation`
