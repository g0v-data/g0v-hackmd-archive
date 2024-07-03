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

The following section mentions the software that you will need, what they are used for, and their respective links to download them for free.

* [Visual Studio code](https://code.visualstudio.com/)

First of all, you need to have an editor to write your code. In this tutorial, we will use Visual Studio Code (VSCode). You can use any editor of your choice as long as it supports the plugin we will use.

* [PyMakr](https://hackmd.io/@lnu-iot/rkiTJj8O9#Windows-OS)

The PyMakr plugin can be installed as an extension in VSCode. It is used to develop using MicroPython (which is a version of Python dedicated to programming microcontrollers).

* [Node.js ](https://nodejs.org/en)

Node.js is a framework that allows you to run JavaScript in your machine environment. However, we are not going to use it for that purpose; we only need it so that PyMakr will work.

Before we move to the next section, you will need to update the MicroPython firmware by following the steps below:

1. Download the latest MicroPython firmware version [here](https://micropython.org/download/rp2-pico-w/) version.
2. Use the smaller end of the USB cable to plug it into the microcontroller (Raspberry Pi Pico W).
3. Hold the BOOTSEL button (a small white button) on the microcontroller and connect the other end of the USB cable to your computer while holding the button. Then you can release the button.
4. Now, if you open your file system, there should be a specific storage called RPI-RP2, which is meant for the Raspberry Pi Pico W. Move the UF2 file to that storage.
5. Your board will automatically disconnect and reconnect. If it does that, then you are ready to move to the next section.



Uploading code
---

Start by opening VSCode and installing PyMakr from the extensions by following the steps illustrated below.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2342ec9ccbaea84579483e28fb03c69d.png)

> Credits: Applied IOT LNU
> 

Then, you can connect your microcontroller via PyMakr. Click the PyMakr icon; your microcontroller should be viewed in the DEVICES section. Click the electricity symbol associated with your microcontroller to start the device. Then, click the terminal symbol to open a new terminal. This terminal is associated with your microcontroller and will provide you with some information about the Raspberry Pi Pico W, such as the version. You can also print a string, as illustrated in the picture below.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4737dba8249383f51d315e4d4e6efcdc.png)

> Credits: Applied IOT LNU
> 

Now you should be able to create your first project.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_cb03454354de9a79ebda27e779d641bb.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_389d753cbfcb5f152358c590279b800e.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fde1940c472bd50162fa60644daa4565.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_135da1c0fd031bcabc1f195aee5e9e8b.png)

> Credits: Applied IOT LNU
> 

Putting everything together
---
Now we need to have our environment running, and in order to do that, we need to build an electronic circuit. To build that, we will use the materials in the materials list: mainly the Raspberry Pi Pico, the KY-039 sensor, two male/male jumpers, three female/male jumpers, and the breadboard. It is worth noting that the illustration below only shows how to connect the electronic components to the breadboard without connecting the microcontroller's body to the breadboard because we will use the microcontroller and the sensor on their own later. 
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_172189784e7e6bdd8b0f62352481a7bc.png)

1. As illustrated in the image above, connect the sensor to the breadboard by placing its three pins in the breadboard between points 42-44.
2. Use a female/male jumper to connect the pin labeled "S" on the sensor to pin number 32 on your microcontroller, which is an ADC pin (Analog to Digital Conversion). Our sensor registers analog signals, so we need to convert these signals to digital signals for the computer to understand and use. This is made possible by the ADC pins on the microcontroller.
3. Use one male/male jumper to connect the middle pin (the VCC pin of the sensor) to the positive row on the breadboard. Then, use a female/male jumper (of the same color if available) to connect that point on the positive row to pin number 36 (3V3 OUT) on the microcontroller. This pin supplies the connected components with a 3.3V output power, providing the sensor with the power it needs to function. 
4. Repeat the same process for the pin labeled "-" (GND) on the sensor to connect it to the negative row on the breadboard, and then connect it to pin number 38 (Ground) on the microcontroller. This is necessary to complete our electrical circuit.


If you want to build this circuit separately without the breadboard, you can follow the steps below:

