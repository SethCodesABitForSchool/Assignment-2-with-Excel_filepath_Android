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

# Identify the Stationarity  - ADF Test for stationarity
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










