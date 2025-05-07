# Identification of the DNA Damage through Augmented Cell Painting Profiles and Experimental Analysis

This repository provides the full implementation for the manuscript:

📄 **Title:** Identification of the DNA Damage through Augmented Cell Painting Profiles and Experimental Analysis  

---

## 📌 Overview

This study introduces a machine learning framework for predicting DNA damage response (DDR) from high-dimensional phenotypic profiles extracted via Cell Painting assays. To overcome data scarcity and class imbalance, we generated synthetic data using generative models and validated model predictions both computationally and experimentally.

<p align="center">
  <img src="Figure1_Graphic_Abstract.png" width="700" alt="Graphical Abstract">
</p>

---


## **Code Structure**
```plaintext
├── 1. Data Preprocessing/            
│   ├── code/                        # Scripts for data distribution checks, preprocessing, and binarization
│   ├── data/                        # Sample datasets for preprocessing tasks
│   ├── env/                         # Environment setup files (env_base.yml)
├── 2. Synthetic Data Generation/          
│   ├── code/                        # Scripts for generating synthetic data
│   ├── data/                        # Sample synthetic datasets
│   ├── env/                         # Environment setup files (environment.yml)
├── 3. Model Training/                
│   ├── code/                        # Scripts for DNA damage response model training and application
├── 4. Model Interpretation/
│   ├── code/                        # SHAP analysis scripts
├── README.md                        # Repository documentation
└── Raw Data/                        # Raw Data




---

```
## 📊 Datasets

### 🔹 IDR-0080
- **Source**: [Broad Institute Cell Health](https://github.com/broadinstitute/cell-health)
- 357 CRISPR perturbagens from A549, ES2, and HCC44 cell lines.
- 736 intersected Cell Painting features used.

### 🔹 CPG-0012
- **Source**: [GigaDB Dataset](https://gigadb.org/dataset/view/id/100351)
- 30,616 compound treatments in U2OS cells.

**Preprocessing steps**:
- Aggregation → Median-of-Z-scores (MODZ)  
- Normalization → MAD scaling  
- Feature selection → Shared + informative features only

---

## 🧬 Synthetic Data Generation

We used four generative models implemented via [SDV (Synthetic Data Vault)](https://github.com/sdv-dev/SDV):

- Gaussian Copula (highest fidelity)
- Conditional Tabular GAN (CTGAN)
- Variational Autoencoder (VAE)
- CopulaGAN

### 🧪 Fidelity Metrics
- Column Shape Score
- Column Pair Trends Score
- Combined Similarity

> Gaussian Copula outperformed all others in fidelity and downstream model performance.

---

## 🤖 Machine Learning Pipeline

We trained four classifiers:
- Logistic Regression  
- Support Vector Machine (SVM)  
- Stochastic Gradient Descent Classifier (SGD)  
- LightGBM

### 🧠 Training Scenarios
- Real data only (imbalanced / oversampled)  
- Synthetic data only  
- Real + Synthetic (blended)  
- Balanced vs. Imbalanced  
- Class weights + 5-fold CV

---

## 📈 Key Results

| Data Type                | Best Model | F1 (High DDR) |
|--------------------------|------------|---------------|
| Real + Gaussian Copula   | SVM        | **0.87**      | 
| Synthetic Only (GC)      | SVM        | 0.80          |         
| Real Only (imbalanced)   | SVM        | 0.32          |         

- **SHAP analysis** revealed top contributing features:
  - Cytoplasm_Texture_Gabor_AGP_10  
  - Cytoplasm_Texture_InverseDifferenceMoment_AGP_5_0  
  - Cytoplasm_RadialDistribution_FracAtD_AGP_4of4

---

## 🌍 External Validation: CPG-0012

- Applied the best model (real + synthetic SVM) to 30,616 compounds  
- Identified **1,089 potential DDR-inducing compounds**
- Detected known DDR inducers (doxorubicin, vincristine, etoposide, cisplatin)
- Prioritized **novel candidates**:
  - Tetrindole  
  - LY-2183240  
  - KF38789

---

## 🧪 Experimental Validation

### ✅ γH2AX Staining (Flow Cytometry)
- All three candidates induced γH2AX accumulation in U2OS cells

### ✅ Cell Viability Assay (CellTiter-Glo)
- Dose-dependent reduction in viability for all three compounds

---

## 🧾 License

MIT License © 2025

---

## 📬 Contact

**Chaeyoung Seo**  
📧 Email: kojkos@gmail.com
