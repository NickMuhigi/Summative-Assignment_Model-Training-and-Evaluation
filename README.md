# Earthquake Magnitude Classification using Neural Networks

## Project Overview

This project classifies high-magnitude earthquakes (≥6.0) using seismic data from Rwanda. The dataset contains event features like latitude, longitude, depth, and magnitude. A binary classification target `HighMag` is derived. Neural networks with various optimization and regularization techniques were applied to improve model performance. Comprehensive evaluation was done using accuracy, F1-score, precision, recall, loss curves, and confusion matrices.

## Dataset Description

The dataset includes:
- Latitude and Longitude — location of the seismic event  
- Depth — depth of the earthquake (in km)  
- Magnitude — Richter scale magnitude  
- HighMag — binary label (1 if magnitude ≥ 6.0, else 0)

## Training Instances Summary Table

| Training Instance     | Optimizer | Regularizer | Early Stopping | Learning Rate | Accuracy | F1 Score | Recall | Precision | Loss (Val) |
|-----------------------|-----------|-------------|----------------|----------------|----------|----------|--------|-----------|------------|
| Instance 1 (Baseline) | Adam (default) | None        | No             | 0.001          | 0.8212   | 0.6262   | 0.4610 | 0.9759    | ~0.25      |
| Instance 2            | Adam     | L2 (0.002)  | Yes            | 0.001          | 0.85     | 0.7006   | 0.54   | 0.99      | ~0.41      |
| Instance 3            | RMSprop  | None        | Yes            | 0.001          | 0.67     | 0.6456   | 0.92   | 0.50      | ~0.55      |
| Instance 4 (Best)     | Adam     | None        | Yes            | 0.001          | 0.89     | 0.8090   | 0.74   | 0.89      | ~0.30      |

## Summary of Results and Justification

- **Best Performance**:  
  Instance 4 (Adam, no regularization, with early stopping) achieved a balanced F1-score of 0.81, with high precision (0.89) and good recall (0.74).  
  The model achieved this balance by preventing overfitting via early stopping, while still allowing flexibility in learning without regularization constraints.

- **Baseline (Instance 1)** had high accuracy and F1 but lacked safeguards like early stopping, risking overfitting on training data.

- **Instance 2** had very high precision (0.99) due to L2 regularization, but poor recall (0.54), meaning many actual high-magnitude quakes were missed — a classic sign of underfitting.

- **Instance 3 (RMSprop)** prioritized recall (0.92) but at the cost of precision (0.50), producing too many false positives. RMSprop's adaptive updates may have contributed to instability in convergence.

- **Why Adam Outperformed RMSprop**:  
  Adam combines momentum and adaptive learning rates, stabilizing training and preventing over-aggressive updates. Early stopping helped avoid overfitting.

- **Effect of Regularization**:  
  L2 regularization limited model complexity in Instance 2, improving precision but reducing its ability to learn patterns associated with positive cases.

- **Early Stopping** across all models improved generalization by halting training once validation loss stopped improving, leading to better real-world performance.

## ML vs Neural Network Comparison

Traditional ML algorithms (Logistic Regression, SVM, Random Forest) work well on linearly separable data. However, this task involved learning complex interactions (location + depth + magnitude), which neural networks handled better.

### Typical ML Hyperparameters:
- Random Forest: `max_depth`, `n_estimators`, `min_samples_split`
- Logistic Regression: `C` (regularization), `penalty`, `solver`
- SVM: `C`, `gamma`, `kernel`

Neural networks with dropout, optimizer selection, and early stopping are better suited for learning non-linear patterns present in this dataset.

## Model Deployment

Link to video: https://www.youtube.com/watch?v=NYy2FId0ZQ8

Best model saved as: `models/best_earthquake_model.h5`  
