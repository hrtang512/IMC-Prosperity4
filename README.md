IMC Prosperity 4 — Algorithmic Trading Research

Algorithmic trading research for IMC Prosperity 4, including custom backtesting, options pricing, volatility analysis, order-book strategies, execution diagnostics, and systematic strategy development in Python.

The project follows an end-to-end quantitative research workflow:

Market analysis → hypothesis formation → feature engineering → strategy implementation → backtesting → diagnostics → robustness testing

Project Overview

The IMC Prosperity challenge provides a simulated multi-asset exchange with limit-order-book data, executed trades, position limits, and changing market conditions.

The objective is to develop systematic trading strategies that generate profit while managing:

* Inventory risk
* Execution quality
* Cross-asset exposure
* Adverse selection
* Model and regime uncertainty

Research Infrastructure

<details>
<summary><strong>Custom Backtesting Framework</strong></summary>

Built a Python-based backtesting framework to reconstruct the simulated exchange environment and evaluate strategies using historical market data.

The framework supports:

* Limit-order-book replay
* Position and inventory tracking
* Order execution simulation
* Realized and mark-to-market PnL
* Position-limit enforcement
* Multi-product strategy testing
* Parameter grid search
* Strategy comparison against baseline models

The local backtester was calibrated against official simulation outputs and achieved less than 5% PnL deviation in tested scenarios.

</details>
<details>
<summary><strong>Post-Run Diagnostics</strong></summary>

Developed analysis tools to evaluate:

* Cumulative and product-level PnL
* Drawdowns and recovery periods
* Position and inventory trajectories
* Bid-ask spread capture
* Fill rates and execution quality
* Signal strength and trade timing
* Hedge effectiveness
* Performance across market regimes

These tools helped distinguish whether losses came from weak signals, execution, hedging, or inventory exposure.

</details>

Trading Strategies

<details>
<summary><strong>Market Making</strong></summary>

Implemented inventory-aware market-making strategies using:

* Best bid and ask prices
* Order-book depth
* Fair-value estimates
* Dynamic spreads
* Position-dependent quote adjustments
* Adverse-selection controls
* Position limits and risk constraints

</details>
<details>
<summary><strong>Mean Reversion</strong></summary>

Developed mean-reversion strategies based on deviations between market prices and estimated fair values.

Signals included:

* Absolute price thresholds
* Rolling means and standard deviations
* Z-scores
* Entry and exit rules
* Position-aware sizing
* Regime-dependent parameters

</details>
<details>
<summary><strong>Basket and Relative-Value Trading</strong></summary>

Modeled relationships between composite products and their underlying components to identify temporary pricing dislocations.

The strategy included:

* Synthetic basket valuation
* Spread construction
* Hedge-ratio estimation
* Relative-value signals
* Multi-asset execution
* Residual exposure monitoring

</details>
<details>
<summary><strong>Options and Volatility Trading</strong></summary>

Implemented Black–Scholes-based options research, including:

* Theoretical option valuation
* Implied volatility estimation
* Delta and vega analysis
* Volatility smile and skew evaluation
* Mispricing detection
* Delta hedging
* Implied-versus-realized volatility comparison
* IV-based scalping strategies

</details>
<details>
<summary><strong>Trade-Flow and Counterparty Analysis</strong></summary>

Analyzed trade and counterparty data to study potentially informative order-flow patterns.

Research included:

* Directional flow imbalance
* Counterparty-specific behavior
* Repeated execution patterns
* Short-term price response after trades
* Signal stability across time periods

</details>

Personal Research Lessons

1. Do not overfit the backtest or online test

A high historical PnL does not necessarily imply a robust strategy.

Strong performance may come from:

* Directional bias in the historical sample
* A favorable but temporary market regime
* Parameter tuning to a small number of test cases
* Leakage from repeatedly evaluating on the same data
* Unrealistic assumptions about execution and liquidity

A strategy that performs well in one dataset may fail when the market undergoes a regime switch. For this reason, I learned to evaluate strategies using:

* Multiple historical periods
* Rolling-window analysis
* Out-of-sample testing
* Parameter sensitivity checks
* Stress tests under different directional and volatility regimes
* Performance attribution by signal, execution, and inventory exposure

The goal is not to maximize backtest PnL, but to identify whether the strategy has a stable and economically interpretable edge.

2. Start with the simplest viable strategy

Complexity does not automatically create edge.

Some of the strongest strategies began with very simple rules. For example, an absolute-threshold mean-reversion strategy may be sufficient:

Buy when price falls below threshold (A), and sell when price rises above threshold (B).

A simple strategy can perform surprisingly well when the underlying market mechanism is stable.

Starting simple makes it easier to:

* Understand why the strategy works
* Diagnose losses
* Measure the marginal value of each added feature
* Avoid unnecessary parameter tuning
* Detect when complexity is only fitting noise

The challenge should not be overinterpreted. A transparent strategy with a clear economic rationale may outperform a complicated model that is difficult to validate.

Quantitative Research Methods

This project applies concepts from:

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

Research Workflow

1. Inspect market, trade, and order-book data.
2. Form an economic or statistical hypothesis.
3. Begin with a simple interpretable baseline.
4. Construct predictive features and trading signals.
5. Implement the strategy under position and execution constraints.
6. Backtest across multiple datasets and regimes.
7. Analyze PnL, drawdowns, inventory, and execution.
8. Tune parameters without repeatedly fitting the same test sample.
9. Stress-test performance under regime changes.
10. Compare results against simple baseline strategies.

Key Takeaways

* Historical PnL can be driven by directional bias rather than true predictive edge.
* Regime shifts can invalidate relationships that appear stable in a single backtest.
* Simple strategies should be tested before introducing additional model complexity.
* A profitable signal is not sufficient without realistic execution and inventory management.
* Robustness across periods and parameter choices matters more than peak backtest performance.
* Detailed diagnostics often improve a strategy more than adding another layer of complexity.

Disclaimer

This repository is intended for educational and research purposes. It contains work developed for the IMC Prosperity simulation and does not represent investment advice or a production trading system. Competition data, rules, and proprietary materials remain subject to their respective terms of use.
