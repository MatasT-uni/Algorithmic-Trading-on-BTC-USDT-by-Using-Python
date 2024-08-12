---

# Algorithmic Trading on BTC/USDT

This project focuses on developing, backtesting, and evaluating algorithmic trading strategies for the BTC/USDT pair across various time intervals. The strategies implemented leverage technical indicators such as SMA (Simple Moving Average), MACD (Moving Average Convergence Divergence), Fibonacci retracement, and the Stochastic Oscillator, enhanced with Cooperative Multi-Agent Reinforcement Learning (CMARL). The project aims to identify the most effective trading strategies based on performance metrics across different time intervals.

## Table of Contents

- [Project Overview](#project-overview)
- [Data Preprocessing](#data-preprocessing)
- [Trading Strategies](#trading-strategies)
- [Methodology](#methodology)
- [Performance Analysis](#performance-analysis)
- [Notebooks Overview](#notebooks-overview)
- [How to Run the Project](#how-to-run-the-project)
- [Dependencies](#dependencies)
- [Results Summary](#results-summary)
- [License](#license)
- [Contributors](#contributors)
- [References](#references)

## Project Overview

The project is structured to explore algorithmic trading using a variety of time intervals to determine which provides the best risk-adjusted returns. The strategies are evaluated based on their effectiveness in maximizing returns while minimizing risk, using a combination of classical technical indicators and advanced machine learning techniques.

## Data Preprocessing

### Data Collection
- **Live Data**: The Binance API is used to fetch real-time BTC/USDT price data, ensuring that the trading strategies can adapt to current market conditions.
- **Historical Data**: The Binance API is also used to gather historical data for the BTC/USDT trading pair, which includes timestamps, open, high, low, close prices, and volume. This data is collected across various intervals (1 minute, 1 hour, 4 hours, 1 day).

### Data Cleaning and Preparation
- **Timestamp Conversion**: Converts timestamps from milliseconds to a human-readable datetime format.
- **Data Filtering**: Retains only essential columns such as open, high, low, close, and volume, and ensures that they are in the correct data type.
- **Return Calculation**: Calculates the percentage change in closing prices to derive returns for each interval.
- **Live Data Integration**: Continuously updates the historical dataset with the latest live prices, recalculating returns as new data comes in.

## Trading Strategies

The project implements several key technical indicators to inform trading decisions:

- **SMA50 and SMA200**: These simple moving averages are used to identify medium-term and long-term trends. Crossovers between these averages are used to generate buy or sell signals.
- **MACD**: This momentum indicator helps to identify changes in the strength, direction, momentum, and duration of a trend in a stock's price.
- **Fibonacci Retracement**: Used to identify potential reversal levels by highlighting key support and resistance levels.
- **Stochastic Oscillator**: Identifies overbought or oversold conditions in the market, which can signal a potential reversal.

## Methodology

### Indicator Calculation
- An `IndicatorCalculationAgent` class was developed to compute technical indicators such as SMA, MACD, Stochastic Oscillator, and Fibonacci retracement levels.

### Prediction Model
- A `PredictionAgent` class was created to handle training and predictions using machine learning models like RandomForestClassifier. The model is trained on the calculated indicators to predict price movements.

### Trading Execution
- The `TradingAgent` class simulates trade execution based on the predictions. It manages funds in USDT and BTC, executing buy or sell trades depending on the model's signals.

### Performance Monitoring
- A `MonitoringAgent` class evaluates the strategy’s performance by tracking metrics such as profit/loss, Sharpe ratio, and drawdown.

## Performance Analysis

The project includes both backtesting and real-time simulation:

### Backtesting
- Each trading strategy is tested across different time intervals using historical data. Performance is evaluated based on metrics like final portfolio value, total return, Sharpe ratio, and maximum drawdown.

### Real-Time Trading Simulation
- The strategies are also tested in a real-time trading environment to validate their performance under live market conditions.

## Notebooks Overview

- **agent_1d.ipynb**: Implements and tests trading strategies on the 1-day interval data.
- **agent_1h.ipynb**: Implements and tests trading strategies on the 1-hour interval data.
- **agent_1m.ipynb**: Implements and tests trading strategies on the 1-minute interval data.
- **agent_4h.ipynb**: Implements and tests trading strategies on the 4-hour interval data.
- **agent_All_Intervals_1m,1h,4h,1d.ipynb**: Combines all intervals (1 minute, 1 hour, 4 hours, 1 day) to compare and analyze performance across different timeframes.

## How to Run the Project

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/MatasT-uni/Algorithmic-Trading-on-BTC-USDT-by-Using-Python
   ```

2. **Install Dependencies**:
   Ensure that you have the necessary Python libraries installed:
   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels scikit-learn pmdarima pandas_datareader yfinance
   ```

3. **Run the Notebooks**:
   Open each notebook (`.ipynb` files) in Jupyter Notebook or JupyterLab and execute the cells sequentially to perform data preprocessing, implement trading strategies, and run backtesting.

4. **Analyze the Results**:
   Review the output plots and performance metrics to evaluate the effectiveness of each trading strategy.

## Dependencies

The project requires the following Python packages:

- `pandas` for data manipulation
- `numpy` for numerical computations
- `matplotlib` and `seaborn` for data visualization
- `statsmodels` for statistical modeling and time series analysis
- `scikit-learn` for machine learning models
- `pmdarima` for advanced time series analysis
- `pandas_datareader` for retrieving data from various online sources
- `yfinance` for fetching financial data from Yahoo Finance

## Results Summary

- **1-Minute Interval**: Provided moderate returns with relatively low risk.
- **1-Hour Interval**: Achieved higher returns but with increased volatility.
- **4-Hour Interval**: Showed the best risk-adjusted returns with a positive Sharpe ratio.
- **1-Day Interval**: Provided extremely high returns but with significant risk and drawdowns.

## References

- Investopedia: Various articles on technical indicators and algorithmic trading.
- Coindesk and Binance Academy: Information on cryptocurrency trading bots and their implementation.
- Academic resources and online courses on algorithmic trading.

---
