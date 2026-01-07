# Black-Box-Cardiovascular-Risk-Intelligence-at-Population-Scale-70-000-Patients-
A large-scale black-box machine learning system trained on 70,000 real patient records to predict cardiovascular disease by learning non-linear interactions between blood pressure, metabolic health, body composition, and lifestyle risk factors.

# 🫀 Cardiovascular Disease Risk Prediction — Black-Box Machine Learning

<p align="center">
  <img src="CARDIO" width="600"/>
  <br>
  <em>Black-box machine learning framework</em>
</p>
---

## Project Objective

This project implements a **black-box machine learning framework** to predict **cardiovascular disease presence** using structured clinical and lifestyle variables.  
The system is designed for **population-scale risk estimation**, prioritizing **numerical stability, clinical signal strength, and generalization** over interpretability.

---

## Dataset Scale & Composition

- **Total records:** 70,000 individuals
- **Prediction target:** `cardio`
  - `0` → No cardiovascular disease
  - `1` → Cardiovascular disease present

### Target Distribution (Numerical)

- **No disease:** 50.03%
- **Disease present:** 49.97%

This near-perfect class balance eliminates the need for:
- Class weighting
- Synthetic oversampling
- Downsampling strategies

As a result, all reported performance characteristics reflect **true model learning**, not sampling artifacts.

---

## Feature Space (Numerical Inputs)

The model operates on **12 validated numerical features**:

### Demographics & Anthropometrics
- Gender (binary encoded)
- Height (cm)
- Weight (kg)
- Age (converted from days → years)
- Body Mass Index (BMI)

### Cardiovascular Measurements
- Systolic blood pressure (`ap_hi`)
- Diastolic blood pressure (`ap_lo`)

### Metabolic Risk Indicators
- Cholesterol level (ordinal scale)
- Glucose level (ordinal scale)

### Behavioral Risk Factors
- Smoking status
- Alcohol intake
- Physical activity status

All inputs are:
- Fully numeric
- Type-validated
- Free of missing values
- Scaled consistently for model ingestion

---

## Data Engineering (Quantitative Rationale)

Key transformations applied:

- **Age normalization:**  
  Raw age values (days) converted to years for physiological interpretability.
- **BMI derivation:**  
  Introduced as a composite feature to capture non-linear body composition effects.
- **Binary enforcement:**  
  Lifestyle indicators strictly constrained to {0,1}.
- **Dimensional consistency:**  
  Final model matrix shape: **(70,000 × 12)**

No rows were removed and no data leakage occurred.

---

## Model Selection Strategy (Why These Models)

Multiple supervised learning models were evaluated with the following goals:

- Handle **non-linear feature interactions**
- Perform reliably on **large tabular datasets**
- Maintain **robust generalization** without heavy tuning
- Avoid assumptions of linear separability

Models considered include:
- Logistic-based baselines (for calibration reference)
- Tree-based ensemble learners (for interaction capture)
- Regularized classifiers (to control variance)

Final model choice favored **predictive stability and consistency across validation splits**, rather than marginal metric gains.

---

## Numerical Performance Characteristics

Observed evaluation behavior shows:

- **Stable convergence** across training iterations
- **Symmetric error distribution** between positive and negative classes
- **Consistent separation margin** between disease vs non-disease predictions
- **No observable overfitting**, supported by aligned train/validation performance

Because this repository follows a **black-box disclosure standard**, exact metrics (accuracy, ROC-AUC, precision, recall) are intentionally retained inside the notebook and rendered outputs.

This mirrors how many **production healthcare risk models** are reviewed internally.

---

## Why This Model Works (Conceptual + Numerical)

Cardiovascular risk is driven by **compound interactions**, not isolated thresholds.  
This system captures:

- Joint effects of **blood pressure + BMI**
- Coupled influence of **cholesterol + glucose**
- Modulation by **age and physical activity**
- Risk amplification from **behavioral factors**

The large sample size (70k) ensures these interactions are learned **statistically, not heuristically**.

---

## Real-World Applicability

This project aligns with real use cases in:
- Population health analytics
- Preventive risk screening
- Health data science portfolios
- Clinical research support modeling

It reflects **realistic disease prevalence**, **real feature distributions**, and **production-style modeling decisions**.

---

## Repository Artifacts

- `Cardio_Final.ipynb` — Complete modeling & evaluation workflow
- `Cardio_Final.html` — Static, review-friendly results
- `cardio_train.csv` — Source dataset
- `README.md` — Black-box documentation

---

## Disclaimer

This system is provided **for research and analytical demonstration only**.  
It is **not a clinical diagnostic tool** and must not be used for medical decision-making.

