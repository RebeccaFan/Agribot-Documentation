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
This block of code defines the pins of the trigger and the echo pin. In this case they are the digital pins number 9 and 10 on the Arduino board. They are named as "trigPin" and "echoPin" for clarity of the code. 
The variables are then defined. The travel time you'll get from the sensor is declared as a Long variable and named as "duration". An integer type is needed for the "distance" variable

```
// defines pins numbers for trigger and echo
const int trigPin = 9;      //Sets Trigger to Digital Pin 9
const int echoPin = 10;     //Sets Echo to Digital Pin 10

// defines variables
long duration;
int distance;
```
### Setup section
In setup define the trigPin as an output and the echoPin as an input. The serial communication is required to be started to show the data on the serial monitor.

```
void setup() {
pinMode(trigPin, OUTPUT);    // Sets the trigPin as an Output
pinMode(echoPin, INPUT);    // Sets the echoPin as an Input
Serial.begin(9600);        // Starts the serial communication
}

```
### Loop section
At the start of the loop, you need to ensure that the trigPin is clear to do this set the pin on a LOW state for 2 µs. To generate the Ultra sound wave, set the trigPin on a HIGH state for 10 µs.

```
void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

```
### pulseIN function and calculating distnace
pulseIn () function has 2 variables, the first entry in the bracket is the name of the echo pin (echoPin) and the second entry you can set it to on a HIGH or LOW. This function will read the travel time and put in the variable called duration.
In the code, HIGH means that the pulseIn() function will wait for the pin to go HIGH. This is caused by the bounced of the sound wave. It will then start the timing, it will wait until the pin is LOW when the sound wave will end and stop the timing. It will then return the length of the pulse in microsecond.

For the distance, the data in the duration variable will be multiplied by 0.032 and divide it by 2. The 0.032 value comes from the fact that the speed of the sound is 340 m/s or 0.034 cm/µs. It is divided by 2 since the data that you will get in the echoPin would be doubled as the sound wave needs to travel forward and bounce backward. So in order to get the distance in cm we need to multiply the received data in echoPin which is stored in "duration" variable by 0.034 and then divide it by 2. At the end of the code, it will then display the value of the distance on the serial monitor.

```
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);

```
### Complete Code
Here is the complete code.
```
// defines pins numbers for trigger and echo
const int trigPin = 9;      //Sets Trigger to Digital Pin 9
const int echoPin = 10;     //Sets Echo to Digital Pin 10

// defines variables
long duration;
int distance;

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
Serial.begin(9600); // Starts the serial communication
}

void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
}

```