#  AI Thermal Object Detector

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLOv8-blue?style=for-the-badge&logo=yolo)

A lightweight, real-time object detection pipeline utilizing YOLOv8 and OpenCV, specifically designed for live inference on FLIR Boson thermal camera feeds. This script is optimized for uncrewed ground vehicles (UGVs) like the Clearpath Husky, processing UVC thermal video streams via Ubuntu's V4L2 drivers.

##  Features
* **Real-Time Inference:** Utilizes Ultralytics YOLOv8 `stream=True` generator for memory-efficient, low-latency processing.
* **Plug-and-Play Thermal:** Configured for V4L2 thermal cameras (FLIR Boson) on Linux environments.
* **Custom Weights:** Easily swap in custom trained model weights (e.g., `best.pt`) for specialized thermal object detection.

##  Prerequisites

Ensure you have Python 3.8+ installed. You will need the following libraries:

```bash
pip install opencv-python ultralytics
