# Servo Motor Basics with Arduino

Learn how to connect and control servo motors with your Arduino board.

The [Servo Library](https://www.arduino.cc/reference/en/libraries/servo/) is a great library for controlling servo motors. In this article, you will find two easy examples that can be used by any Arduino board.

The first example controls the position of a RC (hobby) [servo motor](http://en.wikipedia.org/wiki/Servo_motor#RC_servos) with your Arduino and a potentiometer. The second example sweeps the shaft of a RC [servo motor](http://en.wikipedia.org/wiki/Servo_motor#RC_servos) back and forth across 180 degrees.

You can also visit the [Servo GitHub repository](https://github.com/arduino-libraries/Servo) to learn more about this library.

## Hardware Required

- Arduino Board
- Servo Motor
- 10k ohm potentiometer
- hook-up wires

## Circuit

Servo motors have three wires: power, ground, and signal. The power wire is typically red, and should be connected to the 5V pin on the Arduino board. The ground wire is typically black or brown and should be connected to a ground pin on the board. The signal pin is typically yellow or orange and should be connected to PWM pin on the board. In these examples, it is pin number 9.

### Knob Circuit

For the **Knob** example, wire the potentiometer so that its two outer pins are connected to power (+5V) and ground, and its middle pin is connected to A0 on the board. Then, connect the servo motor to +5V, GND and pin 9.

[![The Knob Circuit.](https://docs.arduino.cc/static/323f79da8e7a89e7d2ff9805c5976b25/a6d36/servo-knob-circuit.png)](https://docs.arduino.cc/static/323f79da8e7a89e7d2ff9805c5976b25/29114/servo-knob-circuit.png)The Knob Circuit.



### Sweep Circuit

For the **Sweep** example, connect the servo motor to +5V, GND and pin 9.

[![The Sweep Circuit.](https://docs.arduino.cc/static/943895f1f578104f7af98741d69a7c97/a6d36/servo-sweep-circuit.png)](https://docs.arduino.cc/static/943895f1f578104f7af98741d69a7c97/29114/servo-sweep-circuit.png)The Sweep Circuit.



## Examples

### Knob

Controlling a servo position using a potentiometer (variable resistor).

```arduino
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
int potpin = 0;  // analog pin used to connect the potentiometer
int val;    // variable to read the value from the analog pin

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  val = analogRead(potpin);  // reads the value of the potentiometer (value between 0 and 1023)
  val = map(val, 0, 1023, 0, 180);     // scale it (value between 0 and 180)
  myservo.write(val);                  // sets the servo position according to the scaled value
  delay(15);                           // waits for the servo to get there
}
```

### Sweep

Sweeps the shaft of a RC servo motor back and forth across 180 degrees.

```arduino
#include <Servo.h>

Servo myservo;  // create servo object to control a servo
// twelve servo objects can be created on most boards

int pos = 0;    // variable to store the servo position

void setup() {
  myservo.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
  // goes from 0 degrees to 180 degrees in steps of 1 degree
  for (pos = 0; pos <= 180; pos += 1) { 
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
  for (pos = 180; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees
    myservo.write(pos);              // tell servo to go to position in variable 'pos'
    delay(15);                       // waits 15ms for the servo to reach the position
  }
}
```

