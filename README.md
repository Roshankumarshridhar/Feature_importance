<div align="center">
  <img src="https://github.com/Roshankumarshridhar/Feature_importance/blob/main/image-1.png?raw=true">
</div>


# TEM-1 β-Lactamase Variant Analysis

## Dataset
Our study utilized variants of TEM-1 β-lactamases and their corresponding Minimum Inhibitory Concentration (MIC) values. The dataset includes MIC values for 990 variants, classified as resistant or susceptible based on MIC relative to the wild type (WT) for amoxicillin. Resistance is indicated by positive MIC values, while susceptibility is indicated by negative MIC values. Variants such as A237T, G238S, and E104K were classified as susceptible, whereas E240K, N175S, and Q39K were classified as resistant ([Reference](https://doi.org/10.1073/pnas.1215206110)).

## REMD Simulations
- Six variants and the WT underwent Replica Exchange Molecular Dynamics (REMD) simulations.
- OPLS4 force field and TIP3P water model were used.
- Temperature range: 310 K to 328 K, each simulation lasting 100 ns.
- The last 50 ns was used for feature extraction.

## Feature Extraction
- **Dihedral Angles**: The φ (phi) and ψ (psi) dihedral angles of all 263 amino acids were extracted.
- **Data Volume**: 70,000 frames in total (40,000 susceptible, 30,000 resistant).
- **Scaling**: Center scaling applied using Standard Scaler for normalization.

## Classification Methods for Phenotype Prediction
1. **Linear Regression** - Modeled the relationship between dihedral angles and mutation effects.
2. **Support Vector Machines (SVM)** - Identified complex nonlinear patterns in high-dimensional data.
3. **Random Forest** - Improved accuracy and robustness against noise and overfitting.

## Essential Dynamics Analysis
- **Principal Component Analysis (PCA)** on C-alpha coordinates to determine motion.
- **RMSIP Analysis** was conducted to compare the similarity of motion directions.

## Residue Interaction Network
- Constructed using **RING 4.0**.
- Hydrogen bond frequency network was analyzed over the last 50 ns.


## Machine Learning Workflow
```python
pip install openpyxl imbalanced-learn
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score
from imblearn.over_sampling import SMOTE
