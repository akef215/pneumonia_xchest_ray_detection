# Chest X-ray Pneumonia Classification

This project focuses on the automatic classification of chest X-ray images for **pneumonia detection** using both **classical machine learning approaches** and **deep learning-based feature extraction**.

We compare handcrafted image descriptors (GLCM, HOG, LBP) combined with traditional classifiers to CNN-extracted features from a pre-trained ResNet-50 model, followed by statistical validation using cross-validation and p-value analysis.

---

## 📌 Objectives

- Detect pneumonia from chest X-ray images
- Compare handcrafted image descriptors and CNN-based features
- Evaluate classical machine learning classifiers
- Perform statistical comparison of the best-performing models using p-values

---

## 🗂 Dataset

- **Name:** Chest X-ray Pneumonia
- **Source:** Kaggle / Mendeley  
- **Images:** Anterior-posterior chest radiographs  
- **Classes:** Normal / Pneumonia  
- **Patients:** Pediatric (1–5 years old)

Due to class imbalance, an **undersampling strategy** was applied to the majority class.

---

## ⚙️ Preprocessing

- Image resizing to **224 × 224**
- Grayscale normalization
- Dataset balancing using undersampling

---

## 🧠 Feature Extraction

### Handcrafted descriptors
- **GLCM + first-order statistics**
  - 122 features
  - 10 distances, 4 angles
- **HOG**
  - 144 features
- **LBP**
  - 122 features

### CNN-based features
- **ResNet-50** pre-trained on ImageNet
- Extraction of **2048 deep features**
- Feature standardization and **PCA (120 components)**

---

## 🤖 Classification Models

- Logistic Regression (L2 regularization)
- Support Vector Machine (RBF kernel)

CNN-extracted features are classified using the same ML models to ensure fair comparison.

---

## 📊 Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-score (per class)

Evaluation is performed using **k-fold cross-validation (k = 5)**.

---

## 📈 Statistical Analysis

To assess whether the difference between the two best-performing models is statistically significant:

- Paired **t-test**

The analysis is conducted on cross-validation scores.

---

## 🏆 Results Summary

| Features + Classifier | Accuracy |
|----------------------|----------|
| HOG + SVM            | 84%      |
| CNN Features + SVM   | 84%      |


---

## 📁 Project Structure

```text
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   ├── rapport.ipynb
├── results/
│   ├── figures/
│   └── metrics/
├── requirements.txt
└── README.md
