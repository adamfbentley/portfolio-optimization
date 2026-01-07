# Portfolio Optimization

Mean-variance (Markowitz) portfolio optimization with risk parity allocation and efficient frontier visualization.

## Features

- **Markowitz Optimization**: Maximum Sharpe ratio and minimum variance portfolios
- **Efficient Frontier**: Compute and visualize optimal risk-return tradeoffs
- **Risk Parity**: Equal risk contribution allocation with comparison to other strategies
- **Backtesting**: Historical performance testing with rebalancing support
- **Real Data**: Fetch market data via yfinance

## Installation

```bash
pip install -r requirements.txt
```

## Quick Start

```python
from markowitz import optimize_sharpe
from efficient_frontier import plot_efficient_frontier
import numpy as np

# Expected returns and covariance matrix
mean_returns = np.array([0.12, 0.10, 0.08, 0.14])
cov_matrix = ...  # Your covariance matrix

# Find optimal portfolio
optimal = optimize_sharpe(mean_returns, cov_matrix, risk_free_rate=0.02)
print(f"Sharpe Ratio: {optimal['sharpe']:.2f}")
print(f"Weights: {optimal['weights']}")

# Visualize efficient frontier
plot_efficient_frontier(mean_returns, cov_matrix)
```

## Modules

| Module | Description |
|--------|-------------|
| `data_loader.py` | Fetch historical prices via yfinance |
| `markowitz.py` | Mean-variance optimization (max Sharpe, min variance) |
| `efficient_frontier.py` | Efficient frontier computation and plotting |
| `risk_parity.py` | Risk parity allocation with strategy comparison |
| `backtesting.py` | Historical backtesting with performance metrics |

## Allocation Strategies Compared

| Strategy | Description |
|----------|-------------|
| Equal Weight | 1/n allocation |
| Inverse Volatility | Weight inversely proportional to volatility |
| Risk Parity | Equal risk contribution from each asset |
| Min Variance | Minimize portfolio variance |
| Max Sharpe | Maximize risk-adjusted returns |

## Performance Metrics

- **Sharpe Ratio**: Risk-adjusted return
- **Sortino Ratio**: Downside risk-adjusted return
- **Maximum Drawdown**: Largest peak-to-trough decline
- **Calmar Ratio**: Return / Max Drawdown

## Mathematical Background

### Mean-Variance Optimization
Maximize: $\frac{E[R_p] - R_f}{\sigma_p}$

Subject to: $\sum w_i = 1$

### Risk Parity
Find weights such that: $RC_i = RC_j \quad \forall i,j$

Where risk contribution: $RC_i = w_i \cdot \frac{\partial \sigma_p}{\partial w_i}$

## Example Output

```
Strategy Comparison (2018-2023 Backtest)
----------------------------------------
Strategy        Return    Vol      Sharpe   Max DD
Equal Weight     7.2%    12.1%     0.43    -23.4%
Risk Parity      5.8%     8.2%     0.46    -15.1%
Max Sharpe       8.1%    14.3%     0.43    -28.2%
Min Variance     4.9%     7.1%     0.41    -12.8%
```

## Requirements

- Python 3.8+
- NumPy, Pandas, SciPy
- Matplotlib
- yfinance

## License

MIT
