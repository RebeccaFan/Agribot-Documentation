# Temperature Sensor [<img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.flaticon.com%2Ficons%2Fpng%2F512%2F15%2F15766.png&f=1&nofb=1" width="20px">](./index.md)

## Types of Temperature Sensors

Before deciding to base the the temperature measurement system around the PT100, the various available options were considered. A LM35, thermocouple, US Sensors thermistor and PT100 were all considered. The table below compares the different properties of each of the sensors:

|                **LM35**                 |           **Thermocouple**            |          **Thermistor**           |               **PT100**               |
| :-------------------------------------: | :-----------------------------------: | :-------------------------------: | :-----------------------------------: |
|                                         |                                       |
|      Small Range: -55°C to +150°C       |    Large Range: -270°C to +1400°C     |   Small Range: -30°C to +130°C    |    Medium Range: -200°C to +850°C     |
|  Output Unit: Millivolts (mV) [linear]  | Output Unit: Millivolts (mV) [linear] | Output Unit: Ohms(Ω) [non-linear] |     Output Unit: Ohms(Ω) [linear]     |
|             Poor Stability              |            Poor Stability             |          Poor Stability           |           Decent Stability            |
|   Very low sensitivity, low accuracy    |  Very low sensitivity, low accuracy   | High sensitivity, decent accuracy | Very high sensitivity , good accuracy |
| <img src="images/lm35.png" width="70%"> |  <img src="images/Thermocouple.jpg">  | <img src="images/Thermistor.png"> |     <img src="images/PT100.png">      |

### Reasons why PT100 is used

- It is one of the most accurate sensors because of its platinum material
- It covers a good range of temperature
- Good long-term stability and response time
- The relationship between resistance and temperature is relatively linear
- Relatively immune to electrical noise
- Often used in industrial operations for atmospheric conditions

### Block Diagram for PT100 circuit

<p align="center">
    <img src="images/BlockDiagram.PNG">
</p>

The block diagram for this circuit, the temp range is -30 to 50, using the PT100 tables it equals to 88.22 to 119.40 ohms. K1 is the sensitivity of the Pt100. For a PT100 sensor, a 1 °C temperature change will cause a 0.384 ohm change in resistance.
The values from the PT100 will go to a Wheatstone bridge which will calculate them to 0 to 200mV. K2 is the change in mV from the Wheatstone bridge output per ohm in the PT100.
From there it needs to be amplified to achieve the output of the Arduino.
K3 is the gain needed.
From there it goes into the A/D converter to convert V to Digital Units. For a 10 bit converter it will have values from 0 to 1023. K3 is the sensitivity of the Arduino which is a constant of 204.6 digital units per volt.  
This will need to rescaled to get back to degrees Celsius units,  
K5 is the change per digital unit will be a change in 0.78 degrees Celsius. To talk in dept about these Joy will be explaining the wheatstone bridge.

## Schematic of PT100 circuit

<p align="center">
    <img src="images/schematic.PNG">
</p>

### Equipment for the circuit

- Breadboards
- Arduino Nano
- 2 wire PT100
- 10K Ohm Potentiometer
- LM324 Chip
- x4 200 Ohm Resistor
- x4 10 Ohm Resistor
- x2 100 Ohm Resistor
- x2 47 Ohm Resistor
- x4 1M Ohm Resistor
- x2 470K Ohm Resistor
- Jumper Wires

### Circuit for PT100 Temperature Sensor

<p align="center">
    <img src="images/PT100_Full.jpg" width="60%">
</p>

### Breadboard Close Up

<p align="center">
    <img src="images/PT100_breadb.jpg" width="60%">
</p>

### Breadboard connected to Arduino

<p align="center">
    <img src="images/arduino.jpg" width="60%">
</p>

### Required Temperature Range

| **Tmin** | **Tmax** |
| :------: | :------: |
|  -30 °C  |  50 °C   |
| 243.15 K | 323.15 K |

### Table of Unit Conversion Through System

| T (°C) | T (K)  | Rth (Ω) | Vout (V) | Rescale | A/D (DU) |
| :----: | :----: | :-----: | :------: | :-----: | :------: |
|        |        |         |          |         |          |
| -30.00 | 243.15 |  88.22  |   0.00   |  0.00   |   0.06   |
| -22.00 | 251.15 |  91.37  |   0.02   |  0.53   |  107.86  |
| -14.00 | 259.15 |  94.52  |   0.04   |  1.05   |  214.28  |
| -6.00  | 267.15 |  97.65  |   0.06   |  1.56   |  319.32  |
|  2.00  | 275.15 | 100.78  |   0.08   |  2.07   |  423.03  |
| 10.00  | 283.15 | 103.90  |   0.10   |  2.57   |  525.44  |
| 18.00  | 291.15 | 107.02  |   0.12   |  3.06   |  626.58  |
| 26.00  | 299.15 | 110.12  |   0.14   |  3.55   |  726.46  |
| 34.00  | 307.15 | 113.22  |   0.16   |  4.03   |  825.13  |
| 42.00  | 315.15 | 116.32  |   0.18   |  4.51   |  922.60  |
| 50.00  | 323.15 | 119.40  |   0.20   |  4.98   | 1018.91  |

### Wheatstone Bridge Configuration

|  Vs  |  R1   |  R2   |  R3   |
| :--: | :---: | :---: | :---: |
| 4.71 | 505.8 | 505.8 | 88.22 |

### Amplifier Properties

|    Gain     | R1  | R2  | Rg  |
| :---------: | :-: | :-: | :-: |
| 24.89554462 | 2k  | 10k | 1k  |

### Arduino Code

Download the code in the following:
[Click here to Download](https://github.com/RebeccaFan/Agribot-Documentation/releases/download/1.0.0/PT100_ReScaling_Code.zip)

```
int vinPin = A0;
int vinBits;
float outDegC;

void setup()
{
    Serial.begin(9600);

void loop()
{
    delay(500);
    //delay for half a second

    vinBits = analogRead(vinPin);
    //read in value from Arduino

    outDegC = (vinBits * .0785) - 30;
    //rescale back to degrees celsius
    // (50 - (-30)) / 1019 bits = 0.785

    Serial.print("Voltage In Bits: ");
    Serial.print(vinBits);
    Serial.print("\t\t\t");
    // print out in voltage in bits on screen

    Serial.print("Temperature: ");
    Serial.print(outDegC);
    Serial.print(" °C\t\t\t");
    // print out in degrees on screen

    Serial.println();
}

```
