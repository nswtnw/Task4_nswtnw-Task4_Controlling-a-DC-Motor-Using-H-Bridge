# Arduino Controlling a DC Motor Using H-Bridge
## Introduction
This project involves controlling a DC motor using an Arduino Uno and an H-Bridge (L293D). The motor's speed and direction are controlled through the Arduino based on input from two push buttons.

## Components:
1. Arduino Uno
2. H-Bridge L293D
3. DC Motor
4. Push Buttons (2)
5. Breadboard
6. Connecting Wires

## Circuit Diagram
![image](https://github.com/user-attachments/assets/fe915ad3-dc51-4cb3-8963-af94c2dbbc49)

## Code Expanation
The Arduino code is designed to read the input from two push buttons and control the motor's speed and direction accordingly.

```
int speed1 = 0, speed2 = 0, x = 0, pwm = 0;

void setup() {
  pinMode(3, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(4, INPUT);
  digitalWrite(4, HIGH);  // Enable internal pull-up resistor
  pinMode(5, INPUT);
  digitalWrite(5, HIGH);  // Enable internal pull-up resistor
}

void loop() {
  speed1 = digitalRead(4);
  speed2 = digitalRead(5);

  if (speed1 == LOW) {
    x = 3;
    digitalWrite(6, HIGH);
    digitalWrite(7, LOW);
  }
  if (speed2 == LOW) {
    x = 5;
    digitalWrite(7, HIGH);
    digitalWrite(6, LOW);
  }

  pwm = map(x, 0, 5, 0, 255);
  analogWrite(3, pwm);
}
```

## Conclusion
This project successfully demonstrates how to control a DC motor's speed and direction using an Arduino and an H-Bridge. The push buttons provide an interactive way to change the motor's behavior. The code efficiently reads input, processes the logic, and outputs the required control signals to the motor driver.
