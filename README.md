# 🧳 Travel Insurance Purchase Prediction

Predicting which customers are likely to buy travel insurance — and understanding *why* they do.

---

## Business Problem

A travel company launched an insurance product covering Covid-19 in 2019. Rather than marketing to all customers equally, they want to identify **who is most likely to buy** — so outreach can be targeted, conversion rates improved, and marketing budget better spent.

**Question:** Given a customer's profile, will they purchase travel insurance?

---

## Dataset

- **Source:** [Travel Insurance Prediction Dataset — Kaggle](https://www.kaggle.com/datasets/tejashvi14/travel-insurance-prediction-data)
- **Size:** 1,987 customers × 9 features
- **Target:** `TravelInsurance` (1 = purchased, 0 = did not purchase)
- **Class balance:** 36% positive, 64% negative

| Feature | Description |
|---|---|
| Age | Customer age (25–35) |
| Employment Type | Government vs Private/Self-employed |
| GraduateOrNot | College graduate or not |
| AnnualIncome | Yearly income in Indian Rupees |
| FamilyMembers | Number of family members |
| ChronicDiseases | Has chronic illness (diabetes, high BP, etc.) |
| FrequentFlyer | Booked flights 4+ times in last 2 years |
| EverTravelledAbroad | Has international travel experience |

---

## Key Findings

**Top 3 drivers of insurance purchase:**

1. **EverTravelledAbroad** — strongest predictor. Customers with international travel experience buy at **78%** vs only **26%** for those without — a 3× difference.
2. **AnnualIncome** — acts as a threshold. Bottom 75% of earners purchase at 19–26%, while top quartile jumps to **80%**.
3. **FrequentFlyer** — frequent flyers buy at **57%** vs 30% for others.

**Power segment:** Frequent flyers who have also travelled abroad convert at **88%** — the highest-value target group.

**Minimal predictors:** Chronic diseases and education level show near-zero correlation with purchase — not useful for segmentation.

---

## Approach

```
Raw Data → EDA & Insight → Preprocessing → Model Comparison → Evaluation → Business Recommendations
```

Three Naive Bayes variants compared inside scikit-learn Pipelines with GridSearchCV:

| Model | Scaler | Best F1 |
|---|---|---|
| **Gaussian NB** ✅ | StandardScaler | **0.576** |
| Multinomial NB | MinMaxScaler | — |
| Bernoulli NB | MinMaxScaler | — |

---

## Results

| Metric | Score |
|---|---|
| Accuracy | 76.6% |
| Precision | 81.2% |
| Recall | 44.6% |
| **F1-Score** | **57.6%** |
| ROC-AUC | 74.2% |

**Why F1?** Class imbalance makes accuracy misleading. F1 balances the cost of false positives (wasted outreach) and false negatives (missed buyers).

---
