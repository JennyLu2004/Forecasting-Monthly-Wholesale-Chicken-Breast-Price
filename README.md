# Forecasting-Monthly-Wholesale-Chicken-Breast-Price
 this is an internship project where the goal was to predict monthly wholesale chicken breast price for Tyson Foods. I use multiple time series models to predict this, which include:
- ARima
- Sarima
- SARIMAX model
- Triple exponential smoothing model
 The data sources that were used for this project are historical USDA data on wholesale chicken prices from 2001 - 2026. The four CSV files that were used were:
- EMI monthly prices of CSV
- slaughtered average pounds per head of CSV
- slaughter head counts of CSV
- slaughter total pounds of CSV 
the main working Python file is called EMI Forecast, so you'll be able to see everything that I work in here. 
Here's the main workflow of the project. 
First, import necessary libraries for the entire project which includes pandas, Matplotlib, Statsmodels, Sklearn, and PMDArima 
Prepping the data to remove any NA rows and setting it up for some time series exploratory data analysis 
there were three main drivers that I wanted to study, which are:
- chicken breast
- leg quarters
- wings
For the focus of this time series, I wanted to start with chicken breast first.
 To understand the chicken breast driver, I created a monthly plot, a quarterly plot to understand the seasonality, and a trend line plot over the years to see how the chicken breast price has performed.
 Seasonal decomposition.
 To understand how much of the past data is meaningful for us to use to predict future data, I plotted the ACF graph and the PACF graph. 
Use 80% of the existing data to test on 20% of the rest of the data. 
Before doing this train-test split, we also did a stationary test using an augmented Dickey-Fuller ADF test. This test helps us understand if the time series data that we have is stationary. It's important because stationarity is required for the time series model to accurately capture the trends, the patterns, and the statistical properties for it to be able to accurately predict. 
The models that were used to identify the best models were:
- Triple exponential smoothing
- SARIMAX model with different exogenous variables, such as chicken wings and leg quarters
- Economic factors from the Federal Reserve
- Slaughter data
- Slauughter data and economic factors
 here is a comparison table of how these models performed. 
<img width="1156" height="537" alt="image" src="https://github.com/user-attachments/assets/2597baa2-7bb8-40af-92a8-29a71d144d46" />
The SARIMAX model with economic factors, including U.S. coal prices, soybean prices, heating oil prices, unemployment rate, consumer sentiment index, consumer price index, and beef price, performs the best prediction with a MAPE score of 15.81, mean absolute error of 27.34, and a root mean square error of 31.06 
<img width="3597" height="80" alt="image" src="https://github.com/user-attachments/assets/96955e8b-5424-4b2b-b63c-1ed1ce9d6b0b" />
 Now that we have determined the best performing model, I built a 12-month forecast into the future using this model. 
 <img width="1137" height="657" alt="image" src="https://github.com/user-attachments/assets/29d4ad74-47c9-4e3a-801b-b1bfef0ec2b3" />
 I used this prediction to compare it to the actual USDA data in March 2026 and April 2026 and received really good results. 
 <img width="1248" height="677" alt="image" src="https://github.com/user-attachments/assets/24ee5666-2747-4260-b480-68b12760910a" />


