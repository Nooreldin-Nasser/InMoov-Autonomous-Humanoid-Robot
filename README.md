# InMoov – Autonomous Humanoid Robot

## Overview

An autonomous humanoid robot based on the open-source InMoov platform, developed as a graduation project at the Faculty of Engineering, Ain Shams University.

The project aimed to develop a robotic system capable of autonomous navigation and human-robot interaction by integrating perception, localization, mapping, navigation, manipulation, and voice/gesture-based interaction using ROS.

## System Capabilities

The robot integrates several robotics subsystems:

* Autonomous locomotion and navigation
* Localization using wheel encoders and IMU data
* Sensor fusion using an Extended Kalman Filter (EKF)
* Environment mapping using an RGB-D camera
* Path planning and ROS Navigation Stack
* Real-time object detection using YOLOv3
* Hand/sign recognition using OpenCV
* Speech-to-text and voice-based commands
* Robotic hand control using servo motors
* Motion planning and visualization using MoveIt and RViz
* ROS-based communication between sensors, microcontrollers, and higher-level software

## Software Architecture

ROS Noetic was used as the main robotics framework, providing the communication and integration layer between the different subsystems.

The system used Arduino-based controllers for interfacing with sensors, motor drivers, and actuators. Communication between the microcontrollers and the ROS system was established using `rosserial`.

The overall architecture included:

**Sensors → Arduino / Drivers → ROS → Perception / Localization / Navigation / Manipulation → Actuators**

## Autonomous Navigation

The navigation system included several stages:

### Localization

Robot pose estimation was obtained by combining:

* Wheel encoder measurements
* IMU measurements
* Extended Kalman Filter (EKF)

The EKF was used to fuse the sensor measurements and obtain a more accurate estimate of the robot's position and orientation.

### Mapping

A Kinect RGB-D camera was used to obtain depth information.

The system converted the camera depth data into laser scan information using the ROS `depthimage_to_laserscan` package, which was then used for mapping.

### Path Planning

The project investigated path-planning techniques and integrated the selected approach with the ROS Navigation Stack.

The navigation system used `move_base` together with costmaps to plan and execute robot motion while considering obstacles in the environment.

## Object Detection

YOLOv3 was integrated into the ROS system to provide real-time object detection from camera images.

The project used the YOLO ROS package to process camera images and detect objects using a pretrained neural-network model.

The vision pipeline connected the camera input to the object-detection system through ROS image-processing components.

## Hand & Sign Recognition

A Python-based sign recognition system was developed using OpenCV.

The system detected hand signs and converted the recognized sign into an array of five values. The resulting data was published as a ROS message.

A ROS serial Arduino node subscribed to the recognition output and generated the required motor signals to control the robot's hand.

## Speech Recognition

The robot included a speech-to-text system for voice-based interaction.

The speech recognition pipeline converted spoken commands into text, which was then processed to generate robot commands and responses.

The project also explored AI-based response generation and text-to-speech interaction.

## Robotic Hands & Motion Planning

The robot's hands were driven by position-controlled servo motors.

Each hand used five servo motors controlled through Adafruit I2C-to-PWM converters and an Arduino Mega.

MoveIt was used to configure the robot's manipulation system, including:

* Motion planning groups
* Inverse kinematics
* End effectors
* Position controllers
* Visualization and planning in RViz

The robot model was represented using URDF and integrated with the ROS environment.

## Technologies

### Robotics

* ROS Noetic
* RViz
* MoveIt
* ROS Navigation Stack
* URDF

### Computer Vision & AI

* YOLOv3
* OpenCV
* CNN-based object detection

### Embedded Systems

* Arduino Mega
* Arduino-based sensor and actuator interfaces
* ROS Serial
* I2C
* PWM

### Sensors

* Kinect RGB-D camera
* IMU
* Wheel encoders
* Sound sensors

## Project Structure

The project was developed as a multidisciplinary robotics system combining:

* Mechanical design and assembly
* Embedded systems
* Robotics software
* Computer vision
* Autonomous navigation
* Human-robot interaction

## Academic Project

**Faculty of Engineering – Ain Shams University**
**Graduation Project – 2023**

Developed by a six-member multidisciplinary team.

---
