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
│   ├── code/        # Scripts for DNA damage response model training and application
├── 4. Model Interpretation/
│   ├── code/        
├── README.md                        # Repository documentation
└── Raw Data/                        # Raw Data


---

## 📊 Datasets

### 🔹 IDR-0080
- **Source**: [Broad Institute Cell Health](https://github.com/broadinstitute/cell-health)
- 357 CRISPR perturbagens from A549, ES2, and HCC44 cell lines.
- 736 intersected Cell Painting features used.

### 🔹 CPG-0012
- **Source**: [GigaDB Dataset](https://gigadb.org/dataset/view/id/100351)
- 30,616 compound treatments in U2OS cells.

Preprocessing steps included:
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

### 🧪 Fidelity Metrics:
- **Column Shape Score**
- **Column Pair Trends Score**
- **Combined Similarity**

> Gaussian Copula outperformed all others in fidelity and downstream model performance.

---

## 🤖 Machine Learning Pipeline

We trained four classifiers:
- Logistic Regression
- Support Vector Machine (SVM)
- Stochastic Gradient Descent Classifier (SGD)
- LightGBM

### 🧠 Training Scenarios:
- Real data only (imbalanced / oversampled)
- Synthetic data only
- Real + Synthetic (blended)
- Balanced vs. Imbalanced variants
- Class weights & 5-fold stratified CV

---

## 📈 Key Results

| Data Type                | Best Model | F1 (High DDR) | AUC-ROC |
|--------------------------|------------|---------------|---------|
| Real + Gaussian Copula   | SVM        | **0.87**      | **0.94**|
| Synthetic Only (GC)      | SVM        | 0.80          | 0.90    |
| Real Only (imbalanced)   | SVM        | 0.32          | 0.68    |

- **SHAP analysis** revealed 3 major features:  
  - Cytoplasm_Texture_Gabor_AGP_10  
  - Cytoplasm_Texture_InverseDifferenceMoment_AGP_5_0  
  - Cytoplasm_RadialDistribution_FracAtD_AGP_4of4

---

## 🌍 External Validation: CPG-0012

- Applied best-performing SVM (real + synthetic) to 30,616 compounds
- Predicted **9,923 hits** with high DDR scores
- Detected known DDR inducers (e.g., doxorubicin, etoposide, vincristine)
- Identified **novel candidate compounds**:
  - **Tetrindole**
  - **LY-2183240**
  - **KF38789**

---

## 🧪 Experimental Validation

### ✅ γH2AX staining
- Flow cytometry confirmed increased DNA damage in U2OS cells

### ✅ Cell viability assay (CellTiter-Glo®)
- All 3 selected candidates significantly reduced cell viability in a dose-dependent manner

---


## License
- MIT License © 2025

## Contact
- Chaeyoung Seo
- kojkos@gmail.com

