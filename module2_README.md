# Credit Card Fraud Detection — Advanced Feature Engineering

**Author:** Sankalp Chudmunge  
**Module:** Python Data Science — Module 2: Advanced Preprocessing & Feature Engineering

## Dataset

Synthetic credit card transaction dataset modeled after the [IEEE-CIS Fraud Detection](https://www.kaggle.com/c/ieee-fraud-detection) structure. Generated with realistic class imbalance (~3.5% fraud rate), missing value patterns, and feature correlations.

## What This Notebook Does

### Missing Value Handling (4 strategies)
- **KNN Imputation** for `account_age_days` — 5-neighbor interpolation preserves local distribution
- **Median Imputation** for `dist_from_home` — robust to outliers in skewed data
- **Zero-fill** for `previous_frauds` — domain reasoning: no record means no prior fraud
- **'Unknown' category** for categorical NAs — avoids silent information loss

### Categorical Encoding (2 strategies)
- **One-hot encoding** for low-cardinality features (`card_type`, `device_type`)
- **Frequency encoding** for `merchant_category` and `entry_mode` — avoids sparse matrices while preserving frequency signal

### Numerical Scaling
- **RobustScaler** for `transaction_amt` and `dist_from_home` (outlier-heavy distributions)
- **StandardScaler** for `account_age_days` (approximately normal after imputation)

### Engineered Features (4 new features)
1. `is_night_transaction` — binary flag for 11pm–5am transactions
2. `risk_score` — composite of prior fraud history, distance from home, and time of day
3. `amt_per_account_age` — transaction size relative to account maturity (new accounts + high amounts = risk)
4. `repeat_fraud_flag` — binary prior-fraud indicator

All 4 engineered features appear in the top 15 feature importances of a Random Forest validation model.

## Key Findings

- Night transactions have a measurably higher fraud rate than daytime transactions
- The `risk_score` composite feature clearly separates fraud from non-fraud distributions
- High-value transactions on new accounts (`amt_per_account_age`) is one of the strongest fraud signals
- ROC-AUC improves meaningfully with engineered features vs raw features alone

## How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook module2_creditcard_features.ipynb
```
