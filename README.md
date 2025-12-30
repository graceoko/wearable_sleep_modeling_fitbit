# Wearable Sleep Modeling Using Fitbit Data

## Overview
This project explores how daily activity patterns captured by consumer wearables can be used to predict sleep duration and classify sleep quality. Using Fitbit activity and sleep data, I developed and evaluated machine learning models to understand which behavioral factors most strongly influence sleep outcomes and how those insights could translate into practical, user-facing guidance.

Rather than treating sleep prediction as a purely technical task, this project emphasizes interpretability, validation, and real-world relevance—examining how simple daily behaviors relate to meaningful health outcomes and how wearable data can support scalable sleep monitoring. :contentReference[oaicite:2]{index=2}

---

## Dataset
The analysis uses the publicly available **Fitbit Fitness Tracker Dataset** from Kaggle, which includes approximately one month of data from 30 adults.

Key data sources:
- **Daily activity data:** steps, distances, calories, and activity intensity
- **Minute-level sleep data:** asleep, restless, and awake labels
- **Derived daily sleep summaries:** total minutes asleep, time in bed, and awake time

Minute-level sleep records were aggregated into daily summaries and merged with daily activity data by participant ID and date, producing a dataset suitable for both regression and classification tasks. :contentReference[oaicite:3]{index=3}

---

## Problem Formulation
Two prediction tasks were defined:

- **Regression:** Predict nightly sleep duration (`TotalMinutesAsleep`)
- **Classification:** Predict sleep quality by labeling nights as:
  - *Good sleep* (≥ 7 hours)
  - *Poor sleep* (< 7 hours)

This framing allowed evaluation of both continuous sleep outcomes and decision-oriented classifications relevant to real-world health applications. :contentReference[oaicite:4]{index=4}

---

## Methodology
### Data Preparation
- Aggregated minute-level sleep data into daily metrics
- Merged activity and sleep data by participant and date
- Removed days with missing sleep or activity records
- Standardized predictors using z-scores
- Split data into training and test sets (80/20) with a fixed random seed for reproducibility

### Features
Twelve activity-based predictors were used, including:
- Sedentary, light, moderate, and very active minutes
- Distance-based activity measures
- Total daily calories

Missing activity values were imputed as zeros when no activity was logged. :contentReference[oaicite:5]{index=5}

---

## Models Evaluated
### Classification Models
- Decision Tree
- K-Nearest Neighbors
- Support Vector Machine (RBF)
- Logistic Regression
- Random Forest
- Gradient Boosting

Models were ranked using a weighted score combining test accuracy, F1-score, and cross-validation stability to prioritize both performance and robustness.

### Regression Models
- Decision Tree Regressor
- KNN Regressor
- Support Vector Regressor
- Ridge Regression
- Random Forest Regressor
- Gradient Boosting Regressor

Performance was evaluated using R² and mean absolute error (MAE). :contentReference[oaicite:6]{index=6}

---

## Results & Key Insights
- **Gradient Boosting** was the top-performing classifier, achieving:
  - 85% test accuracy
  - F1-score of 0.83
  - Strong cross-validation stability
- **Random Forest Regression** explained ~69% of the variance in sleep duration with an average error of ~61 minutes.

### Behavioral Insight
**SedentaryMinutes** emerged as the dominant predictor across both tasks:
- Accounted for ~68% of feature importance in regression
- Showed a strong negative correlation with sleep duration (r = −0.58)

Practically, participants with higher sedentary time slept ~78 minutes less per night, while reducing sedentary behavior by 30–60 minutes per day corresponded to meaningful increases in sleep duration. :contentReference[oaicite:7]{index=7}

---

## Why This Matters
These findings suggest that:
- Simple daily activity summaries contain actionable signals for sleep health
- Reducing sedentary time may have a larger impact on sleep than increasing vigorous exercise
- Wearable-derived behavioral data can support scalable, low-cost sleep monitoring and guidance

This work demonstrates how machine learning can move beyond prediction toward insight generation that supports real-world behavior change. :contentReference[oaicite:8]{index=8}

---

## Limitations
- Small sample size (n = 30)
- Limited behavioral and contextual variables (e.g., stress, caffeine, screen time)
- Reliance on daily summaries rather than minute-level time series
- Consumer-grade wearable measurements instead of PSG

---

## Future Work
- Apply the pipeline to multimodal datasets such as DREAMT
- Incorporate minute-level time-series modeling and deep learning approaches
- Add contextual and behavioral covariates
- Explore sleep regularity and circadian rhythm metrics

---

## Artifacts
- **Notebook:** End-to-end data processing, modeling, and evaluation
- **Technical Report:** Extended written analysis with detailed methodology and discussion
- **Presentation:** High-level walkthrough of motivation, approach, and findings

Each artifact targets a different audience, reflecting how analytics and AI work is communicated across technical and non-technical stakeholders. :contentReference[oaicite:9]{index=9}
