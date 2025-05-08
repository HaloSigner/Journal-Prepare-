# Predicting DNA Damage Response Using Synthetic Cell Painting Profiles and Experimental Analysis

This repository provides the full implementation for the manuscript:

📄 **Title:** Predicting DNA Damage Response Using Synthetic Cell Painting Profiles and Experimental Analysis

---

## 📌 Overview

This study introduces a machine learning framework for predicting DNA damage response (DDR) from high-dimensional phenotypic profiles extracted via Cell Painting assays. To overcome data scarcity and class imbalance, we generated synthetic data using generative models and validated model predictions both computationally and experimentally.


---


## **Code Structure**
```plaintext
├── 1. Data Preprocessing/            
│   ├── code/                        # Scripts for data distribution checks, preprocessing, and binarization
│   ├── data/                        # Datasets for preprocessing tasks
│   ├── env/                         # Environment setup files (env_base.yml)
├── 2. Synthetic Data Generation/          
│   ├── code/                        # Scripts for generating synthetic data
│   ├── data/                        # Synthetic datasets
│   ├── env/                         # Environment setup files (environment.yml)
├── 3. Model Training/                
│   ├── code/                        # Scripts for DNA damage response model training and application
│   ├── env/                          
├── 4. Model Interpretation/
│   ├── code/                        # SHAP analysis scripts
│   ├── env/
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

## Future Work

1. **Broaden biological scope:**  
   - Incorporate multiple cancer and non-cancer cell lines (beyond U2OS, A549, ES2, HCC44) to assess and improve model generalizability across diverse cellular contexts.  
   - Integrate multi-concentration and time-course Cell Painting profiles to capture dynamic DDR induction kinetics.

2. **Mitigate batch and domain shifts:**  
   - Implement advanced domain adaptation techniques (e.g. adversarial alignment, CORAL) to harmonize CRISPR-based (idr-0080) and small-molecule (cpg-0012) datasets, reducing batch effects.  
   - Explore transfer-learning workflows to fine-tune the synthetic-augmented model on new imaging platforms or staining protocols.

3. **Advance synthetic data generation:**  
   - Evaluate state-of-the-art generative models (diffusion models, normalizing flows) for higher-fidelity feature simulation and improved minority-class coverage.  
   - Develop active-learning loops that target low-confidence regions in feature space for on-demand synthetic sample generation.

4. **Deepen mechanistic validation:**  
   - Perform orthogonal assays (comet assay, PARP cleavage, cell-cycle profiling) to confirm on- and off-target DDR mechanisms of novel hits.  
   - Validate top candidates in 3D spheroid models or in vivo xenografts to assess translational potential.

5. **Integrate multi-omics and multi-modal imaging:**  
   - Combine Cell Painting readouts with transcriptomic or proteomic signatures to capture complementary molecular phenotypes and boost predictive power.  
   - Leverage live-cell and time-lapse imaging data to enrich feature space with temporal dynamics.

6. **Enable prospective, high-throughput screening:**  
   - Deploy the pipeline within automated screening platforms for real-time DDR prediction during large-scale compound libraries.  
   - Build interactive dashboards for streamlined visualization and decision support by drug-discovery teams.

These enhancements will not only address potential reviewer concerns around generalizability, batch effects, and mechanistic depth but also pave the way for robust, clinically relevant phenotypic prescreening in drug discovery.

---



## 🧾 License

MIT License © 2025

---

## 📬 Contact

**Chaeyoung Seo**  
📧 Email: kojkos@gmail.com
