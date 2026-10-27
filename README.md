# NVIDIA (NVDA) Risk and Return Analysis, 1999 to 2026

**Question:** How has NVDA's risk and return profile changed over time, and how does it compare to the S&P 500?

**Notebook:** [nvda_risk_return_analysis.ipynb](nvda_risk_return_analysis.ipynb) (runs in Google Colab)

## Data
- Kaggle: *Nvidia Historical Stock Data* (6,958 daily observations, 1999-01-22 to 2026-09-21). [Add the dataset link here.](https://www.kaggle.com/datasets/muhammadishahrukh/nvidia-historical-stock-data)
- Benchmark: SPY (S&P 500 ETF) from Yahoo Finance via `yfinance`.
- Only the raw price and volume columns were used. All returns and risk metrics were recomputed from scratch.

## Data validation
- No missing values, duplicate dates, non-positive prices, or rows where high < low.
- Prices are split-adjusted (first close about $0.04; largest one-day drop is -35.2%).
- Recomputed returns match the dataset's own return columns to within 1e-9.

## Method
Annualized return, volatility, Sharpe ratio, max drawdown, 1-day 95% VaR and CVaR, calculated overall and by 5-year era. Rolling volatility and Sharpe, a drawdown and recovery table, and a benchmark comparison against SPY (beta, correlation, growth of $10,000).

## Key findings
| Metric | NVDA | SPY |
|---|---|---|
| Annualized return | 37.1% | 8.8% |
| Annualized volatility | 59.2% | 19.2% |
| Sharpe ratio | 0.58 | 0.30 |
| Max drawdown | -89.7% | -55.2% |

- **Beta vs SPY is 1.64** (correlation 0.53). Beta was about 2.0 in 2000 to 2004, about 1.4 in 2005 to 2014, and 1.88 in 2025 to 2026.
- **Deep drawdowns:** NVDA fell more than 60% four times. The 2007 to 2008 fall took about 7.4 years to recover; the 2022 fall recovered in about 7 months.
- **$10,000 invested in January 1999 grew to about $60.6 million**, versus about $102,000 for SPY. This is a hindsight result, not a realistic expectation.

## Limitations
- Survivorship bias: NVDA is a famous winner.
- A single stock, not a diversified portfolio.
- Flat 3% risk-free rate assumed for all years.
- NVDA's price basis is unspecified, while SPY is dividend-adjusted.
- Past performance does not predict future results.

## How to run
1. Download the dataset from Kaggle and save it as `nvda_stock_clean.csv`.
2. Open the notebook in Colab, upload the CSV, and click **Runtime → Run all**.

## Tools
Python, pandas, NumPy, matplotlib, seaborn, yfinance
