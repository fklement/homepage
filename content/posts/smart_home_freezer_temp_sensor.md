---
description: "Smart Home: Freezer temperature sensor! ❄️"
date: 2019-08-03T10:55:04+02:00
draft: false
tags:
  - Smart-Home
  - IoT
  - ESP8266
---

Lately we’ve had the problem that our freezer sometimes simply turns off. Which is of course not that great because our ice cream, and frozen pizzas were defrosted and obviously some other food as well.

![“A figurine of a stormtrooper under a desk lamp with an incandescent light bulb” by [James Pond](https://unsplash.com/@shotbyjamespond?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)](https://cdn-images-1.medium.com/max/12000/0*bfY-RyrbceXVo9OU.)*“A figurine of a stormtrooper under a desk lamp with an incandescent light bulb” by [James Pond](https://unsplash.com/@shotbyjamespond?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)*

So I decided to use IoT to develop some kind of early warning system when the temperature in our freezer will start to raise.

*Components i used for this project:*
-[ Raspberry PI 3 Modell B+ ](https://www.reichelt.de/?ARTICLE=217696&PROVID=2788&gclid=CjwKCAjwwuvWBRBZEiwALXqjw0soi13WDjrGDijPiIw-aWGf-aH7ML5nZ3KSk5xhuSI9IlroHuSmhxoC9boQAvD_BwE)(as our MQTT Broker and to run Node-RED)
- [ESP8266 NodeMCU](https://www.ebay.de/itm/NodeMCU-V3-Arduino-ESP8266-ESP-12-E-Lua-CH340-WiFI-WLan-IoT-Lolin-Mini-Micro/252718027546?hash=item3ad72b131a:g:nRoAAOSwYwJaD2tX) (to send the temperature data via the MQTT protocol)
- [DS18b20 ](https://www.ebay.de/itm/DE-Lager-Wassertemperaturf%C3%BChler-Temperatursensor-Sensor-DS18b20-wasserdicht/173231702870?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2060353.m2749.l2649)temperature sensor (for measuring the actual temperature in the freezer)

At first I took a breadboard and tested the temperature sensor in combination with the ESP8266. The DS18b20 sensor has 3 pins: red (VCC), yellow(DATA) and black(GND). I decided to connect the DATA-Pin to pin D7(GPIO13) on the ESP-Board, which is a normal I/O pin or for SPI data. 
All in all, it’s not very complicated to connect the DS18b20 to the ESP8266. Just have a look at the complete breadboard layout down below.

![Fritzing connection layout](https://cdn-images-1.medium.com/max/2000/1*R1mWadxk4eW08EkxXeoFyw.jpeg)*Fritzing connection layout*

The next step was to programm the ESP8266 so it is possible to receive the current temperature and send it via MQTT to our broker. I used the Arduino IDE to programm the microcontroller.

I used 4 different libraries:
- [ESP8266WiFi library](https://github.com/esp8266/Arduino/tree/master/doc/esp8266wifi) (for connecting the ESP with our local WiFi)
- [PubSubClient](https://github.com/knolleary/pubsubclient) (an arduino client for MQTT)
- [OneWire](https://github.com/PaulStoffregen/OneWire) (library for Dallas/Maxim 1-Wire chips)
- [DallasTemperature](https://github.com/milesburton/Arduino-Temperature-Control-Library) (arduino library for maxim temperature integrated circuits)

All we now have to do is connecting our ESP via WiFi to our local network so it can access our MQTT-Broker, which we’ll later run on our raspberry pi. Then we need to connect to our broker via the PubSubClient library. After this is all set up we can start to readout the temperature from the sensor and publish it to the MQTT topic “sensor/temperature”. It’s really no rocket science 🚀.
The complete documented code can be found in the [fridgy-temp](https://github.com/fklement/fridgy-temp) repo on my [github page](https://github.com/fklement).
[**fklement/fridgy-temp**
*fridgy-temp - ESP8266 with an DS18b20 temperature sensor*github.com](https://github.com/fklement/fridgy-temp)

The next step now is to setup the raspberry pi. I installed [mosquitto ](https://mosquitto.org/)and configurated everything. A good tutorial for installing mosquitto with a quick intro into MQTT can be found [here](http://www.switchdoc.com/2016/02/tutorial-installing-and-testing-mosquitto-mqtt-on-raspberry-pi/) 👈.

Afterwards I set-up Node-RED, which is a flow-based development tool. I decided to go for this plattform because it allows you to easily setup your IoT-Service. You can simply wire all your devices and needed tools visually together and have the ability to provide a cool dashboard. Of course you can do much more but, for our application purpose this is all we need. A currated list of features and a getting started guide can be found in the [docs](https://nodered.org/docs/). 📚

Our freezer has a standard temperature around -21/-22 °C (-5,8/-7,6 °F). I wanted to send myself an email when the temperature raises to ≥ -19°C. So I started to implement an Node-RED flow with some different nodes for checking the temperature and triggering an email if the temperature is greater than my setted threshold.

![Node-RED flow for checking the temperature and sending an email](https://cdn-images-1.medium.com/max/2358/1*CNbBH7Ay9kUZrWt5y3zSpA.png)*Node-RED flow for checking the temperature and sending an email*

I also implemented a simple Dashboard to visualize the temperature course in relation to time and to display the current freezer temperature. This was easily done with the [node-red-dashboard package](https://github.com/node-red/node-red-dashboard). Which provides a dashboard UI for Node-RED. The flow can be also found in the above-mentioned repo.

![Node-RED dashboard for visualization purposes](https://cdn-images-1.medium.com/max/2336/1*Qb_8Gih3gH9AqNW1zDqlKQ.png)*Node-RED dashboard for visualization purposes*

Now that the sensor is tested and all software parts work, I started to design a case housing for our microcontroller. I used [crashoverride](https://www.thingiverse.com/Crashoverride/about)’s [ESP8266 ESP-12E nodeMCU Lua Case](https://www.thingiverse.com/thing:1305796) as my base. I changed some small things via [tinkercad, ](https://www.tinkercad.com/)which is a really nice 3D CAD design tool by the way and et voilà we’re ready to print the casing!

![CAD model for our housing](https://cdn-images-1.medium.com/max/2000/1*k811yIxx4fwmxleoleLHYg.png)*CAD model for our housing*

While my 3D printer printed out the case, I soldered the parts together on a hole pattern board and inserted a flat ribbon cable into the middle of our cable. The reason is that I just pinch the cable into the door and thus the rubber lip of the freezer is not pressed so far apart.

In the near future I want to add a little microcontroller for our office, with a passive buzzer module as an additional alarm when the temperature increases. I already ordered some buzzer modules, but it will take some time until they will arrive from Hong Kong. In summary, it was a really cool project for a Saturday afternoon.
