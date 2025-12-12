# 📈 AlgoTrade: Quantitative Stock Price Prediction Pipeline

## 🚀 Executive Summary
In the high-frequency domain of algorithmic trading, static statistical models often fail to capture real-time market volatility. This project involves building a scalable **Data Science Pipeline** to ingest, analyze, and predict short-term price movements for major tech equities (**AAPL, MSFT, GOOGL, AMZN, TSLA**).

The study rigorously compares a traditional **ARIMA** (statistical) baseline against a **Gradient Boosting (XGBoost)** machine learning model. The results demonstrate that incorporating non-linear features (volatility, momentum) significantly outperforms linear forecasting methods.

---

## 🔑 Key Results
| Metric | ARIMA (Baseline) | XGBoost (Proposed) | Improvement |
| :--- | :--- | :--- | :--- |
| **RMSE** | 30.95 | **11.13** | **+64.0%** |
| **MAPE** | 16.00% | **4.54%** | **+71.6%** |

> **Business Insight:** The XGBoost model successfully reduced the forecasting error to ~4.5%, making it a viable candidate for generating short-term **Day Trading** or **Swing Trading** signals, whereas ARIMA proved too slow to react to recent price action.

---

## 🛠️ Tech Stack & Methodology
* **Language:** Python 3.10+
* **Data Ingestion:** Yahoo Finance API (`yfinance`)
* **Processing:** Pandas, NumPy, **Dask** (demonstrated for large-scale data handling)
* **Modeling:** `statsmodels` (ARIMA), `xgboost` (Gradient Boosting), `scikit-learn`
* **Visualization:** Matplotlib, Seaborn

### **Pipeline Architecture**
1.  **Data Ingestion:** Automated extraction of daily OHLCV data (2020–2023).
2.  **Robust Cleaning:** Implementation of Forward/Backward filling strategies and data integrity checks (simulated `pytest`).
3.  **Feature Engineering:**
    * **Lags:** ($t-1, t-5, t-21$) to capture market memory.
    * **Rolling Statistics:** 7-day & 21-day Moving Averages + Rolling Volatility (Standard Deviation).
    * **Momentum:** Daily Log Returns.
4.  **Model Evaluation:** Time-series split (80/20) validation using RMSE, MAE, and MAPE.

---

## 📊 Exploratory Analysis (EDA)
* **Volatility Clustering:** Identified **Tesla (TSLA)** as the highest-risk asset with "fat tail" return distributions, necessitating dynamic position sizing.
* **Sector Correlation:** High correlation (>0.7) observed between **MSFT** and **GOOGL**, suggesting common macroeconomic drivers.

<img width="986" height="451" alt="plot_forecast" src="https://github.com/user-attachments/assets/5e514295-d77d-4d0d-97c9-55119aba98b5" />
*(Figure: XGBoost [Green] tightly tracks Actual Price [Black], while ARIMA [Red] fails to capture volatility.)*

---

## 🔮 Future Improvements (Roadmap)
* **Production Deployment:** Integrate the pipeline with **AWS S3** for automated daily data storage.
* **Signal Visualization:** Export model predictions to **Tableau/PowerBI** for Portfolio Manager review.
* **Sentiment Analysis:** Enhance feature set with NLP-driven sentiment scores from financial news APIs to capture earnings-related shocks.

---

## 📜 License
This project is open-source and available under the MIT License.
