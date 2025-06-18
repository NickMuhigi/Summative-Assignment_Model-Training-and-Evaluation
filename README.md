🌍 Earthquake Magnitude Classification using Neural Networks
🧠 Project Overview
This project investigates how various optimization and regularization techniques affect the performance of a neural network classifier. The model aims to classify whether an earthquake has a high magnitude (≥6.0) using geospatial and depth-based input features. The goal is to improve performance, generalization, and convergence speed using techniques such as early stopping, dropout, L2 regularization, and different optimizers.

📂 Dataset Description
The dataset contains records of earthquakes, including:

Latitude and Longitude — location of the earthquake

Depth — how deep the quake occurred

Magnitude — the Richter magnitude of the event

HighMag — a derived binary label: 1 if magnitude ≥6.0, else 0

The target variable (HighMag) is used to predict whether an earthquake is "high magnitude."

📊 Training Instances Summary Table
Training Instance	Optimizer Used	Regularizer Used	Epochs	Early Stopping	Number of Layers	Learning Rate	Accuracy	F1 Score	Recall	Precision
Instance 1 (Baseline)	Adam	None	30	No	3 (64-32-1)	0.001	(TBD)	(TBD)	(TBD)	(TBD)
Instance 2	Adam	L2	~14	Yes	3 (64-32-1)	0.001	0.85	0.70	0.54	0.99
Instance 3	RMSprop	None	~16	Yes	3 (64-32-1)	0.001	0.67	0.65	0.92	0.50
Instance 4 (Best)	Adam	None	~12	Yes	3 (64-32-1)	0.001	0.89	0.81	0.74	0.89

✅ Summary of Results
The best performing model was Instance 4, using the Adam optimizer without regularization but with early stopping.

This model achieved:

Accuracy: 89%

F1 Score: 0.81

Precision: 0.89

Recall: 0.74

In contrast, Instance 2 showed higher precision (0.99) but poor recall, resulting in a lower F1 Score. Instance 3 demonstrated strong recall (0.92) but weak precision, suggesting the model overpredicted positive cases.

🤖 ML vs Neural Network Comparison
Although not detailed in this notebook, traditional ML algorithms (e.g., Random Forest, Logistic Regression) tend to perform comparably on simpler or more linearly separable datasets. However, the neural network's flexibility and ability to model complex nonlinear patterns made it more suitable here.

Potential Hyperparameters for ML Models (if explored):
Max depth, number of trees (for Random Forest)

Regularization (C) for Logistic Regression

Kernel, gamma, and C for SVMs

Neural networks, especially when enhanced with early stopping and optimizer tuning, offer greater adaptability to data with interaction effects like seismic features.

📦 Model Deployment
The best model was saved as:

bash
Copy
Edit
best_earthquake_model.h5
This model can be loaded and used for real-time earthquake classification.

🎥 Video Presentation Instructions
🎥 REQUIRED VIDEO DEMO
Please record a short video (3–5 minutes) covering the following:

Turn on your camera for visibility and academic integrity.

Briefly introduce the problem and the dataset.

Walk through your Jupyter Notebook, explaining:

Model architecture

Optimization combinations

Confusion matrices and metrics

The training instance performance table

Clearly state which model performed best and why.

End with your insights or potential improvements.

🏁 Conclusion
This project demonstrates how simple changes in regularization, optimizers, and early stopping can significantly impact a neural network's generalization ability. By evaluating models not only on accuracy but also on F1 score, precision, and recall, a more balanced and robust selection process was achieved.

