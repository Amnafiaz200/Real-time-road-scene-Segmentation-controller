Copy this complete code and paste it directly into your `README.md` file:

````markdown
# Real-Time Semantic Segmentation & Vision-Based Heading Controller

<p align="center">
  <img width="750" height="368" alt="Segmentation Preview 1" src="https://github.com/user-attachments/assets/6370c5f5-bcee-430d-850c-278003d24308" />
</p>

<p align="center">
  <img width="750" height="368" alt="Segmentation Preview 2" src="https://github.com/user-attachments/assets/0c10c2b0-ccf6-48da-9621-328f54464419" />
</p>

<p align="center">
  <img width="750" height="368" alt="Segmentation Preview 3" src="https://github.com/user-attachments/assets/38a0653e-e7d1-4e7a-903a-452277de1810" />
</p>

<p align="center">
  <b>Real-time road-scene understanding for autonomous robotic navigation using deep learning and vision-based control.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue" />
  <img src="https://img.shields.io/badge/Framework-PyTorch-orange" />
  <img src="https://img.shields.io/badge/Computer%20Vision-OpenCV-green" />
  <img src="https://img.shields.io/badge/Task-Semantic%20Segmentation-purple" />
  <img src="https://img.shields.io/badge/Robotics-Vision%20Control-red" />
</p>

---

## Project Overview

This project combines **Deep Learning**, **Computer Vision**, and **Control Systems** to build a real-time perception and navigation pipeline for autonomous robotics.

The system processes a **1280 × 720 RGB video feed at 30 FPS** captured using an **Intel RealSense D455 RGB-D camera**. Each frame is passed through a lightweight semantic segmentation model that classifies important navigation regions and objects. The segmentation output is then used by a vision-based heading controller to make safe movement decisions such as speed control, yaw correction, and emergency stopping.

The goal of this project is not only to perform semantic segmentation, but also to connect perception with robotic decision-making in a real-time environment.

---

## Segmentation Classes

The model segments every frame into 5 navigation-critical classes:

| Class | Purpose |
|---|---|
| **Road** | Detects the drivable path for robot movement |
| **Sidewalk** | Identifies path boundaries and non-road areas |
| **Speed Breaker** | Triggers speed reduction when detected nearby |
| **Human** | Detects pedestrians and activates emergency stop |
| **Obstacle** | Detects blocking objects and activates emergency stop |

---

## Model Prediction Results

Each result below shows:

1. **Original RGB Image**  
2. **Ground Truth Semantic Mask**  
3. **Model Prediction**

<p align="center">
  <img width="1182" height="234" alt="Prediction Result 1" src="https://github.com/user-attachments/assets/5986b342-5a1f-441b-8152-b70b299b3ed4" />
</p>

<p align="center">
  <img width="1182" height="234" alt="Prediction Result 2" src="https://github.com/user-attachments/assets/8af81765-a782-467b-8f04-722e35aa2a0d" />
</p>

<p align="center">
  <img width="1182" height="234" alt="Prediction Result 3" src="https://github.com/user-attachments/assets/c8c8d406-1d55-4d03-bfc7-7b4711505ce8" />
</p>

<p align="center">
  <img width="1182" height="234" alt="Prediction Result 4" src="https://github.com/user-attachments/assets/158368a4-09eb-46f8-abb2-23e9aa9b4706" />
</p>

<p align="center">
  <img width="1182" height="234" alt="Prediction Result 5" src="https://github.com/user-attachments/assets/ad2b568a-9e72-43a0-92e1-d423b8339e81" />
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
````

---

## Model Performance

The trained segmentation model was evaluated on the test set using the 5 required semantic classes.

| Metric             |     Result |
| ------------------ | ---------: |
| **Pixel Accuracy** | **99.28%** |
| **Mean IoU**       | **95.61%** |

### Per-Class Evaluation

