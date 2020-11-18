# Temperature Sensor

## Types of Temperature Sensors

| **Thermocouple**                                        | **Thermistor**                                                          | **PT100**                                 |
| ------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------- |
| Range is very wide -270°C to +1400°C                    | Range is small -30°C to +130°C                                          | Range is medium -200°C to +850°C          |
| Output –mV increase with temp                           | Output -resistance changes with temp, therefore, must convert to mV     | Output resistance increases linearly      |
|  Stability is poor, linear                              | Stability is poor, non-linear                                           | Stability is good, linear                 |
| Very low sensitivity, accuracy is low                   | Very high sensitivity output, large change in ohms, accuracy is medium  | Very high sensitivity , accuracy is high  |
| <img src="images/Thermocouple.jpg" alt="Thermocouple">  | <img src="images/Thermistor.png" alt="Thermistor">                      | <img src="images/PT100.png" alt="PT100">  |

## Schematic of the Temperature Sensor Ciruit

The following is the schematic of the full ciricuit with the wheatstone bridge and pt100

<p align="center">
    <img src="images/schematic.PNG"  width="60% >
</p>

## Excel for the PT100 and Wheatstone Bridge

| PT100 Excel Calculations and Graphs |           |          |                 |     |         |          |     |             |                       |
| ----------------------------------- | --------- | -------- | --------------- | --- | ------- | -------- | --- | ----------- | --------------------- |
|                                     |           |          |                 |     |         |          |     |             |                       |  |  |
|                                     |           |          |                 |     |         |          |     |             | WheatStone Properties |  |  |
| Temperature Range                   |           |          |                 |     |         |          |     | Vs          | R1                    | R2 | R3 |
| Tmin                                | -30       | DegC     | 243.15          | K   |         |          |     | 4.71        | 505.8                 | 505.8 | 88.22 |
| Tmax                                | 50        | DegC     | 323.15          | K   |         |          |     | Ro          | a                     | b | c |
|                                     |           |          |                 |     |         |          |     | 1.00E+02    | 3.91E-03              | -5.78E-07 | -4.18E-12 |
| T(degC)                             | T(Kelvin) | Rth = R4 | Vo (Wheatstone) |     | Rescale | A/D (DU) |     |             |                       |  |  |
| -30.00                              | 243.15    | 88.22    | 0.00            |     | 0.00    | 0.06     |     |             |                       |  |  |
| -22.00                              | 251.15    | 91.37    | 0.02            |     | 0.53    | 107.86   |     |             |                       |  |  |
| -14.00                              | 259.15    | 94.52    | 0.04            |     | 1.05    | 214.28   |     |             | A/D Properties        |  |  |
| -6.00                               | 267.15    | 97.65    | 0.06            |     | 1.56    | 319.32   |     | Vin range   | No.bits               | Arduino Sensitivity |  |
| 2.00                                | 275.15    | 100.78   | 0.08            |     | 2.07    | 423.03   |     | 5           | 10                    | 204.6 |  |
| 10.00                               | 283.15    | 103.90   | 0.10            |     | 2.57    | 525.44   |     |             |                       |  |  |
| 18.00                               | 291.15    | 107.02   | 0.12            |     | 3.06    | 626.58   |     |             | Amplifier Properties  |  |  |
| 26.00                               | 299.15    | 110.12   | 0.14            |     | 3.55    | 726.46   |     | Gain        | R1                    | R2 | Rg |
| 34.00                               | 307.15    | 113.22   | 0.16            |     | 4.03    | 825.13   |     | 24.89554462 | 2k                    | 10k | 1k |
| 42.00                               | 315.15    | 116.32   | 0.18            |     | 4.51    | 922.60   |     |             |                       |  |  |
