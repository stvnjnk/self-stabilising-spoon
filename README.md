# self-stabilising-spoon
Arduino based self stabilising spoon

Self-Stabilizing Spoon Project

This repository contains the code and documentation for a Self-Stabilizing Spoon, designed to assist individuals with Parkinson's disease or similar conditions in stabilizing their spoon during meals. The spoon uses an Inertial Measurement Unit (IMU), Kalman filters, and PID controllers to maintain its horizontal position, compensating for unintentional hand movements.

Project Overview

This project aims to create a self-stabilizing spoon for people with motor control issues, particularly those suffering from Parkinson’s disease. The spoon stabilizes itself automatically by correcting tilt and angle through two servo motors.

Features
Kalman Filter: For precise angle estimation from noisy IMU data.
PID Control: For balancing the spoon along X and Y axes.
Servo Motors: Adjusts the spoon’s position based on the control signals from the PID controller.
Components

Arduino Nano
MPU-6050 (6-axis IMU sensor)
2 x Servo Motors
9V Battery
Mini Breadboard and jumper wires
Spoon and enclosure material
For a detailed overview of these components, check out the lab manual​(Self-Stabilizing Spoon …).

Libraries

The project relies on several libraries to manage sensor data and control the servos:

Wire.h: For I2C communication with the MPU-6050.
Kalman.h: Provides methods for applying Kalman filtering to IMU data.
Functions like getAngle(), setQangle(), and setRmeasure() are used to manipulate and retrieve filtered sensor data​(keywords).
PID_v1.h: Implements PID control for adjusting the servo motors based on the filtered sensor data.
Servo.h: Controls the two servos responsible for spoon stabilization.
How It Works

IMU Data Processing: The MPU-6050 provides raw acceleration and gyroscope data for both X and Y axes.
Kalman Filter Application: This data is passed through a Kalman filter to estimate the true tilt angles with minimized noise.
PID Controller: The PID controllers then calculate the necessary corrections to maintain balance by adjusting the angles of the two servos.
Servo Adjustment: The servos adjust the position of the spoon based on the outputs from the PID controllers, ensuring it stays stable even when the user’s hand tilts.
Code Example
cpp
Copy code
#include <Wire.h>
#include <Kalman.h>
#include <PID_v1.h>
#include <Servo.h>

Kalman kalmanX, kalmanY;
Servo servo1, servo2;
double InputX, OutputX, SetpointX;
double InputY, OutputY, SetpointY;
PID PIDX(&InputX, &OutputX, &SetpointX, 1, 0, 0, DIRECT);
PID PIDY(&InputY, &OutputY, &SetpointY, 1, 0, 0, DIRECT);

void setup() {
  Serial.begin(9600);
  Wire.begin();
  servo1.attach(2);
  servo2.attach(3);
  // Further setup...
}

void loop() {
  // Get sensor data, apply Kalman filter and PID control
  PIDX.Compute();
  PIDY.Compute();
  servo1.write(OutputX);
  servo2.write(OutputY);
}
Installation

Clone the repository:
bash
Copy code
git clone https://github.com/your-repo/self-stabilizing-spoon.git
Install the necessary libraries via the Arduino IDE:
Kalman Filter (available in the Kalman.h file included)
PID_v1
Servo
Wire (default Arduino library)
License

This project is licensed under the GNU General Public License v2 as described in the LICENSE file​(gpl2).

Documentation

For detailed instructions on assembling the hardware, refer to the lab manual​(Self-Stabilizing Spoon …).
See keywords.txt for details on the Kalman library syntax coloring and method descriptions​(keywords).
Future Improvements

Fine-tuning the PID values for more responsive stabilization.
Incorporating a more advanced filter for even better noise reduction.
Adding external sensors for more accurate control.
Feel free to contribute to the project or fork it for your own developments.
