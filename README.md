# Arduino Ultrasonic Sensor with LEDs and Buzzer

This project uses an Arduino Uno, an HC-SR04 ultrasonic sensor, 2 LEDs, and a buzzer to create a simple distance alert system.

## Components
- Arduino Uno
- HC-SR04 Ultrasonic Sensor
- 2 LEDs (Red and Green)
- Buzzer
- Jumper wires
- Breadboard (optional)

## How it works
1. The ultrasonic sensor continuously measures distance.
2. LEDs light up based on the measured distance:
   - Green LED: Object is far
   - Red LED: Object is too close
3. Buzzer sounds when the object is within a critical distance.

## Wiring
- **HC-SR04**
  - VCC → 5V
  - GND → GND
  - Trig → Arduino pin 9
  - Echo → Arduino pin 10
- **Red LED** → Arduino pin 2 (with resistor)
- **Green LED** → Arduino pin 3 (with resistor)
- **Buzzer** → Arduino pin 4

## Installation
1. Connect the components as described above.
2. Upload the `UltrasonicLEDsBuzzer.ino` sketch to the Arduino.
3. Observe LEDs and buzzer reacting to distance changes.

## Code Example
```cpp
#include <Arduino.h>

const int trigPin = 9;
const int echoPin = 10;
const int redLED = 2;
const int greenLED = 3;
const int buzzer = 4;
long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(buzzer, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // Ultrasonic distance measurement
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;
  Serial.println(distance);

  // LED and buzzer control
  if (distance < 10) {
    digitalWrite(redLED, HIGH);
    digitalWrite(greenLED, LOW);
    digitalWrite(buzzer, HIGH);
  } else {
    digitalWrite(redLED, LOW);
    digitalWrite(greenLED, HIGH);
    digitalWrite(buzzer, LOW);
  }
  delay(200);
}
