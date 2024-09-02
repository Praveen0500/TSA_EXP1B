#### DEVELOPED BY : PRAVEEN S
#### REG NO : 212222240078
#### DATE : 

# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA

### AIM:
To perform regular differncing,seasonal adjustment and log transformation Onion Price data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv('/content/OnionTimeSeries - Sheet1.csv')

data['Date'] = pd.to_datetime(data['Date']) 
data.set_index('Date', inplace=True) 

data.fillna(method='ffill', inplace=True)

first_100_data = data.iloc[:100]

Max_data_100 = first_100_data['Max']

plt.figure(figsize=(14, 8))
plt.plot(Max_data_100, label='Max (First 100)')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Max Price of Onion (First 100 Data Points)')
plt.legend()
plt.show()

Max_diff_100 = Max_data_100.diff().dropna()

plt.figure(figsize=(14, 8))
plt.plot(Max_diff_100, label='Max (Diff - First 100)')
plt.xlabel('Date')
plt.ylabel('Differenced Price')
plt.title('Differenced Max Data (First 100 Data Points)')
plt.legend()
plt.show()

Max_log_100 = np.log(Max_data_100 + 1)

plt.figure(figsize=(14, 8))
plt.plot(Max_log_100, label='Max (Log - First 100)')
plt.xlabel('Date')
plt.ylabel('Log Transformed Price')
plt.title('Log-Transformed Max Data (First 100 Data Points)')
plt.legend()
plt.show()

Max_seasonal_adjustment_100 = Max_log_100 - Max_log_100.rolling(window=7).mean()
Max_seasonal_adjustment_100.dropna(inplace=True)

plt.figure(figsize=(14, 8))
plt.plot(Max_seasonal_adjustment_100, label='Max (Seasonally Adjusted - First 100)')
plt.xlabel('Date')
plt.ylabel('Seasonally Adjusted Price')
plt.title('Seasonally Adjusted Log-Transformed Max Data (First 100 Data Points)')
plt.legend()
plt.show()

```

### OUTPUT:

#### ORGINAL DATASET:
![image](https://github.com/user-attachments/assets/42592bed-fbf3-4cd0-b1cf-b182e4bf88ef)



#### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/d4f7ac0b-f7b0-4526-b203-495efc6bcc10)



#### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/a3481461-1d47-425b-9de5-c84b95509290)


#### LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/3fc0146c-785c-4259-9424-4b7cdc16c0a2)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Onion Price
data.
