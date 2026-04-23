# YOLOv10 Blood Cell Detection: A Robustness Analysis

## Description
This repository contains the code and models for my MSc dissertation at the University of East London. The project investigates the vulnerability of YOLOv10‑based blood cell detectors to plain (non‑adversarial) patches, establishing a baseline for security evaluations in medical AI.

## Key Features
- **Combined Dataset:** Code to merge and preprocess BCCD and TXL‑PBC datasets into YOLO format.
- **Model Training:** Scripts to train YOLOv10m and YOLOv8s on the combined dataset.
- **Patch Attack Evaluation:** A framework to overlay plain patches (gray, white, black, shaky) at random positions and evaluate counting accuracy.
- **CNN Comparison:** A ResNet‑18 classifier on cropped cells for classification robustness analysis.

## Main Results
- **YOLOv10m Baseline:** Achieved **94.80%** (RBC), **98.36%** (WBC), and **95.65%** (Platelets) counting accuracy.
- **Vulnerability to Plain Patches:** The same model showed a ≈30 percentage point drop in RBC accuracy with a 160×160 pixel patch.
- **Model Dependency:** YOLOv8s displayed different vulnerability patterns, including a surprising improvement in platelet accuracy with solid patches.

| Model     | Condition | RBC Acc | WBC Acc | Platelets Acc |
|-----------|-----------|---------|---------|---------------|
| YOLOv10m  | Clean     | 94.80%  | 98.36%  | 95.65%        |
| YOLOv10m  | Gray patch| 65.10%  | 93.93%  | 83.77%        |
| YOLOv8s   | Clean     | 90.45%  | 88.52%  | 85.51%        |
| YOLOv8s   | Gray patch| 68.13%  | 78.03%  | 96.23%        |

*(Full results tables are in the dissertation.)*

## Getting Started
### Prerequisites
- **Hardware:** A GPU is recommended for training (used a Tesla T4 on Google Colab).
- **Software:** Python 3.12. Ensure the environment has the necessary libraries.

### Installation and Setup
1. **Clone the repository**
   ```bash
   git clone https://github.com/itskareem01/adversarial-patch-blood-cell-detection.git
   cd adversarial-patch-blood-cell-detection
