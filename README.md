# Binance Cryptocurrency Trading Forecasting

This project aims to analyze and forecast daily trade count data from the Binance cryptocurrency exchange for the year 2022. Using time series techniques, such as Box-Cox transformation and ARIMA modeling, the project builds a forecasting model to predict future trading activity, with a specific focus on the performance for January 2023 ( This project in implemented in R).

## Table of Contents
- [Project Overview](#project-overview)
- [Data Exploration & Preprocessing](#data-exploration--preprocessing)
- [Modeling Approach](#modeling-approach)
- [Results & Evaluation](#results--evaluation)
- [Limitations & Future Improvements](#limitations--future-improvements)
- [Conclusion](#conclusion)
- [Getting Started](#getting-started)
- [License](#license)

## Project Overview
Cryptocurrency trading on Binance has surged in recent years, and understanding its patterns is crucial for traders and platform operators. This project analyzes daily trade counts on Binance throughout 2022 to identify patterns and predict future trading activity. The volatility of the cryptocurrency market presents a challenge, but applying rigorous time series techniques helps uncover valuable insights.

## Data Exploration & Preprocessing
The dataset includes daily trade counts for 2022, with training data from January to December 2022 and testing data from January 2023.

Key data challenges included:
- Non-stationarity in the time series
- Skewed distribution
- Seasonal patterns (weekly fluctuations)
- Extreme outliers

### Data Transformation
- **Box-Cox Transformation**: Stabilized variance to normalize data.
- **Differencing**: Ensured stationarity using first differencing.
- **Augmented Dickey-Fuller Test**: Confirmed stationarity of the differenced series.

## Modeling Approach
### Model Selection Strategy
Multiple ARIMA models were tested with different specifications:
1. **Basic ARIMA(p,0,q)**: On the differenced, transformed data.
2. **ARIMAX**: ARIMA with outlier dummies as external regressors.
3. **SARIMA**: ARIMA with seasonal components to capture weekly seasonality.
4. **SARIMAX**: ARIMA with seasonal components and outlier treatment.

The model evaluation used:
- **AIC** and **BIC**: For model fit and complexity.
- **Shapiro-Wilk Test**: For normality of residuals.
- **Ljung-Box Test**: For autocorrelation in residuals.

### Best Model
The best model was a **SARIMA(2,0,4)(1,0,1)** with outlier dummies. This model effectively captured time-dependent patterns and handled outliers well.

## Results & Evaluation
### Residual Diagnostics
- **Residual Time Plot**: Showed no obvious patterns, confirming good model fit.
- **ACF and PACF of Residuals**: No significant spikes, indicating proper temporal dependencies capture.
- **Q-Q Plot**: Residuals followed the diagonal, confirming successful Box-Cox transformation.
- **Histogram**: Residuals followed a normal distribution.

The final model demonstrated a **MAPE of 12%** on the test data, indicating good predictive accuracy.

### Limitations
- **Market Shocks**: The model cannot predict sudden market shifts caused by external factors.
- **Missing External Variables**: Price data, market sentiment, and trading volumes from other exchanges were not included, which could improve accuracy.
- **Outlier Focus**: Excessive focus on outliers may lead to overfitting.

## Future Improvements
- **Incorporating External Factors**: Including data such as Bitcoin/Ethereum price volatility, market sentiment, and trading volumes from other exchanges.
- **Advanced Modeling**: Exploring machine learning models (Random Forest, Gradient Boosting) and deep learning (LSTMs) for improved forecasting.
- **Forecast Combination**: Combining forecasts from multiple models for more robust predictions.

## Conclusion
This project demonstrates that time series analysis can uncover patterns in the volatile cryptocurrency market, helping to forecast trading activity. While the model provides useful predictions, it cannot account for unpredictable market shifts. Future work could improve forecast accuracy by including additional variables and employing advanced modeling techniques.

## Getting Started
To run this project locally, follow these steps:

1. Clone the repository.
2. Install required dependencies.
3. Run the model.


