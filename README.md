# 🤖 Practical Robotics – Autonomous Differential-Drive Robot

This project showcases the design, assembly, and control of a **differential-drive mobile robot** equipped with autonomous navigation, localization, and visual perception capabilities.

This robot combines sensor fusion, motor control, and mapping techniques to explore a grid-based maze and avoid obstacles using SLAM and computer vision.

![image](https://github.com/user-attachments/assets/c2324bad-2b3f-4908-980f-300dd1c13224)


## 🛠️ Hardware Components

- Arduino Robotics Board (ARB)
- TB6612FNG Dual Motor Driver
- Raspberry Pi 4 (with camera)
- USB to Serial UART HAT
- Micro SD with RPi OS
- Power Bank (USB-C)
- 2 Wheels + Ball Castor
- Sharp GP2Y0E02B IR Sensor
- 4 x Ultrasonic Sensors
- IR Sensor

---

## ⚙️ Key Functionalities

### 🧭 Motion Control & Localization

- **Wheel Encoder Integration**  
  Measures distance and speed (12 pulses/rev).  
  Ideal: 1200 pulses, Actual: ~894 pulses.

- **Straight Line Correction**
  - PID Controller (with low-pass filtering, derivative on measurement, output clamping)
  - Experimental PWM bias (0.017) applied to left wheel

- **Turning & Orientation**
  - Calculated angular displacement from wheel motion
  - Wall alignment algorithm for accurate 90° turns

---

### 🧠 Vision-Based Navigation

- **OpenCV-Based Detection**
  - Color masking to isolate target blobs
  - `SimpleBlobDetector` for shape recognition
  - ArUco tag detection for orientation and obstacle recognition

---

### 🗺️ Mapping & Path Planning

- **Occupancy Grid Mapping**
  - 22x17 matrix (each cell = 10x10 cm²)
  - Walls and obstacles marked using IR/Ultrasonic sensor data

- **SLAM (Simultaneous Localization and Mapping)**
  - Filters noisy sensor data using thresholding
  - Efficient environment exploration and mapping

- **A* Pathfinding Algorithm**
  - Optimized using Manhattan Distance heuristic
  - Plans shortest path from start to goal in a known map

---

## 🧪 Challenges & Solutions

| Challenge                           | Solution                                                                 |
|------------------------------------|--------------------------------------------------------------------------|
| Noisy sensor readings              | Thresholding and error rejection                                         |
| Robot drifting during motion       | PID controller + experimental bias calibration                           |
| Derivative instability in PID      | Clamping + smoothing via low-pass filter                                 |
| Obstacle detection orientation     | Pre-turn wall alignment using IR sensors and vision feedback             |
| SLAM inconsistencies               | Defined map boundaries + conservative obstacle detection thresholds      |

---

## 🎥 Demo

[Google Drive](https://drive.google.com/file/d/1ykf35T0uxLuvQtm6LJtfaLc6Gzhy7us1/view?usp=sharing)

---

## 👨‍💻 Author

**Aditya Johorey**  
MSc in Intelligent Robotics – University of York  
[LinkedIn](https://linkedin.com/in/adityajohorey) | [GitHub](https://github.com/yourusername)

---

## 📎 Project Modules Overview

- `hardware/` – Assembly instructions and component specs  
- `code/` – Arduino and Raspberry Pi scripts for control, sensors, and vision  
