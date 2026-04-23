# YOLOv10 Blood Cell Detection: A Robustness Analysis

## Description
This repository contains the code and models for my MSc dissertation at the University of East London. The project investigates the vulnerability of YOLOv10‑based blood cell detectors to plain (non‑adversarial) patches, establishing a baseline for security evaluations in medical AI.

## Key Features
- **Combined Dataset:** Code to merge and preprocess BCCD and TXL‑PBC datasets into YOLO format.
- **Model Training:** Scripts to train YOLOv10m and YOLOv8s on the combined dataset.
- **Patch Attack Evaluation:** A framework to overlay plain patches (gray, white, black, shaky) at random positions and evaluate counting accuracy.
- **CNN Comparison:** A ResNet‑18 classifier on cropped cells for classification robustness analysis.

## Reproduction Steps (Run notebooks in this order)

### 1. `Blood_Cell_project.ipynb`
- **What it does:**  
  - Trains **YOLOv10m** on the BCCD dataset (clean baseline).  
  - Then merges BCCD with the **TXL‑PBC** dataset.  
  - Trains YOLOv10m on the **combined dataset**.  
  - Evaluates clean counting accuracy on the test set.
- **Outputs:** Trained model weights, clean baseline results.

### 2. `patch_attack_evaluation.ipynb`
- **What it does:**  
  - Loads the YOLOv10m model trained on the combined dataset.  
  - Applies plain patches (gray, white, black, shaky) at random positions.  
  - Computes counting accuracy drop.  
- **Outputs:** Patched accuracies.

### 3. `patch_attack__evaluation_yolov8s.ipynb`
- **What it does:**  
  - Trains **YOLOv8s** on the **combined dataset**.  
  - Evaluates clean baseline.  
  - Applies the same plain patches and computes accuracy drop.  
- **Outputs:** YOLOv8s clean and patched accuracies.

### 4. `patch_attach__evaluation_CNN.ipynb`
- **What it does:**  
  - Crops individual cells from the combined dataset.  
  - Trains a **ResNet‑18** classifier on cropped cells.  
  - Evaluates clean classification accuracy.  
  - Applies patches (160×160) to cropped cells and computes accuracy drop.
- **Outputs:** CNN clean and patched accuracies.

## Main Results Summary
| Model     | Condition | RBC Acc | WBC Acc | Platelets Acc |
|-----------|-----------|---------|---------|---------------|
| YOLOv10m  | Clean     | 94.80%  | 98.36%  | 95.65%        |
| YOLOv10m  | Gray patch| 65.10%  | 93.93%  | 83.77%        |
| YOLOv8s   | Clean     | 90.45%  | 88.52%  | 85.51%        |
| YOLOv8s   | Gray patch| 68.13%  | 78.03%  | 96.23%        |
| CNN       | Clean     |                     100.00%       |
| CNN       | Gray patch|                     84.80%        |


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
