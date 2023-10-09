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
