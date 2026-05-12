# Real-Time Semantic Segmentation & Vision-Based Heading Controller

A real-time robotics perception and navigation system that combines **Deep Learning**, **Computer Vision**, and **Control Systems** for autonomous scene understanding and motion control.

The system performs semantic segmentation on live RGB video streams and uses the segmented scene information to generate intelligent navigation decisions such as:

- Direction correction
- Speed adjustment
- Path following
- Emergency stopping

---

https://github.com/user-attachments/assets/d50d8e9c-3181-4024-9e8e-66896d247f51

---

# 📌 Project Overview

This project uses a lightweight semantic segmentation model to process video frames captured from an **Intel RealSense D455 RGB-D camera** at:

- **Resolution:** 1280 × 720
- **Frame Rate:** 30 FPS

The predicted semantic masks are then used by a **vision-based heading controller** to guide robot navigation safely in real time.

---

# 🧠 Semantic Classes

The model segments each frame into the following navigation-critical classes:

| Class | Purpose |
|---|---|
| Human | Detect pedestrians and trigger emergency stop |
| Obstacle | Detect blocking objects and trigger emergency stop |
| Road | Identify drivable area |
| Sidewalk | Detect road boundaries |
| Speed Breaker | Reduce speed near bumps |

---

# 🖼️ System Results

## Input & Segmentation Results

Each prediction contains:

1. Original RGB Image  
2. Ground Truth Mask  
3. Predicted Semantic Mask  

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/5986b342-5a1f-441b-8152-b70b299b3ed4" />

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/8af81765-a782-467b-8f04-722e35aa2a0d" />

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/c8c8d406-1d55-4d03-bfc7-7b4711505ce8" />

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/158368a4-09eb-46f8-abb2-23e9aa9b4706" />

<img width="1182" height="234" alt="image" src="https://github.com/user-attachments/assets/ad2b568a-9e72-43a0-92e1-d423b8339e81" />

---

# ⚙️ System Pipeline

```text
Input RGB Video
      │
      ▼
Frame Extraction
      │
      ▼
Preprocessing & Resizing
      │
      ▼
Semantic Segmentation Model
      │
      ▼
Class Mask Prediction
      │
      ▼
Scene Understanding
      │
      ▼
Heading Controller & Decision Logic
      │
      ▼
Robot Motion Commands
```

---

# 📊 Model Performance

The model was evaluated using semantic segmentation metrics on the test dataset.

## Overall Metrics

| Metric | Score |
|---|---:|
| Pixel Accuracy | 99.28% |
| Mean IoU | 95.61% |

---

## Per-Class Performance

| Class | IoU | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Human | 98.57% | 99.51% | 99.06% | 99.28% |
| Obstacle | 98.00% | 99.55% | 98.43% | 98.99% |
| Road | 99.04% | 99.44% | 99.59% | 99.52% |
| Sidewalk | 98.08% | 99.35% | 98.72% | 99.03% |
| Speed Breaker | 84.33% | 89.72% | 93.35% | 91.50% |

---

# 🤖 Navigation & Control Logic

The segmentation output is used for autonomous navigation decisions.

| Scene Condition | Robot Action |
|---|---|
| Road is clear | Maintain / increase speed |
| Road center shifted | Adjust steering angle |
| Speed breaker detected | Reduce speed |
| Human detected nearby | Emergency stop |
| Obstacle detected nearby | Emergency stop |
| Path not centered | Correct heading direction |

---

# ✨ Features

- ✅ Real-time semantic segmentation
- ✅ Lightweight model for robotics applications
- ✅ RGB video processing pipeline
- ✅ Automated frame extraction
- ✅ Semantic mask generation
- ✅ Colored prediction visualization
- ✅ Heading/yaw correction system
- ✅ Speed control near speed breakers
- ✅ Emergency stop system
- ✅ Segmented output video generation
- ✅ Camera calibration using checkerboard images

---

# 🛠️ Tech Stack

- Python
- PyTorch
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Deep Learning
- Computer Vision
- Semantic Segmentation
- Robotics Control Systems

---

# 🚀 Installation

## Clone Repository

```bash
git clone <your-repository-link>
cd <repository-name>
```

---

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

# ▶️ Usage

## Run Semantic Segmentation

```bash
python src/inference.py --input sample_video.mp4 --output segmented_output.mp4
```

---

## Run Heading Controller

```bash
python src/controller.py --input sample_video.mp4
```

---

# 📦 Model Weights

The trained weights are not included directly in this repository due to file size limitations.

Add your weights link below:

```text
Weights: <Google Drive / OneDrive / GitHub Release Link>
```

---

# 👩‍💻 Contributors

- Amna
- Sana
- Roha

---

# 📚 Project Domain

**Robotics • Deep Learning • Computer Vision • Autonomous Navigation • Semantic Segmentation • Vision-Based Control**

---

# 📄 License

This project was developed for academic and research purposes.
