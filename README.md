# Early Stroke Prediction System — MTI850 Project

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![PySpark](https://img.shields.io/badge/PySpark-Apache%20Spark-orange?logo=apachespark)
![ML](https://img.shields.io/badge/Domain-Healthcare%20%7C%20Big%20Data%20%7C%20ML-green)
![License](https://img.shields.io/badge/License-Academic-lightgrey)

> A **Big Data Analytics** pipeline for early stroke risk prediction, built on **Apache Spark (PySpark)** and trained on augmented patient health records — achieving ~86% Recall on positive stroke cases using an optimized Random Forest classifier.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Features & Pipeline](#features--pipeline)
- [Machine Learning Models](#machine-learning-models)
- [Notebook Structure](#notebook-structure)
- [Tech Stack](#tech-stack)
- [Key Results](#key-results)
- [Authors](#authors)

---

## Overview

According to the **World Health Organization (WHO)**, stroke is the **third leading cause of death and disability worldwide**. Early detection is critical to improving patient outcomes.

This project, developed as part of the **MTI850** course, builds an end-to-end analytical system capable of evaluating a patient's stroke probability based on demographic and medical features. The core focus is on applying **Big Data** processing techniques at scale using the **Apache Spark** ecosystem, including a streaming simulation for real-time patient data ingestion.

---

## Dataset

The project uses the [Kaggle Stroke Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset).

| Property | Details |
|---|---|
| Base volume | ~5,110 patient records |
| Augmented volume | Synthetically expanded to simulate a Big Data context |
| Target variable | `stroke` (binary: 0 / 1) |
| Key features | Age, gender, hypertension, heart disease, marital status, work type, average glucose level, BMI, smoking status |

> **Note:** Data augmentation includes controlled noise injection and random missing value introduction to stress-test pipeline robustness.

---

## Features & Pipeline

The project implements a complete, production-ready Spark pipeline across the following stages:

1. **Data Augmentation**  
   Synthetic data generation to simulate large-scale volumes, with added noise and missing values.

2. **Preprocessing & Cleaning**  
   Missing value imputation (mean/mode strategies), categorical encoding via `StringIndexer` and `OneHotEncoder`.

3. **Exploratory Data Analysis (EDA)**  
   Correlation matrices, feature distributions, and class imbalance visualization across medical variables.

4. **Modeling & Class Imbalance Handling**  
   Oversampling (SMOTE-like) and class weighting strategies to address the strong imbalance between stroke/non-stroke cases.

5. **Production Pipeline**  
   Full exportable Spark ML pipeline enabling real-time inference on new patient records.

6. **Streaming Simulation**  
   Structured streaming setup to simulate continuous patient data arrival and trigger live predictions.

---

## Machine Learning Models

Three classifiers were trained and evaluated using **AUC-ROC** and **Recall** as primary metrics (Recall prioritized to minimize false negatives in a medical context):

| Model | Notes |
|---|---|
| Logistic Regression | Baseline linear model |
| Random Forest | Best performer — optimized for Recall |
| Gradient Boosted Trees (GBT) | Ensemble boosting approach |

> **Best model:** Random Forest with a Recall of **~86%** on positive stroke cases.

---

## Notebook Structure

| Section | Content |
|---|---|
| 1–3 | Spark environment setup & initial data exploration |
| 4–5 | Data visualization & feature engineering |
| 6 | Storage management (Parquet format, HDFS) |
| 7–8 | Model training, algorithm comparison & model export |
| 9–10 | Pipeline deployment & structured streaming test |

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Big Data Processing | PySpark (Spark SQL, MLlib) |
| Data Analysis | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| ML Models | Logistic Regression, Random Forest, GBT (via MLlib) |
| Infrastructure | Google Colab / Hadoop HDFS |

---

## Key Results

- Random Forest achieves **~86% Recall** on positive stroke cases, minimizing the risk of missed diagnoses.
- PCA and correlation analysis reveal **age, glucose level, and hypertension** as the strongest predictors.
- The full Spark pipeline is exportable and compatible with real-time streaming inference.

---

## Authors

| Name | Institution |
|---|---|
| Fatima Igueroufa | Université de Technologie de Compiègne (UTC) |
| Louis-Philippe Robichaud | Université de Technologie de Compiègne (UTC) |
| Tareq Derdaki | Université de Technologie de Compiègne (UTC) |

**Course:** MTI850  
**Institution:** [Université de Technologie de Compiègne (UTC)](https://www.utc.fr)

---

> **Reference:** World Health Organization (WHO). *Global Health Estimates.* [who.int](https://www.who.int)
