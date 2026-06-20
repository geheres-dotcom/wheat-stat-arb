# Statistical Arbitrage on the Wheat Market

A multivariate statistical arbitrage study on the wheat market, built around cointegration
between US wheat futures and a basket of agricultural equities. The project implements two
complementary strategies: a market-neutral multi-asset portfolio optimized under constraints,
and an optimized one-versus-one pairs-trading strategy. The framework adapts Yang and Malik
(2024), originally developed for cryptocurrencies, to agricultural commodities.

## Data

The asset universe follows a three-tier structure: US wheat futures (CBOT) as the anchor,
two sector ETFs (WEAT, 3WHL), and a set of agricultural equities spanning the value chain
(producers of inputs, equipment manufacturers and grain traders, e.g. AGCO, CF Industries,
Mosaic, Archer-Daniels-Midland). Daily OHLCV data is retrieved through `yfinance` for the
2020–2025 period. Cleaning aligns all series on common trading days, forward-fills market
holidays, and removes data-feed artifacts using an interquartile-range rule with a factor of
three before a final forward fill.

## Methodology

Two assets are considered cointegrated when a linear combination of their log-prices is
stationary, the hedge ratio being estimated by ordinary least squares. Stationarity of the
resulting spread is tested with the Augmented Dickey-Fuller test. Each spread is standardized
into a Z-score; a position is opened when the Z-score moves beyond two standard deviations and
closed when it returns within half a standard deviation.

The first strategy selects the five assets most cointegrated with the futures anchor and, at
each entry signal, solves a quadratic optimization with Gurobi to build a market-neutral
portfolio (the beta-weighted sum of positions is constrained to zero), subject to long/short
weight bounds and a capital constraint. Transaction costs of ten basis points are applied to
every entry and exit.

The second strategy isolates the single most cointegrated pair (wheat futures against Mosaic),
estimates a static hedge ratio by OLS, and trades a rolling Z-score. It adds two risk filters:
a volatility-regime filter that suppresses entries when short-term volatility exceeds
long-term volatility by more than fifty percent, and an adaptive trailing stop that liquidates
a position after an adverse move of two standard deviations. The rolling lookback window is
chosen by grid search over macro-aligned horizons; a 150-day window proved markedly superior,
matching the slow harvest cycles of agricultural markets.

## Results

Backtested over 2020–2025, net of ten basis points of transaction costs:

| Metric | Market-neutral portfolio | Optimized pairs trading |
|---|---|---|
| CAGR | 12.3% | — |
| Max drawdown | 41.7% | 11.5% |
| Sharpe ratio | 0.26 | 1.14 |
| Calmar ratio | 0.30 | 1.46 |

The market-neutral portfolio improves on a buy-and-hold benchmark across all risk-adjusted
measures, mainly by reducing the maximum drawdown, which is consistent with its zero-beta
construction. The pairs-trading strategy is the stronger of the two; its performance is driven
in part by the Q1 2022 dislocation in wheat prices, which the long lookback identified as a
temporary divergence rather than a regime change.

## Running the project

The analysis is contained in a Jupyter notebook. Dependencies:

```
pip install pandas numpy matplotlib scipy statsmodels yfinance gurobipy
```

The optimization step requires a Gurobi installation and a valid license (a free academic
license is available). The notebook downloads the raw data through `yfinance`, writes a cleaned
CSV, and reloads it for the backtests; the cleaned dataset is also included so the analysis can
be reproduced without re-downloading.

## Repository contents

The notebook holds the full pipeline, from data retrieval and cleaning through cointegration
testing, signal generation, optimization and backtesting. The cleaned dataset accompanies it.
A written report documents the methodology, parameters and detailed results.

## Reference

Yang and Malik (2024), multivariate statistical arbitrage with constrained quadratic
optimization, adapted here from cryptocurrency markets to agricultural commodities.
