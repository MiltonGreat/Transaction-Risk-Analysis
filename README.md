# # Credit Risk Model Bias Audit with SHAP & LIME

### Project Overview

This project implements an unsupervised fraud detection system using the Local Outlier Factor (LOF) algorithm to flag anomalous transactions in a simulated banking dataset. The model analyzes features like transaction amount, timing, and customer behavior (where available) to assign risk scores.

### Dataset

Simulated financial transactions with:
- Features: CustomerID, Timestamp, Amount, Transaction Hour/Day, Weekend flag
- Limitations: Single transaction per customer (no behavioral history)

### Methodology

1. Feature Engineering

Time-based features:
- Hour/day of transaction
- Weekend vs. weekday
- Time since last transaction (if available)

Customer behavior (when multiple transactions exist):
- Average amount, spending consistency, time patterns

2. Anomaly Detection

Algorithm: Local Outlier Factor (LOF)
- Flags transactions deviating from local density patterns
- contamination=0.01 (default: 1% expected outliers)
- Scaling: RobustScaler (resistant to outlier distortion)

3. Output
- LOF_Score: Anomaly score (lower = more suspicious)
- LOF_Outlier: Binary flag (1 = outlier, 0 = normal)

### Results

Flagged Patterns:

- Negative amounts (potential reversals)
- Unusual hours (e.g., 3 AM transactions)
- Extreme amounts

### Key Limitations

1. Single-Transaction Customers:
- Cannot detect behavioral anomalies (e.g., sudden spending spikes).

2. Unsupervised Approach:
- No ground truth to validate precision/recall.

3. Feature Simplicity:
- Lacks contextual data (e.g., merchant category, location).

### Conclusion

While this implementation successfully identified structural outliers, true fraud detection requires richer transaction history and labeled data. Future work should focus on expanding the dataset, refining features, and validating results against known fraud cases to build a more robust risk-scoring system.

### Source

[Synthetic Bank Transfers Dataset from Kaggle](https://www.kaggle.com/datasets/nyingsha/synthetic-bank-transfers)
