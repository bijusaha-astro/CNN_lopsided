# Galaxy Lopsidedness Classification — Dataset and Model

This repository contains the training datasets, the best-performing model weights, a demo notebook for loading the model weight to make prediction, and catalogue of newly predicted galaxies. 

## Repository contents

- Training Data
  - `Training_Lopsided.csv`
  - `Training_Symmetric.csv`
  - These two CSVs form the training datasets for lopsided and symmetric galaxies, respectively.

- High-confidence predictions (p ≥ 0.85)
  - `High_confidence_predicted_lopsided.csv`
  - `High_confidence_predicted_symmetric.csv`
  - Lists of new galaxy predictions where the model predicted a class with probability ≥ 0.85.

- Lower-confidence predictions (p < 0.85)
  - `Below_85prediction_lopsided.csv`
  - `Below_85prediction_Symmetric.csv`
  - Predictions where the model probability for the predicted class is below 0.85.

- Model weights
  - `best_model.pt` — weights of the best-performing trained model.

- Demo notebook
  - `prediction_code.ipynb` — Demonstrates loading the above model and generating predictions for new galaxy images.

## Columns / Fields

All CSVs share the following columns (unless otherwise noted):

- `IAU Name` — International Astronomical Union designation for the galaxy.
- `SDSS PhotObjID` — SDSS photometric object identifier.
- `A1` — Lopsidedness parameter (provided for training files).
- `Environment Type` — Environment classification (if available).
- `Prediction Probability` — (prediction CSVs) Model's predicted probability for the reported class.

## Contact

For more information, please contact: Biju Saha — bijusaha930@gmail.com
