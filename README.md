# finance-portfolio

# 📈 Financial Investment Portfolio Optimization

This project aims to construct an optimized portfolio of U.S. stocks and bonds using **forecasted returns** and **Modern Portfolio Theory (MPT)**. We evaluate the portfolio's performance against the S&P 500 (SPY) to determine if we can outperform the market on a **risk-adjusted basis**.

---

## 🧠 Problem Statement

**Can we build a portfolio of stocks with a required allocation to bonds—using forecasted returns and Modern Portfolio Theory—that can outperform the S&P 500 on a risk-adjusted basis?**

---

## 📊 Data

- **Source**: Yahoo Finance via `yfinance`
- **Data Range**: 2019–2025
- **Portfolio Candidates**: 50 stocks from various S&P 500 sectors (excluding Utilities)
- **Fixed Income Component**: IEF (iShares 7–10 Year Treasury Bond ETF)
- **Benchmark**: SPY (S&P 500 ETF)

---

## 🔧 Methodology

### 1. Exploratory Data Analysis (EDA)
Basic visualization and summary statistics of stock prices and returns.

### 2. Statistical Pre-Modeling Tests
Before applying time series models, we tested for:
- **Stationarity (ADF Test)**: Checks for unit roots in return series—i.e., whether a time series has a stable mean and variance over time.
- **Trend & Seasonality**: Ensures returns don’t follow predictable patterns that could bias models.
- **Volatility Clustering (ARCH Effects)**: Detects periods of high volatility clustering, important for risk modeling.

### 3. Forecasting with ARIMA
We used **ARIMA(1, 0, 1)** to forecast returns:
- (1, 0, 1) represents 1 autoregressive term, 0 differencing, and 1 moving average term.
- Forecasts were generated for each asset’s log returns to inform portfolio optimization.

### 4. Portfolio Optimization
Using the **forecasted returns** and **historical covariance matrix**, we optimized the portfolio via **Quadratic Utility Maximization**:
- Required allocation to IEF between 10% and 30%.
- Risk aversion preferences explored across a grid of values for diversification.

### 5. Backtesting (Past 12 Months)
We evaluated the selected portfolio against SPY using:
- **Cumulative Returns**
- **Annualized Return & Volatility**
- **Maximum Drawdowns**
- **Rolling Correlation**
- **Alpha & Beta**
- **Sortino Ratio**

---

## 📌 Portfolio Output

**Final Portfolio Recommendation:**

| Ticker | Allocation |
|--------|------------|
| MS     | 44.10%     |
| EOG    | 25.06%     |
| AMT    | 13.05%     |
| PLD    | 1.55%      |
| IEF    | 16.24%     |

✅ **Cumulative 12-month return**: 18.10%  
📉 **S&P 500 return** in same period: 11.48%  
📈 Portfolio **outperformed on a risk-adjusted basis**

---

## ✅ Interpretation Aids

- **Annualized Return & Volatility**: Higher return is desirable; lower volatility indicates smoother performance.
- **Maximum Drawdowns**: Measures the largest peak-to-trough decline, highlighting potential losses.
- **Rolling Correlation**: Evaluates how closely the portfolio tracks the benchmark over time.
- **Alpha & Beta**: Alpha represents excess returns; Beta measures sensitivity to market movement.
- **Sortino Ratio**: Like Sharpe but focuses only on downside volatility, offering a more conservative view of risk-adjusted return.

---

## 🚀 Next Steps

- **Expand to full S&P 500**: Scale from 50 to 500+ stocks for broader exposure.
- **Diversify asset classes**: Include commodities, cryptocurrencies, and possibly derivatives (if feasible).
- **Use advanced libraries**: Integrate tools like [PyPortfolioOpt](https://github.com/robertmartin8/PyPortfolioOpt) for flexible portfolio construction and constraints.
- **Sector analysis**: Evaluate risk and return contribution by sector to improve diversification and identify trends.

### Explore Alternative Strategies

- **Different forecasting techniques**: Compare with models such as GARCH (for volatility), or machine learning models like LSTM for non-linear dynamics.
- **Ensemble modeling**: Combine ARIMA, GARCH, and ML predictions for more robust forecasts.
- **Rebalancing**: Simulate periodic rebalancing (monthly, quarterly) to reflect real-world strategies and assess impact on performance stability.

---

## 📁 Repository Structure

