# Real-Time Semantic Segmentation & Vision-Based Heading Controller

<img width="750" height="368" alt="image" src="https://github.com/user-attachments/assets/6370c5f5-bcee-430d-850c-278003d24308" />
<img width="750" height="368" alt="image" src="https://github.com/user-attachments/assets/0c10c2b0-ccf6-48da-9621-328f54464419" />
<img width="750" height="368" alt="image" src="https://github.com/user-attachments/assets/38a0653e-e7d1-4e7a-903a-452277de1810" />


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

### Model Prediction Results

Each result shows:

1. Original RGB image  
2. Ground truth semantic mask  
3. Model prediction

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/5986b342-5a1f-441b-8152-b70b299b3ed4" />
<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/8af81765-a782-467b-8f04-722e35aa2a0d" />
<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/c8c8d406-1d55-4d03-bfc7-7b4711505ce8" />
<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/158368a4-09eb-46f8-abb2-23e9aa9b4706" />
<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/ad2b568a-9e72-43a0-92e1-d423b8339e81" />

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

- Amna
- Sana
- Roha


---

## Project Category

**Robotics | Deep Learning | Computer Vision | Semantic Segmentation | Autonomous Navigation | Vision-Based Control**

---

## License

This project is developed for academic and research purposes.
