# Assignment 2 - Topic: Stationary TS Models
Solve the following problems from Enders (Ch. 2) - (end of chapter) Questions and Exercises: 9 and 10.

Source: https://time-series.net/data_sets

# Question 9: 

The second column in file SIM_2.XLS contains the 100 values of the simulated ARMA(1, 1) process used in Section 7. This series is entitled Y2. Use this series to perform the following tasks (Note: Due to differences in data handling and rounding, your answers need only approximate those presented here.):

a. Plot the sequence against time. Does the series appear to be stationary? Plot the ACF.

b. Verify the results in Table 2.3.

c. Estimate the process using a pure MA(2) model. You should obtain 

yt = −1.15𝜀t−1   +   0.522𝜀t−2 + et        ; usable observations: 100
     (−13.22)          (5.98)

Verify that the Ljung–Box Q-Statistics are Q(8) = 28.48, Q(16) = 37.47, and Q(24) = 38.84 with significance levels of 0.000, 0.000, and 0.015, respectively.

d. Compare the MA(2) to the ARMA(1, 1).

# Question 10: 

The third column in file SIM_2.XLS contains the 100 values of the simulated AR(2) process used in Section 7. This series is entitled Y3. Use this series to perform the following tasks (Note: Due to differences in data handling and rounding, your answers need only approximate those presented here.):

a. Plot the sequence against time. Verify the ACF and the PACF coefficients reported in Section 7. Compare the sample ACF and PACF to those of a theoretical AR(2) process.

b. Estimate the series as an AR(1) process. You should find that the estimated AR(1) coefficient and the t-statistic are 
yt = 0.467yt−1  +   et
      (5.24)

Show that the standard diagnostic checks indicate that this AR(1) model is inadequate. Be sure to perform a recursive estimation of the AR(1) model and to plot the CUSUMs.

c. Could an ARMA(1, 1) process generate the type of sample ACF and PACF found in part a? Estimate the series as an ARMA(1, 1) process. You should obtain

yt = 0.183yt−1   +   0.510𝜀t−1     + et       ; usable observations: 99
     (1.15)            (3.64)

Use the Ljung–Box Q-statistics to show that the ARMA(1, 1) model is inadequate.

d. Estimate the series as an AR(2) process to verify the results reported in the text.

# Install Packaged for Excel
install.packages("readxl")
# Load the readxl library
library(readxl)

# Example - ousourced 
path <- file.path("C:", "Users", "John", "Documents", fsep="\\")
setwd(path)

# Specify the file path
file_path <- file.path("C:", "Users", "kumbalas-INS", "Downloads", "Sim.xlsx")


# Print the file path (optional)
cat("File Path:", file_path, "\n")
C:\Users\kumbalas-INS\Downloads\sim.xlsx

# Load the readxl package to read Excel files
library(readxl)
data <- read_excel(file_path)

# Read the dataset with the filepath 

file_path <- file.path("C:", "Users", "kumbalas-INS", "Downloads", "Sim_2.38134535.xls")

# Extract Y2
data_subset <- subset(data, select = c("Y2"))

# Remove data/values to declutter the REnvironment
rm(data)
rm(file_path)

The data in Y2 is already a time series (so not creating a ts object)

