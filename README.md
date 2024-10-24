# Self Stabilising Spoon

**Arduino-based project to assist people with Parkinson’s disease by stabilizing a spoon during meals.**

![Self-Stabilizing Spoon](./Images/SPOON_FINAL_DRAWINGS_+_3D_(FINAL)_2024-Jun-11_06-04-31PM-000_CustomizedView7454801331.png)

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Components](#components)
- [Libraries Used](#libraries-used)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

The **Self-Stabilizing Spoon** is a project designed to assist individuals with **Parkinson’s disease** or other motor control issues. The spoon is built using an **Arduino Nano**, **MPU-6050 IMU sensor**, and **servo motors**. It maintains its horizontal position by compensating for involuntary hand movements using a combination of **Kalman filters** and **PID controllers**.

---

## Features

- **Automatic Tilt Compensation**: Stabilizes the spoon based on user hand movements.
- **Kalman Filtering**: Reduces sensor noise for more accurate tilt readings.
- **PID Controllers**: Adjusts servo motors for real-time balance corrections.

---

## Components

- **Arduino Nano** (ATmega328 microcontroller)
- **MPU-6050 IMU Sensor** (3-axis gyroscope, 3-axis accelerometer)
- **2 Servo Motors**
- **Breadboard and jumper wires**
- **9V Battery**
- **Spoon and enclosure materials**

---

## Libraries Used

This project requires several libraries, available in this repository or via the Arduino Library Manager:

- **Wire.h**: For I2C communication with the MPU-6050.
- **Kalman.h**: Implements a Kalman filter for accurate tilt angle readings.
- **PID_v1.h**: Handles the proportional, integral, and derivative control for the servos.
- **Servo.h**: Controls the movement of the servo motors.

See the [`keywords.txt`](./Libraries/KalmanFilter-master/keywords.txt) for additional information about Kalman filter functions and PID setup. file for additional information about Kalman filter functions and PID setup.

---

## How It Works

1. **IMU Data Collection**: The MPU-6050 gathers raw acceleration and gyroscope data.
2. **Kalman Filter**: Processes the data to estimate accurate tilt angles, minimizing noise.
3. **PID Control**: PID controllers calculate the required correction angles for the servos to maintain a stable spoon position.
4. **Servo Movement**: The servos receive the output from the PID controllers and adjust the spoon's tilt accordingly.

---

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo/self-stabilizing-spoon.git
   cd self-stabilizing-spoon
   ```
2. Install the necessary libraries via the Arduino IDE:
   - Kalman Filter (`Kalman.h`)
   - PID Controller (`PID_v1.h`)
   - Servo Control (`Servo.h`)
   - Wire (for I2C communication)

3. Wire the hardware components according to the design.

4. Upload the provided code to the Arduino Nano.

5. Power the system using a 9V battery and observe the stabilisation of the spoon as it compensates for hand movements.

---

## Future Improvements

- **PID Tuning**: Adjust the proportional, integral, and derivative values for more precise control.
- **Advanced Filtering**: Implement alternative filtering techniques for improved noise reduction.
- **Additional Sensors**: Integrate more sensors for enhanced motion tracking and control.

---

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for improvements or bug fixes.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
