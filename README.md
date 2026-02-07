# AI-driven Time Series Forecasting – S&P 500 Returns
Course project on forecasting S&amp;P 500 returns using feature-engineered models and foundation models.

## Project Overview
This project focuses on **next-day return forecasting** for S&P 500 constituent stocks using daily log returns.
The objective is to compare **feature-engineered statistical models** with a **pretrained foundation time series model (Chronos)** under a strict out-of-sample evaluation framework, and to analyze their robustness in high-noise financial data.

---

## Data
- **Universe:** S&P 500 constituent stocks  
- **Frequency:** Daily closing prices  
- **Sample size:** 500+ stocks, 250 trading days per stock  
- **Target variable:** Next-day log return  

All experiments use **time-based train/test splits** to avoid look-ahead bias.

---

## Feature Engineering
For the statistical baseline, features were constructed from historical returns, including:
- Lagged returns to capture short-term dynamics
- Rolling statistics (mean and volatility over multiple windows)

These features are designed to model **momentum effects** and **volatility clustering** commonly observed in financial time series.

---

## Models
The following models were implemented and compared:

- **Ridge Regression**
  - Used as a global baseline trained across all stocks
  - Provides stability under multicollinearity and noisy inputs

- **Chronos (Pretrained Transformer-based Time Series Model)**
  - Applied in a rolling-window forecasting setup
  - Used without domain-specific fine-tuning to assess out-of-the-box performance

---

## Evaluation
Models were evaluated using:
- **Out-of-sample MAE and RMSE**
- **Rolling-window analysis** to assess robustness and regime sensitivity

This evaluation design enables performance comparison across different market conditions rather than relying on a single static split.

---

## Key Findings
- Feature-engineered linear models delivered **more stable and reliable performance** than the pretrained foundation model in high-noise return prediction tasks
- Chronos showed limited advantage without domain adaptation, highlighting the importance of **problem-specific feature engineering** in financial forecasting
- Rolling-window evaluation revealed strong **regime sensitivity**, reinforcing the inherent difficulty of return prediction

---

## Project Structure
```text
├── data_processing.ipynb
├── feature_engineering.ipynb
├── ridge_model.ipynb
├── chronos_baseline.ipynb
├── evaluation.ipynb
└── README.md
