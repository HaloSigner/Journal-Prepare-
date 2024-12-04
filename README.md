Code for "Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery"
This repository contains the implementation details and code used in the study "Integrating Synthetic Data for Improved DNA Damage Response Profiling in Drug Discovery", which demonstrates the use of synthetic data augmentation and machine learning for DNA damage response (DDR) profiling.

Contents
Data Preprocessing
Scripts for feature extraction, normalization (MODZ), and preprocessing steps (e.g., low-variance feature removal).
Synthetic Data Generation
Implementation of generative models (Gaussian Copula, CTGAN, TVAE, CopulaGAN) using the SDV library.
K-means Clustering and Binary Classification
Code for applying K-means clustering to identify DDR-related clusters and consolidating them into binary categories.
Machine Learning Model Training
Scripts for training machine learning models (SVM, Logistic Regression, SGD Classifier, LightGBM) and hyperparameter optimization using GridSearchCV.
Model Evaluation
Code for evaluating models using metrics such as F1-score, ROC-AUC, and t-SNE visualization.
