# Click-Through Rate (CTR) Prediction – Avazu Dataset

## Overview
This project implements an end-to-end machine learning pipeline to predict Click-Through Rate (CTR) for online ads using the Avazu CTR dataset. The goal is to estimate the probability of a click for each ad impression using contextual and device-level features.

The project follows a realistic ML Software Development Lifecycle (ML SDLC), focusing on correct validation, feature handling, and incremental model improvements rather than brute-force scaling.

---

## Dataset
- **Source:** Avazu CTR Prediction Dataset
- **Scale:** ~40 million ad impressions
- **Target Variable:** `click` (binary classification)

Due to the dataset size, a representative subset was sampled for model development and experimentation.

> Note: Raw data is not included in this repository due to size constraints.

---

## ML SDLC Followed

### 1. Problem Framing
- Binary classification: Predict probability of click per ad impression.
- Business metric alignment with online advertising systems.

### 2. Data Handling
- Large-scale tabular data ingestion.
- Responsible sampling for development.
- No manual data entry; features represent machine-generated ad request context.

### 3. Feature Engineering
- Contextual features: site, app, placement, device, connection type
- Numerical features: engineered anonymous variables
- High-cardinality categorical features handled carefully.

### 4. Validation Strategy
- **Strict time-based train-validation split**
- Prevents future data leakage (critical for CTR modeling)

### 5. Modeling Approach
- Baseline: Global CTR benchmark
- Logistic Regression: Linear baseline model
- XGBoost: Non-linear model capturing feature interactions

### 6. Evaluation Metric
- **Log-loss** (industry standard metric for CTR prediction)

---

## Results

| Model                | Log-loss |
|---------------------|----------|
| Baseline            | 0.4669   |
| Logistic Regression | 0.4546   |
| **XGBoost**         | **0.4289** |

XGBoost achieved a significant improvement over both the global CTR baseline and the linear model.

---

## Key Learnings
- Correct validation strategy matters more than model complexity.
- Incremental modeling (baseline → linear → tree-based) is essential.
- Tree-based models outperform linear models in CTR due to non-linear interactions.
- Scaling to full data is an engineering decision once correctness is proven.

---

## Repository Structure
- `notebooks/` – End-to-end modeling workflow
- `images/` – Pipeline and metrics visualizations
- `data/` – Dataset instructions (no raw data)

---

## Technologies Used
- Python
- Pandas, NumPy
- scikit-learn
- XGBoost

---

## Author
Chauhan Rahul
