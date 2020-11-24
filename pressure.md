# Pressure Sensor

The Honeywell 24PC Series miniature pressure sensors provide reliable gage pressure sensing performance in a compact package.

## 24PC Sensor Data Sheet

Using the sensor sheet it will provide as a guide to choose the which 24PC series is best depend on the pressure proportional to height of the tank.

[24PC Datasheet](./24PC.md)

## Build Ciruit with 24PC Sensor

<p align="center">
    <img src="images/.PNG">
</p

The 24PC sensor is connected to a Wheatstone Bridge circuit in the Tank.
A Differential Amplifier was connected with input resistors of 270 K ohms and output resistors of 1 M ohms, to give a gain of 3.7.
A Non-inverting amplifier was connected to the output of the differential amplifier with an input resistance of 1 k ohms and an output resistor of 165 K ohms. Didn't find a resistor with that value to so a 220 K ohms resistor was used to give a gain of 166.
The total gain from the amplifiers is 610.
Instead of the differential and non-inverting amplifier, a single supply instrumentation amplifier was built with a single resistor with a value of 330 ohms to give a gain of 610.
