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

## Schematic of Ultrasonic Sensor
<p align="center">
    <img src="images/1.PNG" width="50%">
</p>

The table below shows the pin name and their corresponding arduino pins. The trigger and echo pin could be
changed into a different digital pins but ensure that the code in the Arduino IDE is modified with it.
**Pin Name**|**Arduino Pins**
:-----:|:-----:
Vcc|5V
Trigger|Digital Pin 9 (D9)
Echo|Digital Pin 10 (D10)
Gnd|Ground

## Code Explanation
Each block of the code will be explained here and the complete code will be provided at the end aswell as on the top righ corner
of the main page available for download.

### Defining the pins and the variables
```
// defines pins numbers for trigger and echo
const int trigPin = 9;      //Sets Trigger to Digital Pin 9
const int echoPin = 10;     //Sets Trigger to Digital Pin 9

// defines variables
long duration;
int distance;
```