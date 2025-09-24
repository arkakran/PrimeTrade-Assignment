# Bitcoin Trader Performance vs Market Sentiment Analysis

A comprehensive Python-based analysis tool that examines the relationship between Bitcoin trader performance and market sentiment using the Fear & Greed Index. This project provides insights into how market psychology affects trading outcomes and generates actionable trading strategies.

## 🎯 Project Overview

This analysis combines historical Bitcoin trading data with market sentiment indicators to:
- Identify correlations between market sentiment and trading performance
- Analyze trader behavior across different sentiment regimes
- Generate data-driven trading signals and strategies
- Provide risk management insights based on sentiment patterns

## 📊 Key Features

### Core Analytics
- **Trader Performance Metrics**: Comprehensive analysis of individual trader performance including PnL, win rates, Sharpe ratios, and volatility metrics
- **Sentiment-Performance Correlation**: Statistical analysis of how Fear & Greed Index values correlate with trading outcomes
- **Time Series Analysis**: Daily performance trends and their relationship with market sentiment
- **Risk Analysis**: Value-at-Risk (VaR) calculations and risk metrics across sentiment levels

### Advanced Insights
- **Seasonal Pattern Analysis**: Monthly and weekly performance patterns
- **Trading Signal Generation**: Automated signal creation based on sentiment moving averages
- **Top Performer Identification**: Traders who excel in different market conditions
- **Volatility vs Performance Analysis**: Risk-return optimization insights

### Visualizations
- Sentiment distribution histograms
- Performance by sentiment category bar charts
- Time series plots of sentiment vs daily PnL
- Correlation heatmaps
- Scatter plots for individual trade analysis
- Volume analysis by sentiment category

## 🛠️ Installation & Setup

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn datetime warnings
```


### Data Files Required
1. **`historical_data.csv`** - Bitcoin trading data with columns:
   - `Timestamp IST`: Trading timestamp
   - `Account`: Trader identifier
   - `Closed PnL`: Profit/Loss for each trade
   - `Size USD`: Trade size in USD

2. **`fear_greed_index.csv`** - Market sentiment data with columns:
   - `date`: Date of sentiment reading
   - `value`: Fear & Greed Index value (0-100)
   - `classification`: Sentiment category

## 🚀 Usage

### Basic Execution
```python
# Run the complete analysis
python bitcoin_sentiment_analysis.py
```

### Custom Analysis
```python
# Import and run specific components
from bitcoin_sentiment_analysis import *

# Process data
merged_data, historical_data_clean, fear_greed_data_clean = preprocess_data()

# Calculate trader metrics
trader_metrics = calculate_trader_metrics(merged_data)

# Analyze sentiment vs performance
sentiment_analysis, merged_data = sentiment_performance_analysis(merged_data)
```

## 📈 Output Files

The analysis generates several CSV files:
- `trader_performance_metrics.csv`: Individual trader statistics
- `daily_sentiment_performance.csv`: Daily aggregated performance data
- `sentiment_analysis_results.csv`: Performance breakdown by sentiment category
- `monthly_patterns.csv`: Monthly performance patterns
- `weekly_patterns.csv`: Weekly performance patterns

## 📊 Key Metrics Explained

### Sentiment Categories
- **Extreme Fear (0-24)**: Market oversold, potential buying opportunity
- **Fear (25-49)**: Cautious market, selective buying
- **Greed (50-74)**: Optimistic market, consider profit-taking
- **Extreme Greed (75-100)**: Market overbought, high risk period

### Performance Indicators
- **Total PnL**: Cumulative profit/loss per trader
- **Win Rate**: Percentage of profitable trades
- **Sharpe Ratio**: Risk-adjusted return metric
- **PnL Volatility**: Standard deviation of trade outcomes
- **Average Sentiment**: Mean Fear & Greed Index during trading period

## 🔍 Analysis Components

### 1. Data Preprocessing (`preprocess_data()`)
- Robust timestamp parsing with multiple format support
- Data cleaning and validation
- Dataset merging with date alignment

### 2. Trader Metrics (`calculate_trader_metrics()`)
- Performance aggregation by trader
- Win rate calculation
- Risk-adjusted return metrics

### 3. Sentiment Analysis (`sentiment_performance_analysis()`)
- Performance breakdown by sentiment category
- Statistical analysis of sentiment impact

### 4. Correlation Analysis (`correlation_analysis()`)
- Pearson correlation coefficients
- Sentiment vs performance relationships

### 5. Trading Signals (`generate_trading_signals()`)
- Moving average crossover signals
- Sentiment-based entry/exit points
- Signal performance backtesting

## 📋 Strategic Recommendations

### Sentiment-Based Trading Strategy
1. **Buy Signals**: Extreme fear levels (0-24) with declining sentiment MA
2. **Sell Signals**: Extreme greed levels (75-100) with rising sentiment MA
3. **Position Building**: Neutral periods (25-74) for gradual accumulation

### Risk Management
- Dynamic position sizing based on sentiment volatility
- Tighter stop-losses during extreme sentiment periods
- Portfolio diversification across sentiment regimes

### Performance Optimization
- Focus on consistently performing traders across all sentiment cycles
- Avoid FOMO trading during extreme greed
- Capitalize on fear-driven market inefficiencies

## 🔧 Customization Options

### Adjusting Sentiment Thresholds
```python
def categorize_sentiment(value):
    if value <= 20:  # Modify threshold
        return 'Extreme Fear'
    # ... adjust other thresholds
```

### Custom Signal Generation
```python
# Modify signal logic in generate_trading_signals()
daily_data.loc[(daily_data['Sentiment'] <= 20), 'Signal'] = 1  # Custom buy threshold
```

## 📊 Visualization Features

The analysis generates comprehensive visualizations including:
- Distribution plots for sentiment and performance metrics
- Time series charts showing sentiment and PnL correlation
- Heatmaps for correlation analysis
- Bar charts for categorical performance comparison
