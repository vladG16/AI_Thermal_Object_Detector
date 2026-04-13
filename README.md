#  AI Thermal Object Detector

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLOv8-blue?style=for-the-badge&logo=yolo)

A lightweight, real-time object detection pipeline utilizing YOLOv8 and OpenCV, specifically designed for live inference on FLIR Boson thermal camera feeds. This script is optimized for uncrewed ground vehicles (UGVs) like the Clearpath Husky, processing UVC thermal video streams via Ubuntu's V4L2 drivers.

##  Features
- **Real-Time Inference:** Utilizes Ultralytics YOLOv8 `stream=True` generator for memory-efficient, low-latency processing.
- **Plug-and-Play Thermal:** Configured for V4L2 thermal cameras (FLIR Boson) on Linux environments.
- **Custom Weights:** Easily swap in custom trained model weights (e.g., `best.pt`) for specialized thermal object detection.

##  Prerequisites & Installation

To avoid system package conflicts on Ubuntu (such as the `externally-managed-environment` error), you must run this project inside an isolated Python virtual environment.

**1. Navigate to the project directory:**
```bash
cd ~/Downloads/AI_Thermal_Object_Detector
```

**2. Create a virtual environment:**
```bash
python3 -m venv venv
```

**3. Activate the virtual environment:**
```bash
source venv/bin/activate
```
> You will know it worked when your terminal prompt starts with `(venv)`.

**4. Install the required libraries:**
```bash
pip install ultralytics opencv-python
```

**5. Add your model weights:**
Place your trained YOLOv8 `.pt` model file into the root of this directory and ensure it is named `best.pt` — or update the `model_path` variable inside the script to match your filename.

---

##  Usage

Every time you open a new terminal or restart the computer, you must activate the virtual environment before running the script:

```bash
source venv/bin/activate
python3 live_test.py
```

> To exit the video stream, press `q` while the OpenCV window is active.

---

##  Troubleshooting the Camera Index

If the script immediately exits with a `Could not open thermal camera` error, your OS likely assigned a different index to the FLIR camera.

1. Open `live_test.py`
2. Locate the camera index variable (e.g., `camera_index = 1`)
3. Try changing it to `0` or `2`

You can list all connected video devices on Ubuntu by running:
```bash
ls /dev/video*
```
This will show you which index the FLIR Boson was assigned.

---

##  Project Structure
