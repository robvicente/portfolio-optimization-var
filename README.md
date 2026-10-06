# Portfolio Optimization and Risk Analysis (US Equities)

Python project that builds a diversified portfolio of US-listed stocks using a top-down approach, optimizes it by maximizing the Sharpe ratio, and evaluates its risk with Value at Risk (VaR), backtesting and stress testing.

Developed as the final project for Modules 2 and 3 of the PEFA 2024 program.

## Project overview

1. **Portfolio construction:** 13 stocks selected across five sectors (Technology, Banks, Energy, Consumer Goods and Others), following a top-down strategy (region, country, sector).
2. **Optimization:** maximum Sharpe ratio portfolio with no short selling and a cap on the weight of each position.
3. **Benchmark comparison:** cumulative return of the optimized portfolio versus the S&P 500.
4. **Risk management:** VaR calculated with three methods, plus marginal, component and incremental VaR.
5. **Backtesting and stress testing** on a USD 1,000,000 portfolio.

## Data

- **Source:** Yahoo Finance, downloaded with `yfinance`.
- **Assets:** AAPL, AMZN, MSFT, JPM, GS, XOM, CVX, WMT, KO, PG, HAS, JCI, AZN.
- **Benchmark:** S&P 500 (`^GSPC`).
- **Period:** 2019-09-25 to 2024-09-25 for the optimization section; 2019-09-25 to 2023-09-25 for the risk sections.
- **Returns:** daily log returns, annualized with 252 trading days.

## Methodology

| Step | Technique |
|------|-----------|
| Optimization | Maximize Sharpe ratio with SciPy (`SLSQP`), weights between 0 and the cap, fully invested |
| VaR | Parametric (normal), historical simulation and Monte Carlo simulation, at 95% confidence |
| Risk decomposition | Marginal VaR, component VaR and incremental VaR |
| Backtesting | Count of days where the portfolio loss exceeds the estimated VaR |
| Stress testing | Portfolio VaR under 10%, 20% and 30% stress levels |

## Key results (optimized portfolio)

| Metric | Value |
|--------|-------|
| Expected annual return | 20.83% |
| Annual volatility | 20.55% |
| Sharpe ratio | 0.965 |

The script also produces charts for cumulative return vs. the S&P 500, VaR composition, component and incremental VaR, backtesting and stress testing.

## How to run

```bash
git clone https://github.com/robvicente/REPOSITORY-NAME.git
cd REPOSITORY-NAME
pip install -r requirements.txt
python portfolio_analysis.py
```

An internet connection is required to download the data from Yahoo Finance.

## Limitations

- The optimization is **in-sample**: weights are estimated with the same historical data used to evaluate them, so past performance does not guarantee future results.
- The weight cap is applied per asset, not per sector.
- The risk-free rate is fixed at 1%.
- The risk analysis in section 3 uses a fixed set of portfolio weights and a simplified stress test.
- Historical data, normal-distribution assumptions and the choice of period all affect the VaR estimates.

## Tools

Python, pandas, NumPy, SciPy, Matplotlib, yfinance.

## Author

Robinson Vicente
[LinkedIn](https://www.linkedin.com/in/robinson-vicente)
