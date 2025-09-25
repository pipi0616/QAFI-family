# QAFI-Family: Protein-Specific and Ensemble-Based Models for Variant Effect Prediction

**QAFI-Family** is a collection of machine learning methods designed for the quantitative prediction of missense variant effects using deep mutational scanning (DMS) data.  
This repository extends the original QAFI framework (Selen et al., 2025) and provides both **protein-specific predictors (PSPs)** and **ensemble-based QAFI models** to enable robust and generalizable variant effect prediction.

---

## Core Principles

All QAFI methods are built on two key principles:

1. **Protein-Specific Modeling (PSPs)**  
   - Individual regression models are trained on DMS datasets for each protein.  
   - Models capture protein-specific sequence, structure, and evolutionary constraints.  

2. **Ensemble Integration (QAFI)**  
   - Predictions from multiple PSPs are aggregated to generalize performance to unseen proteins.  
   - Ensemble strategies include median fusion and correlation-weighted fusion, ensuring robustness and transferability.  

---

## Development of Protein-Specific Predictors (PSPs)

The notebook `ProteinSpecificPredictors.ipynb` provides all analyses related to the development and evaluation of protein-specific predictors (PSPs), which form the foundation for the QAFI framework:

- **Dataset exploration**: Analysis of 60 deep mutational scanning (DMS) assays used in this study.  
- **Feature representation**: Construction of 14 baseline discriminant features and an extended set of 28 sequence-, structure-, and evolution-based descriptors.  
- **Cross-validation**: Leave-one-position-out (LOPO) procedures applied within each protein to evaluate PSP performance.  
- **Cross-protein predictions**: Each PSP applied to predict mutational effects across the remaining proteins, enabling assessment of transferability.  
- **Model variants**:  
  - **PSP1** – 14 features with linear regression.  
  - **PSP2** – 28 features with XGBoost regression.  
  - **PSPsplit1** – Two-step median feature fusion (position-level baseline + variant-level prediction).  
  - **PSPsplit2** – Two-step residual modeling (median baseline + residual correction).  
- **Performance comparison**: Benchmarking of all PSP variants, highlighting the contribution of feature expansion and position-aware modeling.  

The normalized DMS assays and the derived features are available in:  
`data/Dataset_60proteins_features.csv`  

---

## QAFI Ensemble Models and Generalization to Unseen Proteins

The notebook `QAFI_Ensemble.ipynb` extends PSP models to unseen proteins through ensemble-based strategies:

- **Rationale**:  
  PSPs achieve strong accuracy within individual proteins but cannot directly generalize to proteins outside the training set. QAFI addresses this limitation by aggregating predictions from multiple PSPs.

- **Ensemble construction**:  
  We systematically compared ensemble sizes (10, 15, 30, 45, and 60 PSPs). Ensembles of **30 PSPs** most frequently achieved the best predictive correlations, providing an optimal balance between accuracy and robustness (see Supplementary Fig. 4).  
  This ensemble size was therefore adopted for all subsequent QAFI analyses.

- **Model family**:  
  - **QAFI1** – Ensemble of PSP1 models (14 features, linear regression).  
  - **QAFI2.0** – Ensemble of PSP2 models (28 features, XGBoost).  
  - **QAFIsplit1.0** – Ensemble of PSPsplit1 models (median feature fusion).  
  - **QAFIsplit2.0** – Ensemble of PSPsplit2 models (residual modeling).  
  - **QAFIsplit3.0** – Ensemble with correlation-weighted fusion, based on PSPsplit2.  

- **Evaluation**:  
  Performance comparisons against PSP counterparts demonstrate that QAFI models preserve within-protein trends while extending prediction capacity to unseen proteins.  
  Improvements introduced at the PSP level—feature expansion and position-aware modeling—are retained in the ensemble setting.

---

## Citation

If you use this repository, please cite:  

*Selen et al., 2025. QAFI: A Novel Method for Quantitative Estimation of Missense Variant Impact Using Protein-Specific Predictors and Ensemble Learning.*  

---