| Class             |    IoU | Precision | Recall | F1 Score |
| ----------------- | -----: | --------: | -----: | -------: |
| **Human**         | 98.57% |    99.51% | 99.06% |   99.28% |
| **Obstacle**      | 98.00% |    99.55% | 98.43% |   98.99% |
| **Road**          | 99.04% |    99.44% | 99.59% |   99.52% |
| **Sidewalk**      | 98.08% |    99.35% | 98.72% |   99.03% |
| **Speed Breaker** | 84.33% |    89.72% | 93.35% |   91.50% |

---

## Vision-Based Control Actions

The segmentation output is used to make real-time robotic navigation decisions.

| Scene Condition                  | Robot Action                         |
| -------------------------------- | ------------------------------------ |
| Road is clear                    | Maintain or increase linear velocity |
| Road center is shifted           | Adjust angular velocity              |
| Speed breaker is detected nearby | Decrease linear velocity             |
| Human is detected nearby         | Emergency stop                       |
| Obstacle is detected nearby      | Emergency stop                       |
| Path is not centered             | Correct heading/yaw direction        |

---

## Key Features

* Real-time semantic segmentation on `.mp4` video input
* Lightweight deep learning model for robotics applications
* Frame extraction and dataset preparation pipeline
* Colored semantic mask generation
* RGB, ground truth, and prediction visualization
* Camera calibration using checkerboard images
* Vision-based heading/yaw controller
* Linear and angular velocity decision logic
* Speed reduction near speed breakers
* Emergency stop for humans and obstacles
* Segmented output video generation

---

## Tech Stack

| Category                 | Tools / Libraries                                                |
| ------------------------ | ---------------------------------------------------------------- |
| **Programming Language** | Python                                                           |
| **Deep Learning**        | PyTorch                                                          |
| **Computer Vision**      | OpenCV                                                           |
| **Data Processing**      | NumPy, Pandas                                                    |
| **Visualization**        | Matplotlib                                                       |
| **Core Concepts**        | Semantic Segmentation, Robotics Control, Vision-Based Navigation |

---

## Usage

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run Semantic Segmentation on a Video

```bash
python src/inference.py --input sample_video.mp4 --output segmented_output.mp4
```

### 4. Run Segmentation With Heading Controller

```bash
python src/controller.py --input sample_video.mp4
```

---

## Expected Output

The system generates a segmented output video where each frame is color-coded according to the predicted semantic class. It also produces navigation decisions such as:

* Linear velocity increase or decrease
* Angular velocity correction
* Speed reduction near speed breakers
* Emergency stop near humans or obstacles

---

## Model Weights

The trained model weights are not stored directly in this repository because the file may be large.

Add the model weights link below:

```text
Weights: <paste Google Drive / OneDrive / GitHub Release link here>
```

---

## Repository Structure

```text
.
├── README.md
├── requirements.txt
├── src/
│   ├── inference.py
│   ├── controller.py
│   └── model.py
├── notebooks/
│   └── training_notebook.ipynb
├── assets/
│   └── result_images/
├── outputs/
│   └── segmented_videos/
└── report/
    └── project_report.pdf
```

---

## Future Improvements

* Deploy the model on edge devices such as NVIDIA Jetson Nano or Raspberry Pi
* Integrate depth information from the RealSense D455 camera
* Improve speed breaker detection accuracy
* Add ROS/ROS2 support for real robot deployment
* Improve controller smoothness using PID tuning
* Train on a larger and more diverse dataset
* Test robustness under different lighting and road conditions

---

## Contributors

* Amna
* Sana
* Roha

---

## Project Category

**Robotics | Deep Learning | Computer Vision | Semantic Segmentation | Autonomous Navigation | Vision-Based Control**

---

## License

This project is developed for academic and research purposes.

````

For GitHub repo description, use this:

```text
Real-time semantic segmentation and vision-based heading controller for autonomous robotic navigation using RGB video input.
````

Suggested repository name:

```text
real-time-semantic-segmentation-heading-controller
```
