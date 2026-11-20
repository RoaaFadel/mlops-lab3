# Model Selection – Lab 3

## 1. Candidate Models

Three candidate models were trained and evaluated using MLflow:

- Logistic Regression
- Random Forest
- Gradient Boosting

## 2. Overall Performance Comparison

| Metric | Logistic Regression | Random Forest | Gradient Boosting |
|---|---:|---:|---:|
| AUC | 0.798 | 0.778 | 0.759 |
| F1 Score | 0.495 | 0.400 | 0.396 |
| P95 Latency (ms) | 6.4 | 18.26 | 4.839 |
| Model Size (KB) | 4 | 769 | 206 |

## 3. Performance by Contract Type

| Contract Type | Logistic Regression | Random Forest | Gradient Boosting |
|---|---:|---:|---:|
| Month-to-month | 0.543 | 0.480 | 0.417 |
| One-year | 0.250 | 0.000 | 0.250 |
| Two-year | 0.250 | 0.000 | 0.364 |

## 4. Selected Champion

**Logistic Regression** was selected as the champion model.

Reasons for selection:

- Highest overall F1 score (0.495).
- Highest AUC (0.798).
- Best performance on the month-to-month contract group (0.543).
- Smallest model size (4 KB).
- Acceptable inference latency (6.4 ms).

## 5. Trade-offs and Limitations

Gradient Boosting achieved better performance on the two-year contract group (F1 = 0.364) and lower latency (4.839 ms).

However, its overall F1 score and AUC were lower than Logistic Regression.

Logistic Regression also achieved only 0.250 F1 on both one-year and two-year contract groups. This indicates that performance on longer-term contract groups remains a limitation and should be monitored.

Random Forest was not selected because it had lower overall performance, higher latency, and a larger model size.

## 6. Final Decision

Logistic Regression is the selected champion because it provides the strongest overall predictive performance with the smallest deployment footprint.

The promotion gate will enforce the minimum F1 improvement and latency budget before allowing future models to replace the champion.

## 7. Promotion Gate Configuration

- Latency budget: 15.0 ms.
- Minimum F1 improvement: 0.010.

The latency budget was selected to allow Logistic Regression
and Gradient Boosting while blocking the slower Random Forest model.

The minimum F1 gain of 0.010 ensures that a new model must
provide a meaningful improvement before replacing the champion.

Both thresholds balance predictive performance and deployment efficiency.