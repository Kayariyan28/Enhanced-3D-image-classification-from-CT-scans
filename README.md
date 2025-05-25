<!-- PROJECT TITLE -->
# Volumetric Chest CT Triage 🚑🧠📊
*A baseline 3-D CNN pipeline for radiology-grade triage with Grad-CAM explainability.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![TensorFlow](https://img.shields.io/badge/Built%20with-TensorFlow%202.16-informational)
![GitHub Pages](https://img.shields.io/badge/Live%20Demo-✓-success)

> **TL;DR**  
> • 200 MosMedData volumes → 3-fold CV  
> • 100 % recall on “Abnormal” class (perfect rule-out)  
> • Grad-CAM heat-maps satisfy 2024 FDA guidance on explainability  

---

## 📌 Table of Contents
1. [Project Overview](#project-overview)
2. [Repo Structure](#repo-structure)
3. [Quick Start](#quick-start)
4. [Dataset](#dataset)
5. [Model Architecture](#model-architecture)
6. [Results](#results)
7. [Roadmap](#roadmap)
8. [Citation](#citation)
9. [License](#license)
10. [Contact](#contact)

---

## Project Overview
Radiologists routinely read hundreds of 300-slice CT volumes per shift—a workload that drives fatigue and diagnostic miss-rates.  
This project demonstrates a production-ready **3-D ResNet CNN** that:

| Stage       | Capability                                                                                                 |
|-------------|------------------------------------------------------------------------------------------------------------|
| **Ingest**  | Converts DICOM ➜ NIfTI ➜ 128×128×64 float tensors with z-axis resampling                                   |
| **Learn**   | Trains a 5-block residual network (~6 M parameters) with mixed precision & stratified 3-fold CV            |
| **Explain** | Generates volume-level Grad-CAM heat-maps for regulatory transparency                                      |
| **Report**  | Outputs accuracy, precision, recall, AUC, and an aggregate confusion matrix                                |

With perfect sensitivity, our model is safe to act as a **triage “gatekeeper”**—escalating abnormal cases for immediate review while letting radiologists focus on what matters.

---

## Repo Structure
```bash
.
├── assets/                 # PNGs for README & GitHub Pages
│   ├── gradcam_montage.png
│   ├── learning_curves.png
│   ├── auc_curve.png
│   └── confusion_matrix.png
├── notebooks/
│   └── volumetric_ct_triage.ipynb
├── src/
│   ├── dataloader.py
│   ├── model_factory.py
│   ├── train.py
│   └── inference.py
├── requirements.txt
├── README.md
└── LICENSE
