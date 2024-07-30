# Forecasting with ARIMA, XGBoost, and LSTM: A Comprehensive Analysis

This project involves forecasting using three distinct methods: ARIMA (a statistical method), XGBoost (a machine learning technique), and LSTM (a deep learning approach). All methods utilize the input file 'TAB_Betting_Data,' which is notably clean, resulting in a straightforward Exploratory Data Analysis (EDA) phase.

## 1. ARIMA (Autoregressive Integrated Moving Average)

ARIMA is based on the assumption of stationarity in the time series and constant error variance. The model uses past signals of the series to make forecasts, including autoregression (AR) and moving average (MA) components. Most time series exhibit trends, necessitating differencing to achieve stationarity. The model is thus specified by three parameters ARIMA(p, d, q), where 'd' denotes the differencing order. In cases where seasonality is present, Seasonal ARIMA (SARIMA) models are employed.

### Model Specification:
- **Model**: ARIMA(0,0,0)(0,1,1)[7]
- **Auto-ARIMA Result**: ARIMA(0,0,0)(0,1,1)[7]

Despite multiple seasonal differencing attempts, the ARIMA model suffered from significant white noise, indicating high randomness in the data. Consequently, alternative methods such as XGBoost and LSTM were explored.

## 2. XGBoost (Extreme Gradient Boosting)

XGBoost is a robust machine learning method known for its efficiency and performance.

## 3. LSTM (Long Short-Term Memory)

LSTM is a type of recurrent neural network capable of capturing long-term dependencies and trends in time series data.


Although the RMSE for LSTM is higher compared to XGBoost, LSTM demonstrated superior adherence to seasonal patterns in the data. The higher RMSE can be attributed to two primary factors:
1. Limited training resources, resulting in underfitting due to insufficient epochs.
2. The presence of large outliers affecting gradient computation during backpropagation, causing unstable weight updates and hindering model convergence.

Given more training time and adequate resources, LSTM is likely to provide highly accurate forecasts, barring outlier detection challenges.

## Conclusion

This project highlights the comparative performance of ARIMA, XGBoost, and LSTM in forecasting. Despite the inherent challenges and varying results, each method offers unique strengths. While ARIMA struggled with high randomness, XGBoost and LSTM presented viable alternatives, with LSTM showing promise given proper training resources.

---

For any further information or questions, please refer to the individual code files:

1. ARIMA
2. GradientBoosting
3. LSTM
4. RFM

These files encompass the detailed implementation and results of the respective forecasting methods.
