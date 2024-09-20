# DEVELOPED BY: RAGAVENDRAN A
# REGISTER NO: 212222230114
# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Date: 



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
import warnings
warnings.filterwarnings('ignore')

# Load the Summer Olympics medals data
file_path = '/content/Summer_olympic_Medals.csv'  # Path to the medals dataset
data = pd.read_csv(file_path)

# Create a 'Total_Medals' column
data['Total_Medals'] = data['Gold'] + data['Silver'] + data['Bronze']

# Group by 'Year' and sum total medals
yearly_medals = data.groupby('Year')['Total_Medals'].sum()

# Plot settings
plt.rcParams['figure.figsize'] = [10, 7.5]

# Simulate ARMA(1,1) Process
ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=len(yearly_medals))

# Plot the simulated ARMA(1,1) process
plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process for Olympic Medals')
plt.xlim([0, 200])
plt.show()

# Plot ACF and PACF for ARMA(1,1)
plot_acf(ARMA_1)
plot_pacf(ARMA_1)
plt.show()

# Simulate ARMA(2,2) Process
ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=len(yearly_medals) * 10)

# Plot the simulated ARMA(2,2) process
plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process for Olympic Medals')
plt.xlim([0, 200])
plt.show()

# Plot ACF and PACF for ARMA(2,2)
plot_acf(ARMA_2)
plot_pacf(ARMA_2)
plt.show()
```

# OUTPUT:
# SIMULATED ARMA(1,1) PROCESS:
![image](https://github.com/user-attachments/assets/2fddebd6-bb87-4200-861a-681afb3f8411)


# Partial Autocorrelation
![image](https://github.com/user-attachments/assets/00fa6288-c13a-4860-8eb4-774c77c786b3)


# Autocorrelation
![image](https://github.com/user-attachments/assets/459f8e04-0d69-405a-bda5-e75cd9ba83bd)


# SIMULATED ARMA(2,2) PROCESS:
![image](https://github.com/user-attachments/assets/85501d48-c3e7-4237-846f-69a72dd04bd4)


# Partial Autocorrelation
![image](https://github.com/user-attachments/assets/20b73597-f3e8-4e8d-8bec-e43dbee1b129)


#Autocorrelation
![image](https://github.com/user-attachments/assets/466860dc-c725-47a0-b40f-2059d3d7dec0)


# RESULT:
Thus, a python program is created to fit ARMA Model for Time Series successfully.
