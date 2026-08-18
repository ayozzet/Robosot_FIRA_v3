# Robosot_FIRA_v3
**Complete RoboSot robot platform including 3D mechanical designs, STL files, PCB hardware, Raspberry Pi 5 setup, ESP32 firmware, ROS 2 Jazzy nodes, computer vision, and supporting documentation.**

# 🤖 RoboSot Robot Platform

A complete open-source development repository for a **RoboSot autonomous mobile robot**, containing the mechanical design, electronics, embedded firmware, ROS 2 software, computer vision, configuration files, documentation, and supporting resources required to build and operate the robot.

This repository is intended to serve as the central source of information for the RoboSot robot, from the physical hardware and PCB design to the low-level ESP32 controller and high-level ROS 2 autonomous system.

---

## 📌 Overview

The RoboSot robot is a **4-wheel omnidirectional mobile robot** designed for autonomous robotic applications and RoboSot competitions.

The system combines:

* 🛞 4-wheel omnidirectional / mecanum drive
* 🧠 Raspberry Pi 5 as the main onboard computer
* ⚙️ ESP32 for low-level motor and sensor control
* 🔌 Custom PCB electronics
* 📷 Camera-based computer vision
* 🤖 YOLO-based object detection
* 🧭 Compass / IMU-based orientation
* 🔄 Wheel encoder feedback
* 🧩 ROS 2 Jazzy for robot communication and control
* 🐍 Python-based ROS 2 nodes
* 🔧 Custom 3D-printed mechanical components

The repository is organized so that the complete robot development process can be maintained in a single location.

---

## 🏗️ System Architecture

```text
                    ┌─────────────────────────┐
                    │       ROS 2 Jazzy       │
                    │    High-Level System    │
                    └────────────┬────────────┘
                                 │
                           /robot/cmd_vel
                                 │
                    ┌────────────▼────────────┐
                    │      Raspberry Pi 5     │
                    │                         │
                    │ • ROS 2 Nodes           │
                    │ • Computer Vision       │
                    │ • YOLO Detection        │
                    │ • Navigation             │
                    │ • Robot Control         │
                    └────────────┬────────────┘
                                 │
                            Serial / USB
                                 │
                    ┌────────────▼────────────┐
                    │          ESP32           │
                    │    Low-Level Control    │
                    │                         │
                    │ • Motor Control         │
                    │ • Encoder Reading       │
                    │ • Sensor Interface      │
                    │ • Hardware Control      │
                    └───────┬─────────┬───────┘
                            │         │
                 ┌──────────▼───┐ ┌──▼───────────┐
                 │ Motor Drivers │ │   Sensors    │
                 │              │ │              │
                 │ • FL         │ │ • Encoders   │
                 │ • FR         │ │ • Compass    │
                 │ • RL         │ │ • IMU        │
                 │ • RR         │ │ • Other      │
                 └──────┬───────┘ └──────────────┘
                        │
                 ┌──────▼──────┐
                 │  4 Motors   │
                 │ Omnidirectional│
                 │    Drive    │
                 └─────────────┘
```

---

# 📁 Repository Structure

```text
RoboSot/
│
├── README.md
├── LICENSE
│
├── 01_MECHANICAL/
│   ├── 3D_MODELS/
│   ├── STL/
│   ├── STEP/
│   ├── DRAWINGS/
│   └── ASSEMBLY/
│
├── 02_ELECTRONICS/
│   ├── PCB/
│   ├── SCHEMATIC/
│   ├── GERBER/
│   ├── BOM/
│   └── DOCUMENTATION/
│
├── 03_RASPBERRY_PI/
│   ├── OS_SETUP/
│   ├── CONFIGURATION/
│   ├── CAMERA/
│   └── IMAGES/
│
├── 04_ESP32/
│   ├── FIRMWARE/
│   ├── MOTOR_CONTROL/
│   ├── ENCODER/
│   ├── SENSOR/
│   └── TEST/
│
├── 05_ROS2/
│   ├── src/
│   ├── launch/
│   ├── config/
│   ├── nodes/
│   └── scripts/
│
├── 06_COMPUTER_VISION/
│   ├── CAMERA/
│   ├── OPENCV/
│   ├── YOLO/
│   ├── MODELS/
│   └── CALIBRATION/
│
├── 07_ROBOT_TESTING/
│   ├── MOTOR_TEST/
│   ├── ENCODER_TEST/
│   ├── MOVEMENT_TEST/
│   ├── VISION_TEST/
│   └── DATA/
│
├── 08_DOCUMENTATION/
│   ├── HARDWARE/
│   ├── SOFTWARE/
│   ├── SETUP/
│   ├── WIRING/
│   └── TROUBLESHOOTING/
│
└── 09_RESOURCES/
    ├── IMAGES/
    ├── VIDEOS/
    └── REFERENCES/
```