1. You will need three female/female wires. If you don’t have them, we can improvise and make our own. For that, you need six female/male wires.
2. Use a pair of scissors to cut the wires in the middle so that the ends are equally long; we will only need the female ends.
3. Carefully remove the plastic part of the ends to reveal the copper part.
4. Connect the copper parts of two female ends to create a female/female wire, then tape it. Repeat this process three times to create three female/female wires. The image below illustrates how it is done.
5. Use the wires you improvised to connect the sensor's pins to the respective pins on the microcontroller. This way, you will have your prototype working and running exactly the same way as with the breadboard.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9dd0437eadaa396af0bf43aba53fda0f.png)

Platform Choice
---

For this IoT project, the platform used is Adafruit IO. Adafruit IO is a cloud-based platform, so you do not need to set up a local server. It simplifies the process of managing data from IoT devices and has an easy-to-use interface for visualizing data and creating dashboards, which makes it a great choice for beginners. These features are available in the free tier.

Adafruit offers several options for notifications. In this project, a webhook is triggered to send the heart rate when it exceeds 30BPM (that is quite low change it later to a more reasonable value e.g. 60-80).

The code
---
The code used to run this project is written in MicroPython. In your project folder, you should have a main.py file. If you don't, you can create one yourself. In this file, you will first write the code to import the following libraries and components.
```Python=
import network
from mqtt import MQTTClient
import ubinascii
import machine
import micropython 
import utime
```
Then, you need to connect to your WiFi and Adafruit MQTT server. But first, we need to create variables to serve that purpose, then we can connect to WiFi and set up the MQTT client.
```Python=
# WiFi and Adafruit IO credentials
wifi_ssid = 'Your wifi name'
wifi_password = 'you wifi password'
AIO_SERVER = "io.adafruit.com"
AIO_PORT = 1883
AIO_USER = "Your username in Adafruite"
AIO_KEY = "Aktive key"
AIO_FEED = "The name of your feed"
```
The WiFi Connection:
```Python=
# Function to connect to WiFi
def connect_wifi():
    wlan = network.WLAN(network.STA_IF)
    wlan.active(True)
    wlan.connect(wifi_ssid, wifi_password)
    while not wlan.isconnected():
        pass
    print("Connected to WiFi")
    return wlan.ifconfig()
```

Now we need to set up our MQTT client to pass the heart rate data to the feed we will create on Adafruit IO. We will also define the ADC pin of the Raspberry Pi Pico connected to the heart rate sensor (KY-039).
```Python=
# Function to set up MQTT client
def setup_mqtt():
    client = MQTTClient(ubinascii.hexlify(machine.unique_id()), AIO_SERVER, port=AIO_PORT, user=AIO_USER, password=AIO_KEY)
    client.connect()
    return client
    adc = machine.ADC(27)
```
Now that we have our MQTT client set up and a reference to the ADC pin, we can begin with the logic to convert the analog value and calculate the heart rate in BPM (beats per minute).
```Python=
def calculate_heart_rate():
    threshold = 4500  # Threshold to detect a heartbeat
    heartbeats = 0
    measurement_time = 12 # Measure for 12 seconds
    start_time = utime.time()

    while utime.time() - start_time < measurement_time:
        analog_value = adc.read_u16()  # Reads the analog value (0-65535)
        if analog_value > threshold:
            heartbeats += 1
            utime.sleep_ms(800)  # Increased debounce delay
    print("Analog Value:", analog_value)
    heart_rate = (heartbeats * 60) / measurement_time
    return heart_rate
```
We will now use our MQTT client and the value returned from the calculate_heart_rate() function to publish real-time data to Adafruit IO. To do this, we will need to define the following function.
```Python=
def send_data(client, value):
    client.publish(topic=AIO_USER + "/feeds/" + AIO_FEED, msg=str(value))
```
Last but not least, we need a starting point to run this code, which is done through the main() function. This function connects to WiFi, initiates setup_mqtt, and calls both calculate_heart_rate() and send_data().
```Python=
def main():
    connect_wifi()
    client = setup_mqtt()
    
while True:
        heart_rate = calculate_heart_rate()
        print("Heart Rate: {:.2f} BPM".format(heart_rate))
        send_data(client, heart_rate)
        utime.sleep(10)  # Wait 10 seconds before next measurement

# Run the main function
main()

```
Before we move on to the next part, you will need to create another file in the same folder where you have your main.py. Name the new file mqtt.py (this will represent the MQTT library). In that file, paste the content you find in this [link](https://github.com/iot-lnu/pico-w/blob/main/network-examples/N2_WiFi_MQTT_Webhook_Adafruit/lib/mqtt.py).

Transmitting the data
---
The heart rate data is transmitted to Adafruit IO every 10 seconds. The wireless protocol used to carry out the transmission is a **WiFi** network by using the provided SSID and password. The transport protocol to publish the calculated heart rate data to a specified feed on Adafruit IO is **MQTT (Message Queuing Telemetry Transport)**, which allows real-time data to be visualized.

Presenting the data
---
To present the data on Adafruit IO, you should have an account there. Follow the steps below to create your feed and dashboard. One more important thing is that there are some variables in the code that should have their values copied from different steps, so be careful not to leave any of the variables empty.

1.Navigate to Feeds, then click on the “New Feed” button to create a new feed. You can give it a name and a description of your choice. In my case, I named my feed "Heart Rate."
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_145fc984e81d9a433813eeaf0dba57b6.png)

