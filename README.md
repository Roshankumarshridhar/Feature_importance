<div align="center">
  <img src="https://github.com/Roshankumarshridhar/Feature_importance/blob/main/image-1.png?raw=true">
</div>


# TEM-1 β-Lactamase Variant Analysis

## Overview
This project explores the structural and dynamic properties of TEM-1 β-lactamase variants to understand their impact on antibiotic resistance. We employed **Replica Exchange Molecular Dynamics (REMD) simulations** and **Machine Learning models** for phenotype prediction.

## Key Components
- **Dataset**: MIC values for 990 TEM-1 β-lactamase variants.
- **REMD Simulations**: Temperature range (310 K - 328 K), OPLS4 force field, TIP3P water model.
- **Feature Extraction**: Dihedral angles (φ, ψ) from the last 50 ns of REMD simulations.
- **Machine Learning Models**: Random Forest, SVM, Linear Regression.
- **Essential Dynamics Analysis**: PCA-based motion analysis and Residue Interaction Networks.

## Installation
```sh
pip install -r requirements.txt
