Galaxy Lopsidedness Classification — Dataset and Model

This repository contains the data files and model weights associated with our study on classifying lopsided and symmetric galaxies using a deep learning model.

📁 Contents
Training Data

Training_Lopsided.csv

Training_Symmetric.csv

Each file contains the following columns:

IAU Name

SDSS PhotObjID

A1 (lopsidedness parameter)

Environment Type

These two CSVs form the labeled training datasets for lopsided and symmetric galaxies.

High-Confidence Predictions (p ≥ 0.85)

High_confidence_predicted_lopsided.csv

High_confidence_predicted_symmetric.csv

These files list new galaxy predictions made by the best-performing model, including:

IAU Name

SDSS PhotObjID

Prediction Probability (for the predicted class)

Environment Type

Lower-Confidence Predictions (p < 0.85)

Below_85prediction_lopsided.csv

Below_85prediction_Symmetric.csv

Same column structure as above, but containing galaxies where the model prediction probability is below 0.85.

Model Weights

best_perform.pt – Weights of the best-performing trained model.

Demo Notebook

model_demo.ipynb (or your actual file name)
Demonstrates how to load the trained model and use it to generate predictions for new galaxy images.

📌 Usage

You can load the model and reproduce the predictions by following the steps shown in the demonstration notebook. Feel free to adapt the workflow for your own datasets.
