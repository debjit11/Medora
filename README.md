# Smart Iron Dome — AI-Powered Autonomous Threat Defense

> Low-cost prototype for detecting and visually simulating interceptions of small aerial threats.


## Overview
Smart Iron Dome is a demo platform that uses inexpensive sensors (HC-SR04, ESP32-CAM), a YOLO-based vision stack, and a gamified React dashboard to detect, classify, visualize, and simulate the neutralization of micro threats like drones and balloons. Intended for education, hackathons, and prototyping.

## Features
- Servo-driven ultrasonic radar sweep with real-time UI blips
- ESP32-CAM → server inference using YOLO + OpenCV
- Auto & manual fire modes (laser visual only)
- WebSocket telemetry for angle/distance/detections
- Scoreboard, leaderboard, and configurable penalties
- Modular: swap models, change hardware, or adapt UI

## System Architecture
1. **MCU/Sensors:** Servo + HC-SR04 + laser + optional buzzer
2. **Camera:** ESP32-CAM streams frames to server
3. **Server:** Receives frames, runs YOLO inference, decides threat
4. **Actuation:** MCU receives `FIRE`/`STOP` commands and simulates with laser
5. **UI:** React dashboard connects over WebSocket, displays radar and controls

## Hardware (approximate)
- ESP32-CAM
- Arduino Uno / Raspberry Pi Pico W
- HC-SR04 ultrasonic sensor
- SG90 micro servo
- Low-power laser diode (eye-safe)
- Buzzer, jumper wires, breadboard, power supply
- Optional: Raspberry Pi / laptop for inference

## Software (high-level)
- Python (OpenCV, PyTorch, Ultralytics)
- Arduino IDE or MicroPython
- React + Tailwind for UI
- WebSockets for real-time comms

## Quickstart (minimal example)

### 1. Prepare inference host
```bash
python -m venv venv
# macOS / Linux:
source venv/bin/activate
# Windows:
# venv\Scripts\activate

pip install -U pip
pip install opencv-python torch torchvision ultralytics websockets flask
