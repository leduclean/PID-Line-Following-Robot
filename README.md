# PID Line Follower Robot

## Project Overview

A modular, extensible line-following and obstacle-avoiding robot built on Arduino. Developed as a team project during preparatory classes, the robot uses infrared sensors and PWM motor control with a PID loop to follow lines smoothly and reliably.

## Hardware Configuration

* **Microcontroller:** Arduino Uno (with custom shield for power distribution and signal routing)
* **Motor Driver:** L298N dual H-bridge module for two DC motors
* **Motors:** Two DC wheels mounted on a custom chassis
* **Line Sensors:** Three KY-033 infrared reflectance sensors (left, center, right)
* **Power Supply:** 12 V rechargeable battery pack (replaces original disposable batteries)
* **Optional:** Infrared remote control for manual commands (forward, backward, left, right, stop)

## Software Overview

The firmware is organized into clear, separate modules for easy maintenance and future extensions:

* **Main Sketch (`ROBOT.ino`):** Initializes hardware, starts the control loop.
* **Robot Module:** High-level control logic, state management (manual vs. auto modes), PID setup.
* **Motor Module:** Low-level motor driver interface (direction, PWM speed control).
* **Sensor Module:** Reads and interprets line sensor values into an error metric.
* **PID Controller:** Continuously computes correction based on line error and adjusts motor speeds.

> *Note:* The object-oriented structure keeps each component isolated but detailed class explanations are omitted here for clarity.

## Installation & Usage

1. **Clone the Repository**

   ```bash
   git clone https://github.com/leduclean/PROJET-ROBOT.git
   cd PROJET-ROBOT
   ```
2. **Open in Arduino IDE**

   * Open `ROBOT.ino` in Arduino IDE or PlatformIO.
3. **Configure Pins**

   * Review and update pin definitions in `ROBOT_CONFIG.h` to match your wiring.
4. **Upload**

   * Compile and upload to your Arduino board.
5. **Run**

   * Place the robot on a high-contrast line.
   * Switch to automatic mode to enable PID line-following.
   * Use the IR remote for manual testing if desired.

## PID Tuning

Initial PID parameters were obtained using Ziegler–Nichols and fine-tuned by experiments:

```
Kp = 19
Ki = 85
Kd = 20
```

Adjust these in the setup section of `Robot.cpp` as needed for different chassis or sensor layouts.

