# Robot Arm Control Using MPU6050 and STM32F103C8T6

## Overview
This repository contains code for controlling a robotic arm using:
- **MPU6050 Driver**: For measuring motion and orientation.
- **Servo Motor Driver**: For precise control of the robotic arm's joints.
- **STM32F103C8T6 Driver**: As the main microcontroller for processing data and controlling the robotic arm.

The robotic arm responds to motion inputs captured by the MPU6050 sensor, processed by the STM32F103C8T6 microcontroller, and moves accordingly through servo motors.

## Features
- Real-time motion capture and orientation tracking using the MPU6050 sensor.
- Efficient servo motor control for smooth and precise arm movement.
- Modular driver implementation for reusability and easy integration.
- Fully commented and well-structured code for ease of understanding.

## Repository Structure
```
/Robot_Arm_Control
├── /Drivers
│   ├── MPU6050_Driver
│   ├── ServoMotor_Driver
│   └── STM32F103C8T6_Driver
├── /Core
│   ├── main.c
│   ├── stm32f1xx_it.c
│   └── system_stm32f1xx.c
├── /Config
│   ├── mpu6050_config.h
│   ├── servo_motor_config.h
│   └── stm32f103c8t6_config.h
├── /Docs
│   └── README.md
└── Makefile
```

## Prerequisites
- **Hardware**:
  - MPU6050 Motion Sensor
  - Servo Motors
  - STM32F103C8T6 Microcontroller
  - Power Supply
  - Robotic Arm Setup
- **Software**:
  - GCC ARM Toolchain
  - STM32CubeIDE (optional)
  - OpenOCD (for flashing)

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/ziadmohamed0/RoboticProjects.git
   cd RoboticProjects
   ```
2. Build the project using the provided `Makefile`:
   ```bash
   make
   ```
3. Flash the firmware to the STM32F103C8T6:
   ```bash
   make flash
   ```

## Usage
1. Connect the hardware components:
   - Attach the MPU6050 to the robotic arm for motion tracking.
   - Connect the servo motors to the arm joints.
   - Wire the STM32F103C8T6 to the MPU6050 and servo motors according to the configuration files.
2. Power on the system.
3. Move the MPU6050 sensor to control the robotic arm.

## Code Details
### MPU6050 Driver
- Handles I2C communication to read accelerometer and gyroscope data.
- Processes raw data for orientation and motion tracking.

### Servo Motor Driver
- Provides PWM signals for precise motor control.
- Allows customizable movement limits and speeds.

### STM32F103C8T6 Driver
- Integrates the MPU6050 and servo motor drivers.
- Implements motion control algorithms to drive the robotic arm.

## License
This project is licensed under the MIT License.

## Contributing
Contributions are welcome! Please fork the repository and create a pull request for any updates or enhancements.

## Contact
For questions or support, please contact (zizo.alprnc.90@gmail.com).

