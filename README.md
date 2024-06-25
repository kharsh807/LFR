# LFR
LFR-Line Following Robot



![image](https://github.com/kharsh807/LFR/assets/121211344/1ce53c92-b77c-404d-9e36-03e0aceec33c)
## How to Build

1. **Assemble the Chassis**: Mount the motors and wheels onto the chassis.
2. **Install the Sensors**: Attach the IR sensors to the front of the robot, facing downward.
3. **Wiring**: Connect the motors to the motor driver and the IR sensors to the Arduino.
4. **Programming**: Upload the line-following code to the Arduino.
5. **Testing**: Place the robot on a track and test its ability to follow the line.


## Code
/*Run this code in arduino ide*/


## Code

```cpp
// Line Following Robot Code
const int leftSensor = 2; // left sensor connected to digital pin 2
const int rightSensor = 3; // right sensor connected to digital pin 3
const int leftMotorForward = 9; // left motor forward pin
const int leftMotorBackward = 10; // left motor backward pin
const int rightMotorForward = 5; // right motor forward pin
const int rightMotorBackward = 6; // right motor backward pin

void setup() {
  pinMode(leftSensor, INPUT);
  pinMode(rightSensor, INPUT);
  pinMode(leftMotorForward, OUTPUT);
  pinMode(leftMotorBackward, OUTPUT);
  pinMode(rightMotorForward, OUTPUT);
  pinMode(rightMotorBackward, OUTPUT);
}

void loop() {
  int leftValue = digitalRead(leftSensor);
  int rightValue = digitalRead(rightSensor);

  if (leftValue == LOW && rightValue == LOW) {
    // Move forward
    moveForward();
  } else if (leftValue == LOW && rightValue == HIGH) {
    // Turn right
    turnRight();
  } else if (leftValue == HIGH && rightValue == LOW) {
    // Turn left
    turnLeft();
  } else {
    // Stop
    stop();
  }
}

void moveForward() {
  digitalWrite(leftMotorForward, HIGH);
  digitalWrite(leftMotorBackward, LOW);
  digitalWrite(rightMotorForward, HIGH);
  digitalWrite(rightMotorBackward, LOW);
}

void turnRight() {
  digitalWrite(leftMotorForward, HIGH);
  digitalWrite(leftMotorBackward, LOW);
  digitalWrite(rightMotorForward, LOW);
  digitalWrite(rightMotorBackward, HIGH);
}

void turnLeft() {
  digitalWrite(leftMotorForward, LOW);
  digitalWrite(leftMotorBackward, HIGH);
  digitalWrite(rightMotorForward, HIGH);
  digitalWrite(rightMotorBackward, LOW);
}

void stop() {
  digitalWrite(leftMotorForward, LOW);
  digitalWrite(leftMotorBackward, LOW);
  digitalWrite(rightMotorForward, LOW);
  digitalWrite(rightMotorBackward, LOW);
}
