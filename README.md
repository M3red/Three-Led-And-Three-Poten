# Three-Led-And-Three-Poten
How to operate three led using three poten
Tools Required for Tinkercad:
1 Arduino Uno

3 LEDs

3 220 ohm Resistors

3 Potentiometers

Wires

Breadboard

⚡ Connections:
🟢 For LEDs:
LED Positive (Anode) to 220 ohm Resistor Negative (To)
LED1 Pin 9 Yes GND
LED2 Pin 10 Yes GND
LED3 Pin 11 Yes GND

🟠 For Potentiometers:
Each potentiometer has 3 leads:

Left pin to 5V

Right pin to GND

Middle pin (wiper) to an analog input on the Arduino:

Potentiometer Middle pin to Pin
Pot 1 A0
Pot 2 A1
Pot 3 A2

🧾 Arduino code to control the intensity of the light according to the value of each potentiometer:
cpp
Copy
Edit
// Analog input pins for potentiometers
const int pot1 = A0;
const int pot2 = A1;
const int pot3 = A2;

// PWM pins for LEDs
const int led1 = 9;
const int led2 = 10;
const int led3 = 11;

void setup() {
// No need to define analog inputs
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
}

void loop() {
// Read potentiometer values (0 to 1023)
int val1 = analogRead(pot1);
int val2 = analogRead(pot2);
int val3 = analogRead(pot3);

// Convert the value from 0–1023 to 0–255 (for PWM)
int brightness1 = map(val1, 0, 1023, 0, 255);
int brightness2 = map(val2, 0, 1023, 0, 255);
int brightness3 = map(val3, 0, 1023, 0, 255);

// Turn on the LEDs at the desired intensity
analogWrite(led1, brightness1);
analogWrite(led2, brightness2);
analogWrite(led3, brightness3);

delay(10); // A small delay to avoid noise
}
🎯 What does this code do?
It reads the value of each variable resistor.

It converts it to an appropriate value for the light intensity (PWM).

It controls the brightness of each LED independently.
