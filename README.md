# ESP32-TESTKIT

## Motivation
Breadboards are the best or most uncomplicated way to prototype, to test electronic circuit parts quickly and easily or to change them without a soldering iron and without losing the components.

The range of applications for ESP8266 and ESP32 is endless. It is fantastic how quickly and easily practical applications can be realised with this nice devices, which are also super easy to address via WiFi or BLE. They are also very cheap and, like many commercial products (e.g. sonoff, shelly), very reliable. 

The possibilities for using these chips are exorbitantly increased by the great ESPHOME project and also further opened up for prototyping, because it allows the otherwise additionally necessary programming to be reduced to the configuration of a single YAML file. Among other things, it offers the possibility of accessing an elegant web interface, which makes prototypes fantastically easy to implement and test, even if the final programming is to be completely changed afterwards.

** But unfortunately breadboards and ESP-DEVKITS don't really go well together. **
![breadboard_issue](https://user-images.githubusercontent.com/10268240/161389199-028ddf25-8427-4133-889e-8c40c2c76b93.jpeg "breadboard paradox: no pin can be used")

However, if you have ever tried to test your application on a breadboard with a normal TestKIT, the result is somewhat frustrating. I would call it the breadboard paradox. The grid dimension of 2.56mm fits, but all contacts are covered and therefore unusable. There is no chance to contact the individual pins of the board. The required pins must be connected to the board as cables. So you will quickly be faced with a multitude of cable connections that bring with them a high potential for errors during testing. In addition, during my experiments with the ESP32, I found that longer cables in particular can lead to problems with the voltage-supplying lines when the chip wants to establish the WiFi connection, for example, as higher current peaks can obviously occur here.

## Problem definition

This project was therefore about keeping the advantages of ESP-DEVKITS, but resolving the paradox described above and making the CPU pins on the breadboard all available. This makes it extremely convenient to supply power directly to the breadboard. Most DEVKITS have a USB micro-connector and supply the board with 5V as well as 3V3. This would be a requirement that should not be waived. The board should also ensure stable operation of the ESP32 chip, ensuring WiFi setup, etc. without brownout detection or crashes. In addition to the supply via a USB adapter, it could also be helpful to be able to use a 3V3 voltage source (Li-Ion, alkaline batteries) directly.

It has also been shown that there is a need for digital inputs and outputs in almost all circuits. For testing circuits, these should be equipped with signal LEDs to make debugging possible without additional measuring devices, auxiliary circuits, test LEDs. But the ESP32 also offers the possibility to use ADCs and DAC. In order to be able to measure voltages above 3.3V, a suitable voltage divider is needed. Here it would be good to have measurable voltages of up to 15V to cover most applications. Achieving an accuracy of 0.01V is no problem with the ESP32. The ADC functions are masterfully supported by [ESPHOME ADC](https://esphome.io/components/sensor/adc.html?highlight=adc) including the AutoRange function. 

## Provided solution

My ESP32-DEVKIT, which I would like to present here, therefore has the following features:

- USB B micro PowerInput or alternatively
- 12V PlugIn PowerInput
- Input power available as own connector for tests
- DC-DC converter to 3V3
- PGM-socket (shelly-compatible)
- RESET button and GPIO00 button
- 4x 15V ADC-ports (with voltage dividers)
- 4x digital output (LED-controlled) vs. GND-level
- 4x digital input (LED-controlled) vs. GND-level
- all ESP-PINs available on the breadboard

Circuit diagram and board are realised in KICAD V6. The board is 2-layered.

![KIT_Breadboard](https://user-images.githubusercontent.com/10268240/161389607-0493d92c-b815-4872-a612-498574beed3e.jpg)
