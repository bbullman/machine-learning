## Patterns in a Time Series

1. Trend: A pattern exists involving a long-term progression (increase or decrease) in the data
2. Seasonal: A periodic pattern exists due to the calendar. Seasonality is a fixed and known period.
3. Cyclical: A pattern exists where the data exhibits rises and falls that are not of fixed period. The duration of these fluctuations is usually of at least two years.
4. Irregular (noise): Describes random and irregular influence.

Seasons have a constant length with cyclical pattern. The average length of a cyclic patern is longer than the length of a seasonal pattern. The magnitude of a cycle shows more variations than the magnitude. It's harder to predict cyclical data.

### Steps to Decompose a Time Series

1. Estimate the trend
	1. Use smoothing procedures such as moving averages Or
	2. Model trend with regression
2. De-trend the series
	1. Additive Or
	2. Multiplicative
3. Estimate seasonal factors using the de-trended series
	1. Average the de-trended values for a specific season
	2. For instance, to get a seasonal effect for January, we average the de-trended values for all Januaries in the series, and so on
4. Determine the random (irregular) component
	1. Additive model: random = series - trend - seasonal
	2. Multiplicative model: random = series / (trend * seasonal)

### Additive Decomposition

Add trend, seasonal, noise data. Depends whether you'd want to use this or multiplicative.
### Multiplicative Decomposition

Multiply trend by seasonal by noise we get original data.

Multiplicative model is useful when the seasonal variation increases over time.
* Number of people, more technology, availability
## Stationarity

Stationary means you removed the seasonality and the trend in many cases.

Methods to test time series stationarity.

Visual: Plot data and see if statistical properties change with time.
Statistical test: Use augmented Dickey-Fuller (ADF) test.
* Null Hypothesis (series has a unit root (value of a = 1)
* Alternate hypothesis: series has no unit root
* Failure to reject the null hypothesis implies the series is non stationary

Strong stationarity is a distribution of finite sub sequence of random 

## Time vs. Frequency domain

## Time Series Forecasting

Time series forecasting is the use of a model to predict future values based on previously observed values.

One Step Forecast: predicting the observation at the next time step.
Multi-step Forecast: predicting the observation for the next K steps.


### Methods

1. Average method: forecast of all future values are equal to the mean of historical data
2. Naive method: simply set forecasts equal to last observed value
3. Seasonal naive method: set forecasts equal to the last observed value from the same season of the year (e.g. the same month of the previous year)
4. Drift method:  variation on the naive method to allow forecasts to increase or decrease over time (change is called drift)

Common approaches to forecasting:

## ETS Model

Error, Trend Seasonality
	* Time series model that has a linear trend, and increasing seasonal components implies ETS(A,M)
	* A time series model that has exponential trend, and no seasonality implies ETS(M,N)
	* Good baseline to use, although not be-all end-all model to forecast

Smoothing. Simple Exponential Smoothing (SES) - forecasts are calculated using weighted averages.

## Auto-Regressive integrated moving average (ARITA) models

* Autocorrelation refers to the degree of correlation between the values of the same variables across different 
* ACF (autocorrelation function plot) is a plot of the autocorrelation of a time series by lag
	* When we have a trend, small lags tend to be large and positive Autocorrelation
	* When we have seasonal there will be larger seasonal lags. When data are trended and seasonal, you see a combination of these effects.
* ARMA model (autoregressive moving average)
* ARIMA model combines the autoregression and moving average models

Holt's linear method

Damped Trend Methods

* Applies a constant some time in the future
* For values between 0 and 1 phi dampens the trend so that it approaches a constant some time in the future
* Short-run forecasts are trended awhile long-run forecasts are constant

Differencing
* One way to make a non-stationary time series stationary by computing the differences between consecutive observations
* Differencing can help stabilize the mean of a time series by removing changes in the level of a time series, and therefore eliminating or reducing trend and seasonality
* First, second, third ordering...

Box-Jenkins Method

* Refers to a systematic method of identifying, fitting, checking, and using integrated autoregressive modeling...