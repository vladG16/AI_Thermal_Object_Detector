<div align="center">
  <img src="scuba%20logo.png" width="150"/>
</div>

# AI Thermal Object Detector
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)
![YOLOv8](https://img.shields.io/badge/YOLOv8-blue?style=for-the-badge&logo=yolo)
 
A lightweight, real-time object detection pipeline utilizing YOLOv8 and OpenCV, specifically designed for live inference on FLIR Boson thermal camera feeds. This script is optimized for uncrewed ground vehicles (UGVs) like the Clearpath Husky, processing UVC thermal video streams via Ubuntu's V4L2 drivers.
 
## Features
 
- **Real-Time Inference:** Utilizes Ultralytics YOLOv8 `stream=True` generator for memory-efficient, low-latency processing.
- **Plug-and-Play Thermal:** Configured for V4L2 thermal cameras (FLIR Boson) on Linux environments.
- **Custom Weights:** Easily swap in custom trained model weights (e.g., `best.pt`) for specialized thermal object detection.
---
 
## Python Version
 
This project requires **Python 3.11**. The `best.pt` model weights were trained and exported using Python 3.11 and PyTorch — using a newer version such as 3.12 or 3.14 may cause compatibility errors with Ultralytics or PyTorch.
 
To check your Python version:
```bash
python3 --version
```
 
---
 
## Prerequisites & Installation
 
### Step 1 — Create a project folder
 
Create a folder anywhere on your system to hold this project. For example:
 
```bash
mkdir ~/projects/AI_Thermal_Object_Detector
cd ~/projects/AI_Thermal_Object_Detector
```
 
> The folder can be placed anywhere you prefer — Desktop, Documents, a dedicated projects directory, etc. Just remember where you put it.
 
---
 
### Step 2 — Set up a virtual environment
 
A virtual environment keeps this project's dependencies isolated from the rest of your system, which prevents conflicts with other Python projects. **This step is required on Ubuntu**, which will block direct `pip install` calls outside of a virtual environment.
 
Create the virtual environment inside your project folder:
```bash
python3 -m venv venv
```
 
Activate it:
```bash
source venv/bin/activate
```
 
You will know it is active when your terminal prompt starts with `(venv)`. You must activate the virtual environment **every time you open a new terminal** before running the script.
 
---
 
### Step 3 — Install dependencies
 
With the virtual environment active, install the required libraries:
```bash
pip install ultralytics opencv-python
```
 
---
 
### Step 4 — Add your model weights
 
Place your trained YOLOv8 `.pt` file into the root of your project folder and name it `best.pt`, or update the `model_path` variable inside `live_test.py` to match your filename.
 
---
 
## Usage
 
Every time you open a new terminal, navigate to your project folder and activate the virtual environment before running the script:
 
```bash
cd ~/projects/AI_Thermal_Object_Detector   # or wherever your folder is
source venv/bin/activate
python3 live_test.py
```
 
> To exit the video stream, press `q` while the OpenCV window is active.
 
---
 
## Troubleshooting the Camera Index
 
If the script exits immediately with a `Could not open thermal camera` error, your OS likely assigned a different index to the FLIR camera.
 
1. Open `live_test.py`
2. Locate the camera index variable (e.g., `camera_index = 1`)
3. Try changing it to `0` or `2`
To list all connected video devices on Ubuntu:
```bash
ls /dev/video*
```
 
This will show you which index the FLIR Boson was assigned.
 
---
 
## Project Structure
 
```text
AI_Thermal_Object_Detector/   ← your folder, wherever you created it
│
├── best.pt          # Your trained YOLOv8 weights (user provided)
├── live_test.py     # Main inference loop
├── venv/            # Python virtual environment (do not commit this)
└── README.md        # Project documentation
```
 
> **Note:** The `venv/` folder should be added to your `.gitignore` so it is never pushed to GitHub. Only commit your source code and `README.md`.
