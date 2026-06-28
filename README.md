IMC Prosperity 4 — Algorithmic Trading Research

This repository contains my algorithmic trading research and strategy development for IMC Prosperity 4. The project focuses on systematic signal generation, market-making, options pricing, volatility modeling, portfolio hedging, and order-book-based execution using Python.

The research workflow follows an end-to-end quantitative process:

Market data analysis → hypothesis formation → feature engineering → strategy implementation → backtesting → diagnostics → parameter tuning → robustness evaluation

Project Overview

The IMC Prosperity challenge provides a simulated multi-asset exchange with limit-order-book data, executed trades, position limits, and evolving market conditions. The objective is to design automated trading strategies that generate risk-adjusted profit while managing inventory, execution risk, and cross-asset exposure.

This repository includes tools and strategies developed to study:

* Market microstructure and order-book dynamics
* Relative-value and mean-reversion signals
* Basket and component mispricing
* Options pricing and implied volatility
* Delta hedging and inventory management
* Counterparty and trade-flow behavior
* Execution quality and transaction-level PnL
* Strategy stability across market regimes

Research Infrastructure

Custom Backtesting

Built a Python-based backtesting framework to reconstruct the simulated exchange environment and evaluate strategies using historical market data.

The framework supports:

* Limit-order-book replay
* Position and inventory tracking
* Order execution simulation
* Mark-to-market and realized PnL calculation
* Position-limit enforcement
* Multi-product strategy testing
* Parameter grid search
* Strategy comparison against baseline models

The local backtester was calibrated against official simulation results to reproduce trading behavior and PnL with less than 5% deviation in tested scenarios.

Research Diagnostics

Developed post-run analysis tools to evaluate:

* Cumulative and product-level PnL
* Drawdowns and recovery periods
* Position and inventory trajectories
* Bid-ask spread capture
* Fill rates and execution quality
* Signal strength and trade timing
* Hedge effectiveness
* Exposure by product
* Performance across different market regimes

These diagnostics improved the speed of strategy iteration by making it easier to identify whether losses came from signal quality, execution, hedging, or inventory risk.

Trading Strategies

Market Making

Implemented inventory-aware market-making strategies using:

* Best bid and ask prices
* Order-book depth
* Fair-value estimates
* Dynamic bid-ask spreads
* Position-dependent quote adjustments
* Adverse-selection controls
* Position limits and risk constraints

Mean Reversion

Developed statistical mean-reversion strategies based on deviations between market prices and estimated fair values.

Signals were evaluated using:

* Rolling means and standard deviations
* Z-scores
* Entry and exit thresholds
* Signal persistence
* Position-aware sizing
* Regime-dependent parameters

Basket and Relative-Value Trading

Modeled relationships between composite products and their underlying components to identify temporary pricing dislocations.

The strategy included:

* Synthetic basket valuation
* Spread construction
* Hedge-ratio estimation
* Relative-value signals
* Multi-asset execution
* Residual exposure monitoring

Options and Volatility Trading

Implemented Black–Scholes-based options research, including:

* Theoretical option valuation
* Implied volatility estimation
* Delta and vega analysis
* Volatility smile and skew evaluation
* Mispricing detection
* Delta hedging
* Implied-versus-realized volatility comparison
* IV-based scalping signals

Trade-Flow and Counterparty Analysis

Analyzed trade and counterparty data to identify persistent behavioral patterns and potentially informative order flow.

Research included:

* Directional trade-flow imbalance
* Counterparty-specific behavior
* Repeated execution patterns
* Short-term price response following trades
* Signal stability across time periods

Quantitative Research Methods

The project applies concepts from:

* Probability and statistics
* Time-series analysis
* Statistical arbitrage
* Market microstructure
* Options pricing
* Volatility modeling
* Feature engineering
* Backtesting
* Parameter optimization
* Risk management
* Robustness and sensitivity analysis

Technology Stack

* Python
* NumPy
* pandas
* Matplotlib
* SciPy
* scikit-learn
* Git

Example Research Workflow

1. Inspect market and order-book data.
2. Form an economic or statistical hypothesis.
3. Construct predictive features and trading signals.
4. Implement the strategy under position and execution constraints.
5. Backtest the strategy across multiple datasets.
6. Analyze PnL, drawdowns, inventory, and execution.
7. Tune parameters using structured grid search.
8. Stress-test performance across changing market conditions.
9. Compare results with simple baseline strategies.

Key Takeaways

* A profitable signal is not sufficient without realistic execution and inventory management.
* Backtest accuracy is critical when evaluating small differences between strategies.
* Options strategies require joint modeling of fair value, volatility, Greeks, and hedging costs.
* Relative-value signals are most effective when hedge ratios and residual risks are explicitly controlled.
* Strategy performance should be evaluated across multiple regimes rather than through aggregate PnL alone.
* Detailed post-trade diagnostics often contribute more to improvement than additional model complexity.

Disclaimer

This repository is intended for educational and research purposes. It contains work developed for the IMC Prosperity simulation and does not represent investment advice or a production trading system. Competition data, rules, and proprietary materials remain subject to their respective terms of use.
