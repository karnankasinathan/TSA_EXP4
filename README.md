### Developed by : Karnan K
### Reg no : 212222230062
### Date :
# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
data = pd.read_csv('/content/baggagecomplaints.csv')
print(data.head())
production = data['Baggage'].dropna()
ar1 = np.array([1, -0.5])  # AR(1) coefficient
ma1 = np.array([1, 0.5])   # MA(1) coefficient
arma11_process = ArmaProcess(ar1, ma1)
arma11_sample = arma11_process.generate_sample(nsample=len(production))
ar2 = np.array([1, -0.5, 0.25])  # AR(2) coefficients
ma2 = np.array([1, 0.4, 0.3])    # MA(2) coefficients
arma22_process = ArmaProcess(ar2, ma2)
arma22_sample = arma22_process.generate_sample(nsample=len(production))
plt.figure(figsize=(14, 8))
plt.subplot(221)
plot_acf(arma11_sample, lags=20, ax=plt.gca(), title='ACF of Simulated ARMA(1,1)')
plt.subplot(222)
plot_pacf(arma11_sample, lags=20, ax=plt.gca(), title='PACF of Simulated ARMA(1,1)')
plt.subplot(223)
plot_acf(arma22_sample, lags=20, ax=plt.gca(), title='ACF of Simulated ARMA(2,2)')
plt.subplot(224)
plot_pacf(arma22_sample, lags=20, ax=plt.gca(), title='PACF of Simulated ARMA(2,2)')
plt.tight_layout()
plt.show()
```
OUTPUT:
SIMULATED ARMA(1,1) PROCESS:

Partial Autocorrelation

![Screenshot 2024-09-11 095052](https://github.com/user-attachments/assets/6e5b4bb6-5f64-4380-9b0c-d0afa5176bb9)

Autocorrelation

![Screenshot 2024-09-11 095106](https://github.com/user-attachments/assets/7224b7cc-e040-4737-bd02-8a7843060fa2)

SIMULATED ARMA(2,2) PROCESS:

Partial Autocorrelation

![Screenshot 2024-09-11 095115](https://github.com/user-attachments/assets/dd4c8ea1-7134-4ce8-a065-8ff752a2f580)

Autocorrelation

![Screenshot 2024-09-11 095126](https://github.com/user-attachments/assets/881a1d7d-cc80-4fc9-b142-483414759a26)

RESULT:
Thus, a python program is created to fit ARMA Model successfully.
