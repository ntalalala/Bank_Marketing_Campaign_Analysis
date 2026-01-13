# Bank Marketing Campaign Analysis

## 1. Project Overview

This project analyzes a **bank marketing campaign dataset** to predict whether a client will subscribe to a term deposit. The analysis includes comprehensive exploratory data analysis (EDA), feature engineering, and machine learning model development with hyperparameter optimization.

### Objectives
- Understand customer demographics and campaign characteristics
- Identify key factors influencing subscription decisions
- Build predictive models to optimize future marketing campaigns
- Provide actionable business recommendations

---

## 2. Dataset Description

- **Source**: [UCI Machine Learning Repository - Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/bank+marketing)
- **File**: `bank-additional-full.csv`
- **Records**: ~41,000+ client records
- **Features**: 20 input features + 1 target variable

### Feature Categories

| Category | Features |
|----------|----------|
| **Client Demographics** | `age`, `job`, `marital`, `education` |
| **Financial Status** | `default`, `housing`, `loan` |
| **Campaign Information** | `contact`, `month`, `day_of_week`, `duration`, `campaign`, `pdays`, `previous`, `poutcome` |
| **Economic Indicators** | `emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed` |
| **Target Variable** | `y` (yes/no - subscribed to term deposit) |

---

## 3. Exploratory Data Analysis

### Data Quality
- No missing values (but contains `unknown` values in categorical features)
- Duplicate records removed
- **Imbalanced Dataset**: ~88.7% "No" vs ~11.3% "Yes" (8:1 ratio)

### Key Insights

#### Target Customer Profile
| Attribute | Profile |
|-----------|---------|
| **Age** | 26-60 years |
| **Job** | Admin, Technician |
| **Education** | University degree |
| **Marital Status** | Married |
| **Credit Default** | No |
| **Personal Loan** | No |
| **Housing Loan** | Yes |

#### Campaign Characteristics
| Metric | Finding |
|--------|---------|
| **Best Month** | March, September, October show higher conversion rates |
| **Contact Method** | Cellular performs better than telephone |
| **Optimal Duration** | Longer calls (>5 mins) correlate with higher conversion |
| **Previous Contact** | Clients with successful previous outcomes have higher conversion |

---

## 4. Data Preprocessing

### Steps Performed
1. **Duplicate Removal** - Eliminated redundant records
2. **Feature Engineering** - Created age groups, duration bins, campaign categories
3. **Handling Imbalance** - Applied SMOTE (Synthetic Minority Over-sampling Technique)
4. **Encoding** - Label encoding for categorical variables
5. **Scaling** - StandardScaler for numerical features

### Pipeline Components
```python
Pipeline([
    ('preprocess', ColumnTransformer),
    ('smote', SMOTE(sampling_strategy=0.5)),
    ('model', Classifier)
])
```

---

## 5. Machine Learning Models

### Models Evaluated
| Model | Framework |
|-------|-----------|
| Logistic Regression | scikit-learn |
| Random Forest | scikit-learn |
| XGBoost | xgboost |
| **LightGBM** | lightgbm |
| **CatBoost** | catboost |

### Hyperparameter Tuning
- **Method**: Optuna (Bayesian Optimization)
- **Trials**: 20 trials per model
- **Cross-Validation**: 5-fold Stratified K-Fold
- **Metric**: F1-Score (Fbeta with β=1)

### Threshold Optimization
Custom threshold tuning was performed to optimize the F1-score instead of using the default 0.5 probability threshold.

---

## 6. Results

### Single Model Performance

| Model | Threshold | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|-------|-----------|----------|-----------|--------|----------|---------|
| LightGBM | ~0.45 | ~0.90 | ~0.52 | ~0.58 | ~0.55 | ~0.93 |
| CatBoost | ~0.40 | ~0.89 | ~0.48 | ~0.62 | ~0.54 | ~0.93 |

### Ensemble Methods

| Method | Description | Performance |
|--------|-------------|-------------|
| **Probability Averaging** | Simple average of LightGBM + CatBoost probabilities | Improved F1 |
| **Weighted Averaging** | Optimized weights for each model | Better precision-recall balance |
| **Stacking (Meta-Learner)** | Logistic Regression as meta-learner | Best overall performance |

### Best Model
The **Stacking Ensemble** with Logistic Regression meta-learner achieved the best F1-score, combining the strengths of both LightGBM and CatBoost.

---

## 7. Business Recommendations

### Target Customer Segments
1. **Primary Focus**: Ages 26-60, Admin/Technician jobs, University education
2. **Expansion Opportunities**: Students, Retirees (high conversion but low volume)
3. **Financial Profile**: No credit default, no personal loan, has housing loan

### Campaign Optimization
1. **Timing**: Focus on March, September, October; target Thursday
2. **Contact Method**: Prioritize cellular contact
3. **Call Duration**: Aim for 5+ minute conversations
4. **Follow-up Strategy**: Re-contact clients with previous successful outcomes

### Marketing Strategies
- **Age 26-60**: Emphasize long-term financial security and investment benefits
- **Age ≤25**: Leverage social media and digital channels
- **Housing Loan Holders**: Offer flexible savings solutions to complement mortgage payments

---

## 8. Technologies Used

| Category | Tools |
|----------|-------|
| **Language** | Python 3.x |
| **Data Manipulation** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Machine Learning** | scikit-learn, LightGBM, CatBoost, XGBoost |
| **Imbalanced Learning** | imbalanced-learn (SMOTE) |
| **Hyperparameter Tuning** | Optuna |
| **Model Persistence** | Joblib, JSON |

---
