# 📉 Pairs Trading & Cointegration Strategy

A quantitative trading strategy implemented in Python that leverages strong cointegration between stock pairs to execute market-neutral trades. 
This approach aims to profit from the relative performance of two securities while minimizing exposure to overall market risk. It profits from statistical arbitrage, working on the principle of mean-reversion.

---

## 📌 Problem

Stock markets are highly volatile and influenced by factors like investor sentiment, macroeconomic indicators, and global events. Traditional long-only strategies can suffer from broad market downturns.

---

## ✅ Solution

A **market-neutral strategy** like pairs trading helps hedge against systemic risk by simultaneously taking long and short positions in two cointegrated stocks. This way, we exploit the relative price movement of the stocks rather than their absolute direction.

---

## 🎯 Motivation

Design a market-neutral trading strategy that capitalizes on the strong cointegration between a selected pair of stocks. The objective is to earn consistent alpha while maintaining low exposure to market-wide volatility.

---

## ⚙️ Technical Workflow

### 1. 📊 Pair Selection

- **Pearson Correlation (Pre-test)**  
  - Identify stock pairs from the same sector with strong historical correlation (threshold > 0.9).

- **Engle-Granger Cointegration Test**  
  - Perform hypothesis testing by regressing one non-stationary time series on another.
  - If the residuals are stationary, the pair is cointegrated. (p-value of null hypothesis < 0.01)

- **Hedge Ratio Determination**  
  - Use linear regression on cointegrated pairs.
  - Select pair with hedge ratio closest to 1 (balanced exposure).

✅ **Selected pair**: `COALINDIA` and `ONGC`

---

### 2. 🧮 Trading Logic

- **Spread Calculation**  
  - Spread = Price of COALINDIA − Hedge Ratio × Price of ONGC

- **Z-Score of Spread**  
  - Computed using a 14-day rolling mean and standard deviation.  
  \[
  Z = \frac{\text{Spread}_t - \mu}{\sigma}
  \]

- **Trade Entry/Exit Logic**  
  - Enter long–short positions based on Z-score thresholds.
  - Close positions when Z-score reverts to mean.

---

### 3. 📈 Performance Metrics

- **CAGR**: 20.96% over 996 trading days  
- **Sharpe Ratio**: 1.13  
- **Sortino Ratio**: 1.85  
- **Maximum Drawdown**: −14.47%  
- **Trade Frequency**: ~77 trades per year

> ✅ Strategy demonstrates strong excess return per unit of volatility and effective drawdown recovery. Most volatility comes from profitable upward movement.

---

## 🧪 Possible Improvements

- **Johansen Cointegration Test**  
  - Enables multivariate cointegration analysis (multiple assets).
  - Identifies the rank of cointegration to find multiple stationary linear combinations.

- **Dynamic Hedge Ratio**  
  - Implement time-varying hedge ratios via Kalman Filters or rolling regressions.

- **Stop-loss / Take-profit Enhancements**  
  - Add layered exit rules to optimize risk management.

---

## 🛠 Tech Stack

- Python 3.x  
- pandas, NumPy  
- statsmodels  
- matplotlib, seaborn  
- scikit-learn (for regression and preprocessing)

---