# Plot the time Series (Method 1)
plot.ts(data_subset, main= "Time Series of Y2", ylab= "Y2TS", col= "red")
![c7dba089-cc95-4534-bf5e-654effbf460d](https://github.com/SethCodesABitForSchool/Assignment-2-with-Excel_filepath_Android/assets/147195203/a95e0a3d-6c3e-4659-822d-c8245208ba3d)


# Install and Load required library
install.packages("TSA")
library(TSA)

Output: 
package ‘xts’ successfully unpacked and MD5 sums checked
package ‘TTR’ successfully unpacked and MD5 sums checked
package ‘curl’ successfully unpacked and MD5 sums checked
package ‘quadprog’ successfully unpacked and MD5 sums checked
package ‘zoo’ successfully unpacked and MD5 sums checked
package ‘quantmod’ successfully unpacked and MD5 sums checked
package ‘jsonlite’ successfully unpacked and MD5 sums checked
package ‘leaps’ successfully unpacked and MD5 sums checked
package ‘locfit’ successfully unpacked and MD5 sums checked
package ‘tseries’ successfully unpacked and MD5 sums checked
package ‘TSA’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
C:\Users\kumbalas-INS\AppData\Local\Temp\RtmpwjROPj\downloaded_packages

# Plot the time series (Method 2)
plot(data_subset$Y2, type = "l", main = "Time Series Plot - Y2")

![b6a9773a-5a03-40ff-b6f7-73152d80e9ee](https://github.com/SethCodesABitForSchool/Assignment-2-with-Excel_filepath_Android/assets/147195203/e9810326-3a7c-4b58-b4ec-d2e08d1f361d)

# Identifying Stationarity using the summary stats

The primary assumptions of Stationary Series are that it must have a constant mean and variance.

1. Constant Mean: The mean of the time series should remain approximately constant over time. This means that, on average, the series does not trend upward or downward.

2. Constant Variance: The variance (or standard deviation) of the time series should remain relatively constant over time. This implies that the spread or dispersion of the data points should not change systematically.

3. Autocorrelation Structure: The autocorrelation structure, as indicated by the Autocorrelation Function (ACF), should decay relatively quickly to zero. Autocorrelation measures the relationship between a data point and its lagged values. In a stationary series, this relationship should diminish rapidly.

These assumptions of stationarity are essential for many time series models to work effectively. If a series violates these assumptions, it may be necessary to transform or difference the data to induce stationarity. For example, differencing can be used to remove trends or seasonality.

In summary, when assessing stationarity, you often check for constant mean, constant variance, and a stable autocorrelation structure. Statistical tests like the Augmented Dickey-Fuller (ADF) test and visual inspection, including plotting the time series and its ACF, can help you make these assessments.


# Identifying the Stationarity using ADF Test for stationarity
adf_test <- adf.test(ts_data$Y2)
print(adf_test)

# Convert data_subset$Y2 to a vector - Not sure for what
y2_vector <- data_subset$Y2

# Plot the time series
plot(y2_vector, type = "l", main = "Time Series Plot - Y2")


# Install and Load Tseries

ADF.test is part of Tseries. 

install.packages("tseries")

library(tseries)


# ADF Test for stationarity
adf_test <- adf.test(y2_vector)


print(adf_test)


# Output of ADF - Test:
  
  
Augmented Dickey-Fuller Test -Significance level 0.05 

data:  y2_vector

Dickey-Fuller = -8.0087, Lag order = 4, p-value = 0.01


alternative hypothesis: stationary



The output from the Augmented Dickey-Fuller (ADF) test provides information about whether a time series is stationary or not. 

1. Dickey-Fuller: This is the test statistic value. In your output, it is -8.0087.



2. Lag order: This is the number of lags used in the regression. In your output, it is 4.



3. p-value: This is the p-value associated with the test statistic. In your output, it is 0.01.



Alternative hypothesis: This indicates the alternative hypothesis of the test. In this case, it is "stationary," meaning we are testing whether the time series is stationary.




1. Test Statistic (Dickey-Fuller): The more negative the test statistic, the stronger the evidence against the null hypothesis (the hypothesis of non-stationarity). In your case, the test statistic is -8.0087, which is quite strongly negative.



2. p-value: The p-value is compared to a significance level (commonly 0.05). If the p-value is less than the significance level, you reject the null hypothesis. In your case, the p-value is 0.01, which is less than 0.05. Therefore, you reject the null hypothesis.



3. Conclusion: Since the p-value is less than the significance level, you have evidence to reject the null hypothesis. The alternative hypothesis is accepted, suggesting that the time series (y2_vector) is stationary.


# Plot the ACF

acf(y2_vector, lag.max = 25, type = c("correlation"), plot = TRUE, col= "red", main= "Auto-Correlation Function of Y2")



# Load required libraries
install.packages("dplyr")
library(dplyr)

# Calculate mean and variance for the entire series
mean_whole <- mean(y2_vector)
var_whole <- var(y2_vector)

# Calculate mean and variance for different time intervals (e.g., first half vs. second half)
half_length <- length(y2_vector) %/% 2
mean_first_half <- mean(y2_vector[1:half_length])
var_first_half <- var(y2_vector[1:half_length])

mean_second_half <- mean(y2_vector[(half_length + 1):length(y2_vector)])
var_second_half <- var(y2_vector[(half_length + 1):length(y2_vector)])

# Print the results
cat("Mean (Whole):", mean_whole, "\n")
cat("Variance (Whole):", var_whole, "\n")
cat("Mean (First Half):", mean_first_half, "\n")
cat("Variance (First Half):", var_first_half, "\n")
cat("Mean (Second Half):", mean_second_half, "\n")
cat("Variance (Second Half):", var_second_half, "\n")


install.packages("gdata")
library(gdata)

ACF1 = acf(y2_vector, lag.max= 25, main= "AutoCorrelation Function", col= "red", lwd= 2)
ACF1


# Install the forecast package (uncomment the line below if you haven't installed it)
install.packages("forecast")

# Load the forecast package
library(forecast)


# Assuming y2_vector is your time series
adf_test_result <- adf.test(y2_vector)
print(adf_test_result)

# Assume you have your time series data in y2_vector
# Model 1
model1 <- arima(y2_vector, order = c(1, 0, 1))
summary(model1)

# Model 2
model2 <- arima(y2_vector, order = c(1, 0, 1), fixed = c(NA, 0))
summary(model2)
# Model 2 with ma1 fixed to 0
model2 <- arima(y2_vector, order = c(1, 0, 1), fixed = c(NA, 0, NA))
summary(model2)


# Example of calculating error measures (MAE, RMSE, etc.)
residuals <- resid(model1)
error_measures <- accuracy(residuals)


# Model 3
model3 <- arima(y2_vector, order = c(1, 0, 1), fixed = c(NA, 0, NA))
summary(model3)











