# Earthquake Magnitude Classification using Neural Networks

## Project Overview

This project classifies high-magnitude earthquakes using limited seismic data from Rwanda.
It integrates local and global seismic records with location and depth features.
Neural networks with optimization and regularization techniques improve prediction accuracy.
The dataset includes latitude, longitude, depth, and magnitude of seismic events.

## Dataset Description

The dataset contains records of earthquakes, including:

- **Latitude** and **Longitude** — location of the earthquake  
- **Depth** — how deep the quake occurred  
- **Magnitude** — the Richter magnitude of the event  
- **HighMag** — a derived binary label: 1 if magnitude ≥6.0, else 0  

The target variable (`HighMag`) is used to predict whether an earthquake is "high magnitude."

---

## Training Instances Summary Table

| Training Instance         | Optimizer Used | Regularizer Used | Epochs | Early Stopping | Number of Layers | Learning Rate | Accuracy | F1 Score | Recall | Precision |
|---------------------------|----------------|------------------|--------|----------------|------------------|---------------|----------|----------|--------|-----------|
| Instance 1 (Baseline)     | Adam           | None             | 30     | No             | 3 (64-32-1)       | 0.001         | *(TBD)*  | *(TBD)*  | *(TBD)* | *(TBD)*    |
| Instance 2                | Adam           | L2               | ~14    | Yes            | 3 (64-32-1)       | 0.001         | 0.85     | 0.70     | 0.54   | 0.99      |
| Instance 3                | RMSprop        | None             | ~16    | Yes            | 3 (64-32-1)       | 0.001         | 0.67     | 0.65     | 0.92   | 0.50      |
| Instance 4 (Best)         | Adam           | None             | ~12    | Yes            | 3 (64-32-1)       | 0.001         | 0.89     | 0.81     | 0.74   | 0.89      |

---

## Summary of Results

- The best performing model was **Instance 4**, using the Adam optimizer without regularization but with early stopping.  
- This model achieved:
  - **Accuracy:** 89%
  - **F1 Score:** 0.81
  - **Precision:** 0.89
  - **Recall:** 0.74

In contrast, **Instance 2** showed higher **precision** (0.99) but poor recall, resulting in a lower F1 Score. **Instance 3** demonstrated strong recall (0.92) but weak precision, suggesting the model overpredicted positive cases.

---

## ML vs Neural Network Comparison

Although not detailed in this notebook, traditional ML algorithms (e.g., Random Forest, Logistic Regression) tend to perform comparably on simpler or more linearly separable datasets. However, the neural network's flexibility and ability to model complex nonlinear patterns made it more suitable here.

### Potential Hyperparameters for ML Models:

- Max depth, number of trees (for Random Forest)
- Regularization (C) for Logistic Regression
- Kernel, gamma, and C for SVMs

Neural networks, especially when enhanced with early stopping and optimizer tuning, offer greater adaptability to data with interaction effects like seismic features.

---

## Model Deployment

The best model was saved as: best_earthquake_model.h5


