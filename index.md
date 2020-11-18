# Instrumentation

## Introduction

This site will give instructions on how to build and calibrate the required electrical systems for the Agribot Project. Each device will have its own page of instructions and a brief explaination of how the system works.

## Ultrasonic Water Level Sensor  [<img src="http://www.google.com.au/images/nav_logo7.png">](http://google.com.au/)

To measure the water level in the tank an ultrasonic sensor was one of the possible options for measuring the level. The distance between the sensor and the water is measuered using a HC-S04 and that data is passed to an Arduino Nano and used to calculated the level of water left in the tank

[<h2>PT100 Temperature Sensor</h2>](./temperature.md)
To measure the ambient temperature, the system was designed around the PT100 RTD. It is converted to a voltage using a wheatstone bridge and amplified to a 0 - 5V range using an lm324 to make the most use of an Arduino Nano's A/D input range. The Nano is used for A/D conversion and re-scaling of units to output a temperature reading in deg C
