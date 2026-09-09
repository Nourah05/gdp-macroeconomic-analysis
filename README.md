# Economic Analysis and GDP Prediction

Team project for Fundamentals of Data Science & AI, Abdullah Al-Salem University.
Team: Sedra Al-Basha, Nourah Al-Sehali

## Overview

This project analyzes global macroeconomic patterns from 2010–2023 across 45+ countries — including advanced, emerging, and resource-driven economies — to understand how national economies evolve over time and to what extent GDP can be predicted from other macroeconomic indicators.

## Research Questions

- How have major macroeconomic indicators changed across countries over time, and what patterns of stability or volatility can be observed?
- What relationships exist between key economic indicators, and how strongly do they explain variation in GDP?
- How accurately can GDP be predicted using macroeconomic indicators (excluding GNI)?
- Which countries show the strongest combined conditions for investment?

## Dataset

International macroeconomic indicators (2010–2023): GDP, GDP Growth, GDP per Capita, Inflation, Unemployment, Government Finance (Expense/Revenue/Tax), Public Debt, Current Account Balance, and Gross National Income (GNI), across a diverse group of European and major global economies.

## Methodology

1. **Data Cleaning & Imputation**
   - Time-series forward/backward fill for short gaps
   - KNN-based imputation (regional-neighbor averaging) for larger gaps
   - Removed high-missingness features (Real Interest Rate, Public Debt)
   - Log transformation of GDP, GNI, and GDP per Capita to correct skew
   - IQR-based outlier detection (outliers retained as genuine economic phenomena)

2. **Exploratory & Comparative Analysis**
   - Average GDP Growth per country (growth leaders vs. stagnating/contracting economies)
   - Risk vs. Reward analysis (GDP growth vs. volatility) to classify countries into investment quadrants
   - Misery Index (Unemployment + Inflation) trends by country and year
   - Post-COVID GDP recovery analysis, indexed to 2019 baseline
   - Government revenue composition (tax vs. non-tax revenue)

3. **Correlation Analysis**
   - Full correlation matrix across all macroeconomic indicators
   - Identified GDP–GNI as mechanically linked (accounting identity), flagging it as a leakage risk for modeling

4. **Predictive Modeling**
   - Linear Regression to predict GDP, tested under two scenarios: with and without GNI as a predictor

## Key Results

- **China, Ireland, Malta** — highest average GDP growth (>6%)
- **North Macedonia** — highest average Misery Index (greatest combined economic pressure)
- **Bulgaria** — fastest post-COVID GDP recovery; **Japan** — slowest
- **Luxembourg** — top-ranked country by composite Investment Score

**Model performance:**

| Scenario | R² | MAE | RMSE |
|---|---|---|---|
| With GNI | 0.9986 | 0.0426 | 0.0760 |
| Without GNI | 0.1075 | 1.5758 | 1.9284 |

The near-perfect R² with GNI included is **misleading** — GNI is mechanically derived from GDP, so the model largely reproduces an accounting identity rather than learning genuine economic relationships. Once GNI is excluded, true predictive difficulty becomes apparent: GDP size is not well explained by short-term macroeconomic indicators alone.

## Key Takeaway

Correctly diagnosing data leakage (GDP–GNI) was central to this project — a high R² is not automatically a good model, and interpreting *why* a model succeeds or fails is as important as the metric itself.

## Tech Stack

Python · pandas · NumPy · scikit-learn · Matplotlib · Seaborn

## Authors

Sedra Al-Basha, Nourah Al-Sehali
