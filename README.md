# 2.4 Inch TFT LCD Display (ST7789) – Arduino How To Guide 
The purpose of the guide is to help beginner Arduino hobbyist get their 2.4” TFT LCD displays working. When the display I purchased arrived it took me longer than I would like to admit to get it up and running. The reason for this (other than my lack of knowledge) was the lack of documentation/guides available for this particular display. This guide is also intended to introduce some of the background concepts behind what we are doing.
This guide will not be covering the touch functionality mainly because the display that arrived in the mail didn’t come with the touch chip.


![2.4 inch TFT display ST7789](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/2_4inchTftDisplay.jpg)


![2.4 inch TFT display ST7789 back](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/2_4inchTftDispayBottom.jpg)



|Abbreviation|Full Name|
| -------------:|:-------------|
|TFT:| Thin Film Transistor|
|LCD:| Liquid Crystal Display|
|ST7789:| the name of the display controller|
|SPI:| Serial Peripheral Interface|
|TTL:| Transitor-Transitor Logic|
|VCC:| Common Collector Voltage|
|GND:| Ground|
|CS:| Chip Select; SS: Slave Select; DS: Device Select|
|RST:| Reset|
|DC:| Data / Command|
|MOSI:| Master Out, Slave in; PICO: Peripheral In, Controller Out|
|MISO:| Master In, Slave Out; POCI: Peripheral Out, Controller In|
|SCK:| Serial Clock; SCLK: Serial Clock; CLK: Clock|
|LED:| Light Emmitting Diode(s)|
|DIN:| Data In|
|DO:| Data Out|
|IRQ:| Interrup Request|

## Voltage Divider
The 2.4 inch TFT LCD display uses both 5V and 3.3V. Five volts are used for the VCC and powering the LED backlight. 3.3 volts is used for communicating logic/data to the display. The Arduino Uno, Nano, and Mega are not capable of outputting 3.3v logic, therefore we need to reduce the 5V logic coming from the Arduino. To achieve this reduction in voltage we need to arrange resistors in series with the display pins. This setup is known as a voltage divider. 
I decided to build the circuit on a small perf board I had as I will be prototyping another project with it. It has female pin headers so that any Arduino can easily be connected to it and the display can be removed.

|Pins |Voltage|
|------:|:---------|
|VCC|5V|
|GND|GND|
|CS| 3.3V TTL|
|RESET|3.3V TTL|
|DC|3.3V TTL|
|MOSI| 3.3V TTL|
|SCK|3.3V TTL|
|LED| 5V|

![voltage divider circuit Diagram for 2.4 inch TFT display ST7789](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/schematic24InchTFTDisplay.jpg)

![voltage divider on board](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/voltageDivider.jpg)

![voltage divider wiring diagram](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/wiringDiagram2.4InchTFTDisplay.jpg)

![voltage divider on board bottom](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/voltageDividerBottom.jpg)

![voltage divider connected to display side profile](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/voltageDividerSide.jpg)


## Communicating With The Display
The Arduino communicates with the display via Serial Peripheral Interface (SPI) protocol. 
It is best to use the SPI Library, however the library will use the designated SPI pins for your Arduino.
The SPI pins are different for each board type:



|Board |SPI Pin #|
|:------:|:---------:|
|UNO   |MOSI: 11 |
|      |MISO: 12 |
|      |SCK: 13  |
|      |CS: 10   |
|||
|NANO  |MOSI: 11 |
|      |MISO: 12 |
|      |SCK: 13  |
|      |CS: 10   |
|||
|MEGA  |MOSI: 51 |
|      |MISO: 50 |
|      |SCK: 52  |
|      |CS: 53   |


![working display](https://github.com/ZPaulWeleschuk/Arduino-How-To-Guide-2.4-TFT-Display-ST7789/blob/main/images/workingDisplay.jpg)

## Libraries 
Install in the Arduino IDE: **Adafruit ST7735 and ST7789 Library by Adafruit**   
Github link: https://github.com/adafruit/Adafruit-ST7735-Library

Install in the Arduino IDE: **Adafruit-GFX-Library by Adafruit**  
GitHub link: https://github.com/adafruit/Adafruit-GFX-Library

Comes pre-installed in the Arduino IDE: **SPI library** 
