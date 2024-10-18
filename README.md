### Date: 
### Name: Koduru Sanath Kumar Reddy
### Register no: 212221240024
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING



### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
~~~

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing


data = pd.read_csv('Electric_Production.csv', parse_dates=['DATE'], index_col='DATE')
print("Shape of the dataset:", data.shape)
print("First 20 rows of the dataset:\n", data.head(20))


plt.figure(figsize=(10, 6))
warnings.filterwarnings('ignore')
plt.plot(data['IPG2211A2N'][:50], label='Original Data')
plt.title('First 50 Values of the Electricity Production')
plt.xlabel('Date')
plt.ylabel('Electric Production')
plt.legend()
plt.show()

rolling_mean_5 = data['IPG2211A2N'].rolling(window=5).mean()
rolling_mean_10 = data['IPG2211A2N'].rolling(window=10).mean()

print("\nFirst 10 values of the rolling mean (window=5):\n", rolling_mean_5.head(10))
print("\nFirst 10 values of the rolling mean (window=10):\n", rolling_mean_10.head(10))

# Step 7: Create a new figure for plotting the original data and moving averages
plt.figure(figsize=(10, 6))


plt.plot(data['IPG2211A2N'], label='Original Data')
plt.plot(rolling_mean_5, label='Moving Average (window=5)', color='red')
plt.plot(rolling_mean_10, label='Moving Average (window=10)', color='green')
plt.title('Moving Average: Original Data vs Transformed Dataset')
plt.xlabel('Date')
plt.ylabel('Electric Production')
plt.legend()
plt.show()


model = ExponentialSmoothing(data['IPG2211A2N'], trend=None, seasonal=None, seasonal_periods=None)
exp_smoothing = model.fit()


plt.figure(figsize=(10, 6))
plt.plot(data['IPG2211A2N'], label='Original Data')
plt.plot(exp_smoothing.fittedvalues, label='Exponential Smoothing', color='red')
plt.title('Exponential Smoothing: Original Data vs Fitted Values')
plt.xlabel('Date')
plt.ylabel('Electric Production')
plt.legend()
plt.show()
~~~

### OUTPUT:

Moving Average

<img width="688" alt="image" src="https://github.com/user-attachments/assets/20ba6592-5894-4ba4-84e4-1bf2260d6b5b">


Plot Transform Dataset

<img width="688" alt="image" src="https://github.com/user-attachments/assets/650fa202-95f3-4f16-a123-cacdbc4e4fb3">

Exponential Smoothing

<img width="688" alt="image" src="https://github.com/user-attachments/assets/3221c10a-513f-4f3e-8996-e6ed3f128e4a">




### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
