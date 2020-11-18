___
# Ultrasonic Sensor

The HC-SR04 Ultrasonic sensor component will be used to measure the level of the water in a tank. The data will be pass 
onto the arduino nano. The code will be written on the software called Arduino IDE.
___
<p align="center">
    <img src="images/Ultrasonic.png" width="40%">
</p>

**Pin Number**|**Pin Name**|**Description**
:-----:|:-----:|:-----:
1|Vcc|The Vcc pin powers the sensor, typically with +5V
2|Trigger|Trigger pin is an Input pin. This pin has to be kept high for 10us to initialize measurement by sending US wave.
3|Echo|Echo pin is an Output pin. This pin goes high for a period of time which will be equal to the time taken for the US wave to return back to the sensor.
4|Ground|This pin is connected to the Ground of the system.

<p align="center">
    <img src="images/1.png" width="40%">
</p>