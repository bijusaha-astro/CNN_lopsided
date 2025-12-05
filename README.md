# Galaxy Lopsidedness Classification — Dataset and Model

This repository contains the training datasets, the best-performing model weights, a demo notebook for loading the model weight to make prediction, and catalogue of newly predicted galaxies. 

## Repository contents

- Training Data
  - `Training_Lopsided.csv`
  - `Training_Symmetric.csv`
  - These two CSVs form the labeled training datasets for lopsided and symmetric galaxies.

- High-confidence predictions (p ≥ 0.85)
  - `High_confidence_predicted_lopsided.csv`
  - `High_confidence_predicted_symmetric.csv`
  - Lists of new galaxy predictions where the model predicted a class with probability ≥ 0.85.

- Lower-confidence predictions (p < 0.85)
  - `Below_85prediction_lopsided.csv`
  - `Below_85prediction_Symmetric.csv`
  - Predictions where the model probability for the predicted class is below 0.85.

- Model weights
  - `best_perform.pt` — Weights of the best-performing trained model (PyTorch format).

- Demo notebook
  - `model_demo.ipynb` — Demonstrates loading the trained model and generating predictions for new galaxy images.

## Columns / Fields

All CSVs share the following columns (unless otherwise noted):

- `IAU Name` — International Astronomical Union designation for the galaxy.
- `SDSS PhotObjID` — SDSS photometric object identifier.
- `A1` — Lopsidedness parameter (provided for training files).
- `Environment Type` — Environment classification (if available).
- `Prediction Probability` — (prediction CSVs) Model's predicted probability for the reported class.

## Usage

Use the provided demo notebook to reproduce predictions. Below is a minimal example showing how to load weights and run inference in PyTorch — adapt it to your model class and preprocessing pipeline.

Reproduce predictions (example)
1. Install requirements (example):
   - Python 3.8+
   - PyTorch
   - torchvision, numpy, pandas

2. Example PyTorch inference snippet (modify to match your model architecture and preprocessing):

```python
import torch
import pandas as pd
from torchvision import transforms
from PIL import Image

# 1) Define or import your model class exactly as used during training
# from model import MyModel
# model = MyModel(...)

# 2) Load saved weights
state = torch.load("best_perform.pt", map_location="cpu")
# If you saved the full model: model = state
# If you saved state_dict:
# model.load_state_dict(state)

model.eval()

# 3) Example preprocessing (match training transforms)
preprocess = transforms.Compose([
    transforms.Resize((224, 224)),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406],
                         std =[0.229, 0.224, 0.225]),
])

# 4) Load and preprocess an image
img = Image.open("example_galaxy.jpg").convert("RGB")
input_tensor = preprocess(img).unsqueeze(0)  # add batch dim

# 5) Run inference
with torch.no_grad():
    logits = model(input_tensor)
    probs = torch.softmax(logits, dim=1)
    predicted_class = probs.argmax(dim=1).item()
    predicted_prob = probs.max().item()

print("Predicted class:", predicted_class)
print("Probability:", predicted_prob)
```

3. Recreate CSV-style output:
   - For each image or object, collect IAU Name, SDSS PhotObjID (if available), predicted class, prediction probability, and Environment Type.
   - Save results with pandas to CSV for the same format as the repository files.

## Notes

- The repository contains the labeled training sets for the two classes (lopsided vs symmetric). The `A1` column is included in the training CSVs as the reported lopsidedness parameter used in analysis.
- Prediction threshold of 0.85 was used to separate "high-confidence" from "lower-confidence" predictions. You can change this threshold to suit your use case.

## Contact

If you need help reproducing results or want the exact training code / model architecture, please contact the maintainer:

- Maintainer: Your Name — email@example.com
- Repository: https://github.com/<owner>/<repo>
