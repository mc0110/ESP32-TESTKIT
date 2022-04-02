# ESP32-TESTKIT

## Motivation
Breadboards are the best or most uncomplicated way to prototype, to test electronic circuit parts quickly and easily or to change them without a soldering iron and without losing the components.

The range of applications for ESP8266 and ESP32 is endless. It is fantastic how quickly and easily practical applications can be realised with this nice devices, which are also super easy to address via WiFi or BLE. They are also very cheap and, like many commercial products (e.g. sonoff, shelly), very reliable.

However, if you have ever tried to test your application on a breadboard with a normal TestKIT, the result is somewhat frustrating. There is no chance to contact the individual pins of the board. The required pins must be connected to the board as cables. So you will quickly be faced with a multitude of cable connections that bring with them a high potential for errors during testing. In addition, during my experiments with the ESP32, I found that longer cables in particular can lead to problems with the voltage-supplying lines when the chip wants to establish the WiFi connection, for example, as higher current peaks can obviously occur here.

![breadboard_issue](https://user-images.githubusercontent.com/10268240/161389199-028ddf25-8427-4133-889e-8c40c2c76b93.jpeg)



![KIT_Breadboard](https://user-images.githubusercontent.com/10268240/161389607-0493d92c-b815-4872-a612-498574beed3e.jpg)
