# Mushroom Classification Using Machine Learning 🍄

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Keras](https://img.shields.io/badge/Keras-2.0%2B-red.svg)](https://keras.io)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-Latest-orange.svg)](https://scikit-learn.org/)

An end-to-end machine learning project focusing on classifying mushrooms as either **edible** or **poisonous** based on their physical characteristics. This repository implements and evaluates a classical baseline model (**Random Forest**) and a deep learning approach (**Dense Neural Network / MLP**).

This project was developed for the **Adaptive Computation and Machine Learning (COMS 4030A / COMS 7047A)** course at the **University of the Witwatersrand**.

---

## 👥 Authors
* **Mashego Mabeloane** (Student Number: 2654606)
* **Dolf Shungube** (Student Number: 2683067)
* *University of the Witwatersrand — May 2026*

---

## 📊 Project Quick Glance

* **Dataset:** [UCI Machine Learning Repository - Mushroom Dataset](https://archive.ics.uci.edu/ml/datasets/mushroom) (8,124 instances, 22 categorical features).
* **Objective:** Build robust predictive models to accurately differentiate edible mushrooms from toxic ones using physical features.
* **Core Methodology:** * Statistical feature selection using Chi-Square ($\chi^2$) test ranking.
  * Structural comparisons across different feature counts (Tier 1 vs Tier 2 features).
  * Layer configuration experiments for Deep Learning.

> 📄 **Note:** For the full mathematical formulations, comprehensive training curves, data cleaning pipeline details, and deep architectural discussion, please refer to our complete [Machine Learning Report](./Machine_Learning_Report.pdf).

---

## ⚙️ Feature Selection Strategy

Features were analyzed using a Chi-Square test and grouped into priority tiers based on their statistical significance ($p$-values):

* **Tier 1 (Most Informative):** Top 12 features heavily correlated with edibility (e.g., `odor`, `spore-print-color`, `gill-color`).
* **Tier 2:** Features with lower (but significant) correlation (e.g., `stalk-root`, `cap-shape`).
* **Dropped Feature:** `veil-type` was entirely removed from modeling as its statistical score was 0.0, providing zero discriminative power.

---

## 🏆 Final Performance Matrix

The performance metrics of our final model variations evaluated on the unseen **Test Split**:

| Model Architecture | Feature Set Used | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | Tier 1 Only | **1.00** | **1.00** | **1.00** | **1.00** |
| **Random Forest** | Tier 1 + Tier 2 | **1.00** | **1.00** | **1.00** | **1.00** |
| **Dense Neural Network** | Tier 1 Only | `0.99` | `0.99` | `0.99` | `0.99` |
| **Dense Neural Network** | Only *Odor* feature | `0.98` | `0.98` | `0.99` | `0.99` |

### Key Takeaways:
1. **Feature Efficiency:** Random Forest converged perfectly to 100% accuracy using only Tier 1 features. Adding Tier 2 features introduced mild noise at shallow tree depths without improving final performance.
2. **The "Odor" Factor:** Training a Neural Network solely on the `odor` feature yields an impressive 98% accuracy. However, to guarantee absolute food safety, a multi-feature approach remains essential.

---

## 📁 Repository Structure

```text
├── Data/                       # Raw and preprocessed dataset files
├── Notebooks/                  # Jupyter notebooks containing experiments
├── Machine_Learning_Report.pdf # Full academic project report and analysis
└── README.md                   # Project summary (this file)
