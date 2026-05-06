# Neural Network-Based Stock Return Forecasting with Simulated Backtesting

**CSCI 357 - AI and Neural Networks | Spring 2026 | Bucknell University**  
**Author:** Sophie Yang

## Overview

This project builds a stock return forecasting system using LSTM and Transformer neural networks applied to four assets from different industries. Model predictions are translated into trading signals and evaluated through a simulated backtesting framework that compares strategy performance against buy & hold.

## Assets

| Ticker | Company | Industry |
|--------|---------|----------|
| TSLA | Tesla | Technology / Electric Vehicles |
| JPM | JPMorgan Chase | Financial |
| XOM | Exxon Mobil | Energy |
| SPY | S&P 500 ETF | Market Benchmark |

## Architecture

Two neural network architectures are implemented and compared:

**LSTM (Long Short-Term Memory)** reads the input sequence day by day, using forget, input, and output gates to selectively remember information across time. It takes a 20-day window of 16 features as input and outputs next-day predicted returns for all four assets.

**Transformer** uses self-attention to look at all 20 days simultaneously and learn which days are most relevant to the prediction. It projects the input to a 64-dimensional space, applies 2 encoder layers with 4 attention heads, and passes the final timestep to a fully connected output layer.

Both models use hidden size 64, 2 layers, Adam optimizer, and MSE loss.

## Features

Each asset contributes 4 features per day, for a total of 16 input features:

- Daily return (pct_change of closing price)
- MA5 daily change (5-day moving average)
- MA20 daily change (20-day moving average)
- RSI (14-day Relative Strength Index)

## Results

| Model | Test MAE |
|-------|----------|
| Naive Baseline | 0.012311 |
| LSTM | 0.012670 |
| Transformer | 0.013530 |

LSTM backtesting outperformed buy & hold on TSLA (1.142x vs 1.090x) by avoiding a mid-period drawdown. The Transformer's predictions collapsed to near-constant negative values, resulting in a flat strategy curve.

## Installation

```bash
pip install -r requirements.txt
```

## How to Run

Open `project.ipynb` in Jupyter and run all cells from top to bottom. Data is pulled automatically via `yfinance` — no manual download required.

## Video

[Video link](https://drive.google.com/file/d/1mP5-fOVHV4QuF497llK2XzYH5R7FxfQk/view?usp=sharing)