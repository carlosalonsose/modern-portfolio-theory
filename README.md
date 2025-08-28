# Modern Portfolio Theory (MPT) – Advanced Portfolio Optimization

This repository contains an advanced Python implementation of **Modern Portfolio Theory (MPT)**, pioneered by Harry Markowitz in 1952.  
The project demonstrates how to construct and analyze **optimal portfolios** by balancing risk and return, simulating thousands of random portfolios, and comparing the results against the **S&P 500 benchmark**.

---

## Project Overview

Modern Portfolio Theory is a foundational framework in finance that shows how diversification can optimize investment portfolios.  
By allocating weights across multiple assets, investors can achieve the **maximum possible return for a given level of risk**, or equivalently, **minimize risk for a given return**.

This project:
- Downloads and processes historical data for selected assets (NVDA, AAPL, GOOGL, MSFT, AMZN, META, TSLA).  
- Constructs portfolios and computes **expected returns**, **variance**, and **Sharpe ratios**.  
- Simulates thousands of random portfolios to approximate the **efficient frontier**.  
- Identifies the **tangency portfolio** (maximum Sharpe ratio) and the **minimum variance portfolio**.  
- Backtests the optimized portfolio against the **S&P 500 index**.  
- Visualizes both the **theoretical results** (efficient frontier, CAL) and **practical results** (portfolio vs benchmark).  

---

## Mathematical Foundations

- **Expected Portfolio Return**:

$$
\mathbb{E}[R_p] = \sum_{i=1}^n w_i \mathbb{E}[R_i]
$$

- **Portfolio Variance**:

$$
\sigma_p^2 = w^T \Sigma w
$$

- **Sharpe Ratio**:

$$
S = \frac{\mathbb{E}[R_p] - R_f}{\sigma_p}
$$

- **Capital Allocation Line (CAL):**

$$
\mathbb{E}[R_C] = R_f + \sigma_C \cdot \frac{\mathbb{E}[R_P] - R_f}{\sigma_P}
$$

where:
- $w$ = vector of portfolio weights  
- $\mu$ = vector of expected returns  
- $\Sigma$ = covariance matrix of returns  
- $R_f$ = risk-free rate  

---

## Implementation Steps

1. **Data Collection**  
   - Historical price data downloaded via `yfinance`.  
   - Assets: NVDA, AAPL, GOOGL, MSFT, AMZN, META, TSLA.  
   - Benchmark: S&P 500 (`^GSPC`).  

2. **Data Processing**  
   - Calculation of **daily returns**.  
   - Estimation of **mean returns** and **covariance matrix**.  

3. **Portfolio Simulation**  
   - Generated **25,000 random portfolios**.  
   - Computed expected return, volatility, and Sharpe ratio for each.  

4. **Optimization**  
   - Identified the **Maximum Sharpe Ratio Portfolio** (tangency portfolio).  
   - Identified the **Minimum Volatility Portfolio**.  

5. **Visualization**  
   - Efficient Frontier with random portfolios.  
   - Capital Market Line (CML).  
   - Highlighted optimal portfolios.  
   - Portfolio vs. S&P 500 wealth evolution.  

---

## Results

- **Efficient Frontier** clearly shows the set of optimal portfolios.  
- The **tangency portfolio** maximizes risk-adjusted return.  
- The **minimum volatility portfolio** provides lowest risk exposure.  
- Backtest vs **S&P 500** shows that the optimized portfolio outperformed the benchmark significantly, though with **higher volatility** due to concentration in high-growth assets (NVDA, BTC-USD).  

---

## Limitations

- **Normality Assumption:** Returns are assumed normally distributed, but markets exhibit fat tails and skewness.  
- **Static Correlations:** Historical correlations may break down in crises, reducing diversification.  
- **Estimation Error Sensitivity:** Small errors in expected returns or covariances can lead to unstable allocations.  
- **Transaction Costs:** Model ignores fees, taxes, and liquidity constraints.  
- **One-Period Model:** Ignores dynamic rebalancing and multi-period optimization.  

---

## Next Steps

- Add **volatility tying and correlation analysis** for dynamic risk management.  
- Turn this notebook into an **interactive Streamlit app**, where users can:  
  - Select assets dynamically.  
  - Adjust risk-free rate and number of portfolios.  
  - Visualize efficient frontier and optimal portfolios in real-time.  
