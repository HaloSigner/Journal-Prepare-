# **Code for "Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery"**

This repository contains the implementation details and code used in the study **"Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery"**, which demonstrates the use of synthetic data augmentation and machine learning for DNA damage response (DDR) profiling.

## **Contents**
1. **Data Preprocessing**
   - Scripts for feature extraction, normalization (MODZ), and preprocessing steps (e.g., low-variance feature removal).
2. **Synthetic Data Generation**
   - Implementation of generative models (Gaussian Copula, CTGAN, TVAE, CopulaGAN) using the SDV library.
3. **K-means Clustering and Binary Classification**
   - Code for applying K-means clustering to identify DDR-related clusters and consolidating them into binary categories.
4. **Machine Learning Model Training**
   - Scripts for training machine learning models (SVM, Logistic Regression, SGD Classifier, LightGBM) and hyperparameter optimization using GridSearchCV.
5. **Model Evaluation**
   - Code for evaluating models using metrics such as F1-score, ROC-AUC, and t-SNE visualization.

## **Code Structure**
```plaintext
.
├── data/                     # Example datasets (synthetic and real)
├── preprocessing/            # Scripts for feature extraction and preprocessing
│   ├── feature_selection.py  # Feature extraction and low-variance feature removal
│   ├── normalization.py      # MODZ normalization script
├── synthetic_data/           # Synthetic data generation scripts
│   ├── gaussian_copula.py    # Gaussian Copula implementation
│   ├── ctgan.py              # CTGAN implementation
│   ├── tvae.py               # TVAE implementation
│   ├── copulagan.py          # CopulaGAN implementation
├── clustering/               # K-means clustering scripts
│   ├── kmeans_clustering.py  # K-means clustering and binary classification
├── models/                   # Machine learning model training scripts
│   ├── train_svm.py          # SVM training and evaluation
│   ├── train_logreg.py       # Logistic Regression training and evaluation
│   ├── train_sgd.py          # SGD Classifier training and evaluation
│   ├── train_lightgbm.py     # LightGBM training and evaluation
├── evaluation/               # Evaluation and visualization scripts
│   ├── metrics.py            # F1-score, confusion matrix, and ROC-AUC calculation
│   ├── tsne_visualization.py # t-SNE visualization for feature separability
├── README.md                 # Repository documentation
└── requirements.txt          # Required Python packages