> The folder structure can be modified as the project grows.

---

# ⚙️ Hardware

## Main Computer

**Raspberry Pi 5**

The Raspberry Pi 5 acts as the main computer for the robot and is responsible for running the ROS 2 system, computer vision, object detection, robot control, and other high-level processes.

Typical responsibilities include:

* ROS 2 Jazzy
* Camera processing
* OpenCV
* YOLO object detection
* Robot control
* Sensor data processing
* Communication with the ESP32

---

## Low-Level Controller

**ESP32**

The ESP32 handles hardware-level operations that require deterministic and fast control.

Responsibilities include:

* Motor control
* Motor direction
* PWM generation
* Encoder counting
* Sensor acquisition
* Hardware communication
* Low-level robot control

The ESP32 communicates with the Raspberry Pi 5 to exchange commands and sensor information.

---

## Drive System

The robot uses a **4-wheel omnidirectional drive system**.

The four motors are identified as:

```text
FL = Front Left
FR = Front Right
RL = Rear Left
RR = Rear Right
```

The drive system allows the robot to perform:

* Forward movement
* Reverse movement
* Left/right strafing
* Rotation
* Combined omnidirectional movement

---

# 🔌 Electronics

The electronics section contains the hardware design files used to build the robot.

It may include:

* PCB design files
* Schematics
* PCB layouts
* Gerber files
* Bill of Materials (BOM)
* Wiring diagrams
* Connector information
* Power distribution
* Motor driver connections
* Sensor connections

---

# 🧩 Mechanical Design

The mechanical design section contains the 3D models and manufacturing files used to construct the robot.

Supported files may include:

* `.STEP`
* `.STP`
* `.STL`
* `.3MF`
* CAD source files
* Engineering drawings

The repository will contain the mechanical parts required for the robot chassis, electronics mounting, sensors, cameras, motors, wheels, and other components.

---

# 📷 Computer Vision

Computer vision is an important part of the RoboSot system.

The vision subsystem may include:

* USB / CSI cameras
* OpenCV
* Image processing
* Object detection
* Color segmentation
* HSV filtering
* Camera calibration
* YOLO models
* Detection evaluation
* FPS measurement

Example processing pipeline:

```text
Camera
   │
   ▼
Image Acquisition
   │
   ▼
OpenCV Processing
   │
   ▼
YOLO / Object Detection
   │
   ▼
Detection Results
   │
   ▼
ROS 2
   │
   ▼
Robot Decision / Control
```

---

# 🤖 ROS 2

The robot software is developed using **ROS 2 Jazzy**.

The ROS 2 system provides communication between the different robot subsystems.

Typical nodes may include:

```text
Camera Node
     │
     ▼
Image Topic
     │
     ▼
Detector Node
     │
     ▼
Detection Results
     │
     ▼
Robot Control Node
     │
     ▼
/robot/cmd_vel
     │
     ▼
ESP32 / Motor Controller
```

ROS 2 topics may include resources such as:

```text
/robot/cmd_vel

/robot/cam0/raw
/robot/cam0/compressed

/robot/cam1/raw
/robot/cam1/compressed

/robot/encL
/robot/encR

/robot/compass/filter
```

The exact topic names and namespaces may change depending on the robot configuration.

---

# 🧠 Software

The project uses several software technologies.

| Component        | Technology               |
| ---------------- | ------------------------ |
| Main Computer    | Raspberry Pi 5           |
| Microcontroller  | ESP32                    |
| Operating System | Ubuntu / Raspberry Pi OS |
| Robot Framework  | ROS 2 Jazzy              |
| Programming      | Python / C++ / Arduino   |
| Computer Vision  | OpenCV                   |
| Object Detection | Ultralytics YOLO         |
| Communication    | ROS 2 / Serial / USB     |
| CAD              | CAD software             |
| PCB              | PCB design software      |

---

# 📦 Components

A complete list of components used by the robot will be maintained in:

```text
02_ELECTRONICS/BOM/
```

The component list may include:

* Raspberry Pi 5
* ESP32
* Motors
* Motor drivers
* Encoders
* Omni / mecanum wheels
* Camera modules
* IMU
* Compass / magnetometer
* PCB
* Voltage regulators
* Connectors
* Batteries
* Mechanical hardware
* Sensors
* Cables

A detailed BOM should be maintained as the hardware design evolves.

---

# 🖼️ Raspberry Pi Images

Raspberry Pi configuration and system images may be provided in:

```text
03_RASPBERRY_PI/IMAGES/
```

These resources can be used to reproduce the software environment required by the robot.

Documentation should also describe:

1. Operating system installation
2. ROS 2 installation
3. Python environment
4. Camera configuration
5. ROS 2 workspace setup
6. Required dependencies
7. Robot configuration
8. Network configuration

---

# 🔧 ESP32 Firmware

The ESP32 firmware is located under:

```text
04_ESP32/
```

The firmware is responsible for low-level hardware control.

Major functions include:

```text
ESP32
 │
 ├── Motor PWM
 ├── Motor Direction
 ├── Encoder Reading
 ├── Sensor Reading
 ├── Serial Communication
 └── Hardware Diagnostics
```

The firmware should be tested independently before integrating it with ROS 2.

---

# 🧪 Robot Testing

Testing resources are maintained under:

```text
07_ROBOT_TESTING/
```

Testing may include:

### Motor Test

Verify:

* Motor direction
* Motor speed
* Individual motor operation
* Motor driver operation

### Encoder Test

Verify:

* Encoder counting
* Encoder direction
* Encoder resolution
* Encoder-to-distance conversion

### Movement Test

Verify:

* Forward movement
* Reverse movement
* Strafing
* Rotation
* Position accuracy

### Vision Test

Verify:

* Camera FPS
* Detection FPS
* Object detection accuracy
* Detection confidence
* Detection distance

---

# 📊 Testing Data

Robot test data can be stored in:

```text
07_ROBOT_TESTING/DATA/
```

Possible data includes:

* Encoder counts
* Estimated distance
* Actual distance
* Robot speed
* Detection confidence
* FPS
* Detection count
* Test duration
* Motor performance

Example:

```text
Estimated Distance : 0.50 m
Actual Distance    : 0.501 m
Encoder Left       : -19296
Encoder Right      : -21750
FPS                : XX.XX
Detection Count    : XX
Confidence         : XX.XX
```

---

# 🚀 Installation

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

```bash
cd YOUR_REPOSITORY
```

---

## 2. Install ROS 2

Install **ROS 2 Jazzy** according to the official ROS 2 installation instructions for the target operating system.

---

## 3. Create the ROS 2 Workspace

Example:

```bash
mkdir -p ~/robosot_ws/src
cd ~/robosot_ws/src
```

Clone or copy the ROS 2 packages into the workspace.

---

## 4. Build the Workspace

```bash
cd ~/robosot_ws
source /opt/ros/jazzy/setup.bash
colcon build
```

Then:

```bash
source install/setup.bash
```

---

# ▶️ Running the Robot

The exact launch procedure depends on the current robot configuration.

A typical startup sequence may be:

```text
1. Power ON robot
        ↓
2. Start ESP32 firmware
        ↓
3. Start Raspberry Pi 5
        ↓
4. Start ROS 2
        ↓
5. Start camera node
        ↓
6. Start detection node
        ↓
7. Start sensor nodes
        ↓
8. Start robot control node
        ↓
9. Start autonomous behaviour
```

Example:

```bash
ros2 launch robosot_bringup robot.launch.py
```

> The launch command above is an example and should be replaced with the actual launch file used by the project.

---

# 🛠️ Development

This repository is continuously developed and may contain experimental code.

Before modifying the robot:

1. Test hardware independently.
2. Verify motor direction.
3. Verify encoder operation.
4. Verify sensor communication.
5. Verify ROS 2 topics.
6. Test individual nodes.
7. Test the complete system.

For robot movement testing, always ensure the robot is safely elevated or operated in a controlled environment before enabling the motors.

---

# 📝 Documentation

Additional documentation can be found under:

```text
08_DOCUMENTATION/
```

Recommended documentation includes:

* Hardware setup
* Wiring diagrams
* PCB documentation
* Mechanical assembly
* Raspberry Pi setup
* ESP32 firmware setup
* ROS 2 setup
* Camera setup
* YOLO model setup
* Calibration procedure
* Motor calibration
* Encoder calibration
* Troubleshooting
* Robot operation

---

# 📜 License

This project is released under the license specified in:

```text
LICENSE
```

Please check the license before using, modifying, or redistributing the hardware designs, software, and other project resources.

---

# 👨‍💻 Project

**RoboSot Autonomous Robot Platform**

Developed for robotics research, education, experimentation, and RoboSot competition applications.

---

# ⭐ Repository Goals

The main goals of this repository are to:

* Provide a complete record of the RoboSot robot development.
* Make the robot hardware reproducible.
* Maintain all mechanical design files.
* Maintain PCB and electronics documentation.
* Maintain ESP32 firmware.
* Maintain ROS 2 software.
* Document Raspberry Pi configuration.
* Document robot assembly and wiring.
* Provide testing procedures and results.
* Support future development and additional robot units.

---

# 🚧 Project Status

**Status: Active Development**

The hardware, firmware, ROS 2 software, computer vision system, and autonomous behaviour are continuously being developed and improved.

---

## 📌 Note

This repository is intended to contain the **complete development resources for the RoboSot platform**, including hardware, firmware, software, testing, documentation, and supporting files.

As the robot evolves, files and directory structures may change to reflect new hardware revisions, software versions, and competition requirements.

