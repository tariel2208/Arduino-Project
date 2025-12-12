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