2. Navigate to Dashboards and create a new dashboard in the same way you created the feed. I already have one named "HR."
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0e536878058a3189d31aac5692fdc69a.png)

3. Once you create the dashboard, click on it. When it opens, it will be empty. Click on the settings symbol, then on "Create New Block" as illustrated below, and choose the "Line Chart" as a block. Then, check the feed that you want to connect the block to, which is the feed you created in the previous step.

4. Next, click the key icon on the top right to copy your username and the Active Key. Paste these into your code in the variables for username and Active Key.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2e77964636051e5bb9c8fc3799a417ba.png)


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_277f9526c38fd08e24edd7e1d04f0c2f.png)

Lastly, the code provided will automatically format an address to your feed based on your username and the feed name. This is why you will not need to copy and paste the MQTT key into your code.

Webhook
---
In this part, you will connect your feed to an action to send webhooks to a Discord server.


1. First, start by creating a server on Discord. In the left pane, click on the "+" sign to create a new server, then choose >>"Create My Own" and select >>"For me and my friends." Give the server a name of your choice.
2. Click on the settings icon. 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9e867864a98d4265c5227c83505ed295.png)
> Credits: Applied IOT LNU
> 

3. Choose "Integrations" from the settings list, then create a webhook.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_febd2efb0b7bf0594a1ecd5e3c21749a.png)
> Credits: Applied IOT LNU
> 

4. Copy the URL associated with the webhook.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66532e1fed73dbff059ef9e9c09a27be.png)
> Credits: Applied IOT LNU
> 

Now you need to create an action and connect the webhook with it.

1. In Adafruit IO, navigate to Actions, then click on the "New Action" button to create an action.
2.  Click “No, use the form.” In the next window, choose “Reactive.”
3.  Lastly, fill in the input fields with the information needed to connect the action with the feed and the webhook, as shown below. The Webhook URL that you copied from Discord should be pasted in the field marked with orange.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b3688e40172e71a8974f00ce26b584a1.png)

Finalizing the design
---

The final hardware design should look something like one of the last two pictures below, and the dashboard block should look like the first picture. You may wonder why the heart rate is illustrated above 190 BPM; that is because I modified the code at the beginning to calculate the heart rate higher than what it actually is. But that was just an experimental thing, which means you wouldn’t have to do that.

As mentioned earlier, you can build this project in two ways. The first way will give results similar to the second picture, and the second way will give you results similar to the third picture. In both approaches, make sure that the correct side of the sensor is in contact with your skin (the side with the small dot).

Overall, I like how the result turned out. However, something I could have done better was probably having female/female wires to avoid making them myself and spending that time to improve something else in the project. But in the beginning, I didn’t expect that I would need them, so I didn’t order any with the starter kit.


![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_d32b25253a4b4bc4012c574cf897848a.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_27f556e2774b3a8019060ce35f2ed2a5.jpg)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ed47af2627e9564dcff4e1270308f2f9.jpg)


