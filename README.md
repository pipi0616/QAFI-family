# QAFI-Family: Protein-Specific and Ensemble-Based Models for Variant Effect Prediction

**QAFI-Family** is a collection of machine learning methods designed for the quantitative prediction of missense variant effects using deep mutational scanning (DMS) data.  
This repository extends the original QAFI framework (Selen et al., 2025) and provides several complementary strategies that integrate **protein-specific predictors (PSPs)** with **ensemble learning** to achieve robust and generalizable predictions across proteins.

## Methods Included
- **QAFI1** – Linear regression–based PSP ensemble using 14 discriminant features.  
- **QAFI2** – XGBoost PSP ensemble with 28 extended sequence, structural, and evolutionary features.  
- **QAFIsplit1** – Two-step median feature fusion (position-level baseline + variant-level prediction).  
- **QAFIsplit2** – Two-step residual modeling (median baseline + residual correction).  
- **QAFIsplit3** – Correlation-weighted ensemble strategy based on QAFIsplit2.  

## Core Principles
All QAFI methods follow a two-level framework:
1. **Protein-specific modeling** – regression models trained on DMS datasets for individual proteins.  
2. **Ensemble integration** – predictions aggregated across PSPs to generalize to unseen proteins.  

## Highlights
- Incorporates **feature expansion** (14 → 28 features including sequence, structural, and evolutionary descriptors).  
- Introduces **two-step modeling** to decouple position-level tolerance from substitution-specific effects.  
- Employs **ensemble learning** to extend predictions beyond training proteins.  

## Citation
If you use this repository, please cite:  
*Selen et al., 2025. QAFI: A Novel Method for Quantitative Estimation of Missense Variant Impact Using Protein-Specific Predictors and Ensemble Learning.*  

---
