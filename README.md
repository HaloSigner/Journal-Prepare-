# **Code for "Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery"**

This repository contains the implementation details and code used in the study **"Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery"**, which demonstrates the use of synthetic data augmentation and machine learning for DNA damage response (DDR) profiling.

## **Contents**
1. **Data Preprocessing**
   - Scripts for feature extraction, normalization (MODZ), and preprocessing steps (e.g., low-variance feature removal).
   - Sample datasets and environment setup files for preprocessing tasks.
2. **Synthetic Data Generation**
   - Implementation of generative models (Gaussian Copula, CTGAN, TVAE, CopulaGAN) using the SDV library.
   - Scripts and sample data for generating synthetic datasets.
3. **Machine Learning Model Training**
   - Scripts for training machine learning models (SVM, Logistic Regression, SGD Classifier, LightGBM).
   - Code for evaluating model performance and applying models to DDR profiling tasks.

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
├── README.md                        # Repository documentation
└── requirements.txt                 # Required Python packages
