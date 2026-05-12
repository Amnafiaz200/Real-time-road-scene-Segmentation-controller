# Real-Time Semantic Segmentation & Vision-Based Heading Controller

<p align="center">
  <img src="assets/sample_video_1_frames.png" alt="Sample video frame extraction" width="900">
</p>

<p align="center">
  <b>Real-time robotics perception pipeline for semantic scene understanding, safe navigation, and vision-based heading control.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Task-Semantic%20Segmentation-blue" />
  <img src="https://img.shields.io/badge/Domain-Robotics-green" />
  <img src="https://img.shields.io/badge/Input-RGB%20Video-orange" />
  <img src="https://img.shields.io/badge/Control-Vision--Based%20Heading-purple" />
</p>

---

## Project Overview

This project combines **Deep Learning** and **Control Systems** to build a real-time perception and navigation system for robotics.

The system receives a **1280 × 720 RGB video feed at 30 FPS** from an Intel RealSense D455 RGB-D camera and performs semantic segmentation on each frame. The segmentation output is then used by a vision-based heading controller to generate navigation decisions such as speed adjustment, angular correction, and emergency stop.

The model segments every frame into 5 navigation-critical classes:

| Class | Purpose |
|---|---|
| Human | Detect pedestrians and trigger emergency stop |
| Obstacle | Detect blocking objects and trigger emergency stop |
| Road | Identify drivable path |
| Sidewalk | Understand path boundaries |
| Speed Breaker | Reduce speed when nearby |

---

## Visual Results From Notebook

### Sample Frames Extracted From Videos

<p align="center">
  <img src="assets/sample_video_1_frames.png" alt="Video 1 extracted frames" width="900">
</p>

<p align="center">
  <img src="assets/sample_video_2_frames.png" alt="Video 2 extracted frames" width="900">
</p>

---

### Dataset Mask Overlay Examples

These images show the RGB frame together with its colored semantic mask overlay.

<p align="center">
  <img src="assets/mask_overlay_example_1.png" alt="Mask overlay example 1" width="420">
  <img src="assets/mask_overlay_example_2.png" alt="Mask overlay example 2" width="420">
</p>

<p align="center">
  <img src="assets/mask_overlay_example_3.png" alt="Mask overlay example 3" width="420">
</p>

---

### Model Prediction Results

Each result shows:

1. Original RGB image  
2. Ground truth semantic mask  
3. Model prediction

<p align="center">
  <img src="assets/prediction_result_1.png" alt="Prediction result 1" width="900">
</p>

<p align="center">
  <img src="assets/prediction_result_2.png" alt="Prediction result 2" width="900">
</p>

<p align="center">
  <img src="assets/prediction_result_3.png" alt="Prediction result 3" width="900">
</p>

<p align="center">
  <img src="assets/prediction_result_4.png" alt="Prediction result 4" width="900">
</p>

<p align="center">
  <img src="assets/prediction_result_5.png" alt="Prediction result 5" width="900">
</p>

---

## System Pipeline

```text
Input RGB Video
      |
      v
Frame Extraction
      |
      v
Preprocessing & Resizing
      |
      v
Lightweight Semantic Segmentation Model
      |
      v
Class Mask Prediction
      |
      v
Scene Understanding
      |
      v
Heading Controller + Decision Logic
      |
      v
Robot Motion Commands
```

---

## Model Performance

The model was evaluated on the test set using 5 required semantic classes.

| Metric | Result |
|---|---:|
| Pixel Accuracy | 99.28% |
| Mean IoU | 95.61% |

### Per-Class Results

| Class | IoU | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Human | 98.57% | 99.51% | 99.06% | 99.28% |
| Obstacle | 98.00% | 99.55% | 98.43% | 98.99% |
| Road | 99.04% | 99.44% | 99.59% | 99.52% |
| Sidewalk | 98.08% | 99.35% | 98.72% | 99.03% |
| Speed Breaker | 84.33% | 89.72% | 93.35% | 91.50% |

---

## Control Actions

The segmentation output is used to make robotics navigation decisions in real time.

| Scene Condition | Robot Action |
|---|---|
| Road is clear | Maintain or increase linear velocity |
| Road center is shifted | Adjust angular velocity |
| Speed breaker is detected nearby | Decrease linear velocity |
| Human is detected nearby | Emergency stop |
| Obstacle is detected nearby | Emergency stop |
| Path is not centered | Correct heading/yaw direction |

---

## Features

- Real-time semantic segmentation on `.mp4` video input
- Lightweight deep learning model for robotics applications
- Frame extraction and dataset preparation pipeline
- Colored mask generation for visual inspection
- RGB, ground truth, and prediction visualization
- Camera calibration using checkerboard images
- Vision-based heading/yaw control
- Speed reduction near speed breakers
- Emergency stop for humans and obstacles
- Segmented output video generation

---

## Tech Stack

- Python
- OpenCV
- PyTorch
- NumPy
- Matplotlib
- Pandas
- Computer Vision
- Semantic Segmentation
- Robotics Control

---

## Repository Structure

```text
.
├── assets/
│   ├── sample_video_1_frames.png
│   ├── sample_video_2_frames.png
│   ├── mask_overlay_example_1.png
│   ├── mask_overlay_example_2.png
│   ├── mask_overlay_example_3.png
│   ├── prediction_result_1.png
│   ├── prediction_result_2.png
│   ├── prediction_result_3.png
│   ├── prediction_result_4.png
│   └── prediction_result_5.png
├── notebooks/
│   └── Real-Time Semantic Segmentation for Vision-Based Heading Control.ipynb
├── src/
│   ├── inference.py
│   ├── controller.py
│   └── model.py
├── report/
│   └── report.pdf
├── requirements.txt
└── README.md
```

---

## Usage

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Semantic Segmentation on a Video

```bash
python src/inference.py --input sample_video.mp4 --output segmented_output.mp4
```

### Run Segmentation With Heading Controller

```bash
python src/controller.py --input sample_video.mp4
```

---

## Model Weights

The trained model weights are not stored directly in this repository because the file may be large.

Add your model weights link here:

```text
Weights: <paste Google Drive / OneDrive / GitHub Release link here>
```

---

## Future Improvements

- Add ROS/ROS2 integration for robot deployment
- Use RealSense depth data for distance-aware decisions
- Improve speed breaker detection with more diverse training samples
- Deploy the model on edge devices such as NVIDIA Jetson
- Add PID-based smooth heading control
- Improve robustness in low-light and crowded scenes

---

## Contributors

AMNA
SANA
ROHA

---

## Project Category

**Robotics | Deep Learning | Computer Vision | Semantic Segmentation | Autonomous Navigation | Vision-Based Control**

---

## License

This project is developed for academic and research purposes.
