# Forecasting Monthly Wholesale Chicken Breast Prices

An end-to-end time-series forecasting project developed during my internship at Tyson Foods to predict monthly wholesale chicken breast prices. By leveraging historical USDA data alongside macroeconomic and supply-side drivers, this project evaluates multiple statistical models to deliver an accurate 12-month forward-looking price forecast.

---

## Project Overview & Key Results
* **Goal:** Predict monthly wholesale chicken breast prices to assist in strategic procurement and market analysis.
* **Data Horizon:** 25 years of historical data (2001 – 2026).
* **Winning Model:** SARIMAX optimized with macroeconomic exogenous variables.
* **Performance:** Achieved an **84.19% accuracy rate** (15.81% MAPE) on the test set and demonstrated strong alignment when validated against actual March/April 2026 market prices.

---

## Repository Structure & Environment

The main analysis, data preparation, modeling, and validation are executed within the primary Python file:
* **`EMI Forecast.py`** — Main working file containing the end-to-end data pipeline.

### Core Libraries Used:
* **Data Manipulation:** `pandas`
* **Visualization:** `matplotlib`
* **Time Series & Statistical Modeling:** `statsmodels`, `pmdarima`
* **Machine Learning & Evaluation:** `scikit-learn`

---

## Data Sources & Drivers

The project integrates internal and public data across four primary CSV files containing historical USDA data (2001–2026):
1. **`EMI monthly prices.csv`** — Base wholesale pricing data for primary cuts (Chicken Breast, Leg Quarters, Wings).
2. **`slaughtered average pounds per head.csv`** — Supply-side weight metrics.
3. **`slaughter head counts.csv`** — Supply-side volume metrics.
4. **`slaughter total pounds.csv`** — Aggregate volume metrics.

### Focus Driver
While the initial exploratory analysis evaluated three main market drivers (**Chicken Breast**, **Leg Quarters**, and **Wings**), this repository focuses explicitly on forecasting **Chicken Breast** prices.

---

## The Analytics Workflow

### 1. Data Preprocessing & Exploratory Data Analysis (EDA)
* Handled missing values by identifying and removing `NA` rows to ensure statistical continuity.
* Generated monthly and quarterly plots to isolate seasonal spikes (e.g., summer grilling seasons vs. winter dips).
* Plotted long-term trend lines to visualize multi-year market cycles.

### 2. Statistical Diagnostics
* **Seasonal Decomposition:** Separated the time series into trend, seasonal, and residual components.
* **Autocorrelation Analysis:** Plotted Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) graphs to determine the optimal lag structures ($p$ and $q$ parameters).
* **Stationarity Testing:** Conducted an **Augmented Dickey-Fuller (ADF) test** to verify stationarity, ensuring the underlying statistical properties (mean and variance) remain constant over time for optimal model fitting.

### 3. Modeling Strategy (Train-Test Split)
The dataset was split chronologically using **80% for training** and **20% for testing** to evaluate out-of-sample performance. The following architectures were benchmarked:
* Triple Exponential Smoothing (Holt-Winters)
* ARIMA / SARIMA
* SARIMAX (incorporating external features: alternative chicken cuts, slaughter data, and macroeconomic factors)

---

## Model Performance Benchmark

Multiple iterations of the SARIMAX framework were built to isolate how different feature sets impacted accuracy. 

| Model Flavor / Features | MAPE (%) | MAE | RMSE |
| :--- | :---: | :---: | :---: |
| **SARIMAX (Economic Factors Only)** <br> *(US Coal, Soybeans, Heating Oil, Unemployment, Consumer Sentiment, CPI, Beef Prices)* | **15.81%** | **27.34** | **31.06** |
| **SARIMAX (Slaughter Data + Economic Factors)** | *[Insert]* | *[Insert]* | *[Insert]* |
| **SARIMAX (Slaughter Data Only)** | *[Insert]* | *[Insert]* | *[Insert]* |
| **SARIMAX (Cut Variations: Wings & Leg Quarters)** | *[Insert]* | *[Insert]* | *[Insert]* |
| **Triple Exponential Smoothing** | *[Insert]* | *[Insert]* | *[Insert]* |

*(Note: Feel free to fill in the placeholders above using the metrics from the visual benchmark below).*

![Model Performance Comparison Table](https://github.com/user-attachments/assets/2597baa2-7bb8-40af-92a8-29a71d144d46)

### The Winning Insight
The **SARIMAX model optimized with Federal Reserve macroeconomic indicators** significantly outperformed standard supply-side models. By tracking foundational input costs (soybean feed, heating oil, coal) alongside consumer health metrics (unemployment, CPI, consumer sentiment) and competing proteins (beef prices), the model successfully captured the broader economic pressures driving wholesale poultry valuation.

![Winning Model Snippet](https://github.com/user-attachments/assets/96955e8b-5424-4b2b-b63c-1ed1ce9d6b0b)

---

## 12-Month Future Forecast

Using the champion SARIMAX model, a forward-looking 12-month forecast was generated to project future pricing directions.

![12-Month Future Price Forecast](https://github.com/user-attachments/assets/29d4ad74-47c9-4e3a-801b-b1bfef0ec2b3)

---

## 🎯 Out-of-Sample Validation (March & April 2026)

To rigorously test the model's real-world utility, the generated forecast was benchmarked directly against actual, newly released USDA market data for **March 2026** and **April 2026**. The model demonstrated exceptionally tight alignment with the actual price action, validating its predictive reliability in live production environments.

![Validation against actual March/April 2026 data](https://github.com/user-attachments/assets/24ee5666-2747-4260-b480-68b12760910a)
