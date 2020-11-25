# Instrumentation

## Introduction

This site will give instructions on how to build and calibrate the required electrical systems for the Agribot Project. Each device will have its own page of instructions and a brief explanation of how the system works.

## Start with the Basics [<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.flaticon.com%2Ficons%2Fpng%2F512%2F3%2F3665.png&f=1&nofb=1" width="20px">](./basics.md)

A brief introduction to working with the basics like Breadboards, Resistors and the Arduino IDE before building any systems.

## Ultrasonic Water Level Sensor [<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.flaticon.com%2Ficons%2Fpng%2F512%2F3%2F3665.png&f=1&nofb=1" width="20px">](./ultrasonic.md)

To measure the water level in the tank an ultrasonic sensor was one of the possible options for measuring the level. The distance between the sensor and the water is measured using a HC-S04 and that data is passed to an Arduino Nano and used to calculated the level of water left in the tank.

## Pressure Water Level Sensor [<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.flaticon.com%2Ficons%2Fpng%2F512%2F3%2F3665.png&f=1&nofb=1" width="20px">](./pressure.md)

To measure the water level in the tank an using a pressure sensor. Using the Honeywell 24PC pressure sensor series to find the pressure in the tank and calculate the volume of water in the tank.

## PT100 Temperature Sensor [<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.flaticon.com%2Ficons%2Fpng%2F512%2F3%2F3665.png&f=1&nofb=1" width="20px">](./temperature.md)

To measure the ambient temperature, the system was designed around the PT100 RTD. It is converted to a voltage using a wheatstone bridge and amplified to a 0 - 5V range using an lm324 to make the most use of an Arduino Nano's A/D input range. The Nano is used for A/D conversion and re-scaling of units to output a temperature reading in deg C
