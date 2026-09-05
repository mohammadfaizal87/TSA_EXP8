# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 28-08-2026


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
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing

warnings.filterwarnings("ignore")

# Read CSV
df = pd.read_csv(r"House_Price.csv")

print("SHAPE OF DATASET:")
print(df.shape)

print("\nGIVEN DATA:")
print(df)

print("\nCOLUMN NAMES:")
print(df.columns)

# Select Price column
data = df["Price"].dropna().reset_index(drop=True)

plt.rcParams["figure.figsize"] = (12,5)

# First 50 values
plt.figure()
plt.plot(data.head(50))
plt.title("First 50 Values of House Price Data")
plt.xlabel("Observation")
plt.ylabel("Price")
plt.show()

# Moving Average - Window 5
rolling_mean_5 = data.rolling(window=5).mean()

print("\nFIRST 10 VALUES OF ROLLING MEAN:")
print(rolling_mean_5.head(10))

# Moving Average - Window 10
rolling_mean_10 = data.rolling(window=10).mean()

# Plot Original and Moving Average
plt.figure()
plt.plot(data, label="Original Data")
plt.plot(rolling_mean_10, label="Moving Average")
plt.title("Moving Average")
plt.xlabel("Observation")
plt.ylabel("Price")
plt.legend()
plt.show()

# Exponential Smoothing
model = ExponentialSmoothing(
    data,
    trend=None,
    seasonal=None
)

fit = model.fit()
exp_smooth = fit.fittedvalues

# Plot Exponential Smoothing
plt.figure()
plt.plot(data, label="Original Data")
plt.plot(exp_smooth, label="Exponential Smoothing")
plt.title("Exponential Smoothing")
plt.xlabel("Observation")
plt.ylabel("Price")
plt.legend()
plt.show()
```

### OUTPUT:

Moving Average

<img width="991" height="467" alt="image" src="https://github.com/user-attachments/assets/157d0644-eb7f-4e4b-bfbd-e262cbe554f8" />


Plot Transform Dataset

<img width="1070" height="792" alt="image" src="https://github.com/user-attachments/assets/9d656ed2-9616-49be-9c76-103fd99069f2" />


<img width="1244" height="586" alt="image" src="https://github.com/user-attachments/assets/9abe158c-3945-464b-936c-ea1989934857" />

<img width="639" height="252" alt="image" src="https://github.com/user-attachments/assets/3980e8b6-a757-410c-9bdf-e9c98c4ae777" />



Exponential Smoothing

<img width="1158" height="540" alt="image" src="https://github.com/user-attachments/assets/1831d630-5d67-431a-a411-16042e213cea" />



### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
