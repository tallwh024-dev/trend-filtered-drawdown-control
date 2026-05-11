# Trend-filtered-drawdown-control

## Overview

This project studies a defensive trading overlay that combines a moving-average trend filter with an equity-curve drawdown control rule. The goal is to reduce downside risk by lowering exposure during weak market regimes and after meaningful portfolio drawdowns.

The strategy is tested on SPY and QQQ using daily market data, with additional out-of-sample testing and walk-forward analysis to evaluate robustness.

## Research Question

Can a trend-filtered drawdown control strategy reduce maximum drawdown and improve downside risk-adjusted performance compared with a buy-and-hold benchmark?

## Strategy Design

The strategy combines two components:

1. **Trend Filter**  
   Uses moving-average lookback windows of 60, 120, and 240 trading days to classify the market as risk-on or risk-off.

2. **Drawdown Control Overlay**  
   Reduces exposure when the strategy equity curve reaches selected drawdown thresholds:
   - 10% drawdown: reduce to 50% exposure
   - 15% drawdown: reduce to 20% exposure
   - 20% drawdown: reduce to 0% exposure

## Data

- Assets: SPY and QQQ
- Frequency: Daily
- Source: Yahoo Finance via `yfinance`
- Main test period: 2010–2025
- Out-of-sample period: 2019–2025

## Methods

The project includes:

- Moving-average trend signal construction
- Equity-curve drawdown measurement
- Rule-based exposure control
- Parameter optimization using Calmar ratio
- Out-of-sample testing
- Walk-forward analysis
- Performance comparison against buy-and-hold benchmarks

## Key Results

In the out-of-sample test, the defensive strategy reduced maximum drawdown meaningfully:

| Asset | Strategy Max Drawdown | Buy & Hold Max Drawdown |
|---|---:|---:|
| SPY | -15.59% | -33.72% |
| QQQ | -20.54% | -35.12% |

The strategy sacrificed some upside return, but it improved downside protection and risk control, especially for SPY.

## Tools

- Python
- pandas
- NumPy
- yfinance
- matplotlib

## Files

- `notebooks/strategy_project.ipynb`: Main project notebook
- `report/Strategy_Project_CFRM522.pdf`: Full project report
- `figures/`: Equity curve and drawdown charts

## Author

Jackson Wang  
M.S. Computational Finance and Risk Management  
University of Washington
