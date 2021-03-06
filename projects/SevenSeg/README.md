
Overview
--------------------------------------------
* Name: SevenSeg 
* Description: Display an analog input 10-bit ADC value(0-1023)
on a 4 digit seven segment display.
* Author: Gavin Lyons.
* Complier: xc8 v2.05 compiler
* PIC: PIC16F1619 
* IDE:  MPLAB X v5.05
* Development board: Microchip Curiosity Board, PIC16F1619

Table of contents
---------------------------

  * [Overview](#overview)
  * [Features](#features)

Features
----------------------

Display the value of an analog input (10-bit ADC value(0-1023)) of PIC pin,
on a 4 digit seven segment display. The ADC is converted to voltage.
(It assumes vdd  = 5V) which maps 0-1023 to 0-5V ranges. So will look like 3-02 
for 3.02V.

The 10-bit ADC (0 to 1023) value is read from a pot attached to PIC pin RA4(PORT A)
It is then displayed on the 4-digit seven segment display.
The value is read on a interrupt generated by overflow of timer0 every second.
So display will change once every second.
A status LED on RA2 toggles on same Timer.

4 pins of PORT B controls the four cathodes of each digit.

3 pins of PORT C of PIC outputs the data to a 74HC595 shift register which in 
turn is connected to anodes of the SMA420564 common cathode display LED module.

In this folder the main source code in C for program can be found in file main.c
The code  generated using the MPLAB Code Configurator (MCC) tool is  
 in folder called mcc_generated_files

MPLAB Code Configurator (MCC) is a free, graphical programming environment that generates ,
C code to be inserted into your project. It is built in to the MPLAB IDE
Using an interface, it enables and configures a rich set of 
peripherals and functions specific to the application.

RA4 = Analog In.
RA2 = Status LED.

GPIO function on PIC, 3 lines to 74HC595

| 74HC595 pin  | Pic 16F1619 pin |
| ------ | ------ |
| SER  14 serial data | RC0 |
| RCLK 12 Latch | RC1 |
| SCLK 11 Storage | RC2 |

Connections from seven segment module to PIC(digit control).

| Pic 16F1619 pin  | LED module SMA420564 |
| ------ | ------ |
| RB4  | D1 12 |
| RB5 | D2 9 |
| RB6  | D3 8 |
| RB7  | D4 6 |

Connections from seven segment module to shift register pins.

| 74HC595 pin  | LED module SMA420564 |
| ------ | ------ |
| pin 7 QH | A pin 11 |
| pin 6 QG | B pin 7 |
| pin 5 QF | C pin 4 |
| pin 4 QE | D pin 2|
| pin 3 QD | E pin 1|
| pin 2 QC | F pin 10|
| pin 1 QB | G pin 5 |
| n/a | DP pin 3 |

For more info on segments lettering  of seven segment display, see here.
https://en.wikipedia.org/wiki/Seven-segment_display

![PICTURE](https://github.com/gavinlyonsrepo/pic_16F1619_projects/blob/master/images/7segpinout.png)

Schematic
------------------------

![PICTURE ](https://github.com/gavinlyonsrepo/pic_16F1619_projects/blob/master/images/SevenSeg.png)
