# Earthquake Magnitude Classification using Neural Networks

## Project Overview

This project classifies high-magnitude earthquakes using limited seismic data from Rwanda. It integrates local and global seismic records with location and depth features. Neural networks with optimization and regularization techniques improve prediction accuracy. The dataset includes latitude, longitude, depth, and magnitude of seismic events. Comprehensive error analysis using metrics like F1-score, precision, recall, and confusion matrices was performed to evaluate model performance.
## Dataset Description

The dataset contains seismic event records, including:

- **Latitude** and **Longitude** — geographic location of the seismic event  
- **Depth** — depth at which the seismic event occurred  
- **Magnitude** — the Richter scale magnitude of the seismic event  
- **HighMag** — a derived binary label indicating whether the magnitude is high (≥6.0)

The target variable (`HighMag`) is used to predict whether an earthquake is "high magnitude."

---

## Training Instances Summary Table

| Training Instance         | Optimizer     | Regularizer     | Epochs           | Early Stopping | Learning Rate | Accuracy | F1 Score | Recall | Precision |
|--------------------------|---------------|-----------------|------------------|----------------|---------------|----------|----------|--------|-----------|
| Instance 1 (Baseline)    | Default (Adam)| None            | 30               | No             | 0.001 (default)| 0.8212   | 0.6262   | 0.4610 | 0.9759    |
| Instance 2               | Adam          | L2 (0.002)      | ≤30 (early stop) | Yes            | 0.001         | 0.85     | 0.7006   | 0.54   | 0.99      |
| Instance 3               | RMSprop       | None            | ≤30 (early stop) | Yes            | 0.001         | 0.67     | 0.6456   | 0.92   | 0.50      |
| Instance 4 (Best)        | Adam          | None            | ≤30 (early stop) | Yes            | 0.001         | 0.89     | 0.8090   | 0.74   | 0.89      |

---

## Summary of Results

- The best performing model was **Instance 4**, using the Adam optimizer without regularization but with early stopping.  
- This model achieved:
  - **Accuracy:** 89%
  - **F1 Score:** 0.81
  - **Precision:** 0.89
  - **Recall:** 0.74

In contrast, **Instance 2** showed very high **precision** (0.99) but lower recall, resulting in a moderate F1 score.  
**Instance 3** demonstrated strong recall (0.92) but low precision, indicating the model over-predicted positive cases.

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

The best model was saved as: `best_earthquake_model.h5`
