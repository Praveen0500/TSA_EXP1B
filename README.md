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

Max_data = data['Max']

plt.figure(figsize=(14, 8))
plt.plot(Max_data, label='Max')
plt.xlabel('Date')
plt.ylabel('Price')
plt.title('Max price of Onion')
plt.legend()
plt.show()

Max_diff = Max_data.diff().dropna()

plt.figure(figsize=(14, 8))
plt.plot(Max_diff, label='Max (Diff)')
plt.xlabel('Date')
plt.ylabel('Diffrenced Price')
plt.title('Differenced Max Data')
plt.legend()
plt.show()

Max_log = np.log(Max_data + 1)

plt.figure(figsize=(14, 8))
plt.plot(Max_log, label='Max (Log)')
plt.xlabel('Date')
plt.ylabel('Log Transformed Price')
plt.title('Log-Transformed Max Data')
plt.legend()
plt.show()

Max_seasonal_adjustment = Max_log - Max_log.rolling(window=7).mean()
Max_seasonal_adjustment.dropna(inplace=True)

plt.figure(figsize=(14, 8))
plt.plot(Max_seasonal_adjustment, label='Max (Seasonally Adjusted)')
plt.xlabel('Date')
plt.ylabel('Seasonally Adjusted Price')
plt.title('Seasonally Adjusted Log-Transformed Max Data')
plt.legend()
plt.show()

```

### OUTPUT:

#### ORGINAL DATASET:
![image](https://github.com/user-attachments/assets/38ab32d6-e475-4b8d-aa6b-5a44d2dc488f)


#### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/181fd307-0a27-43bd-98ec-56e10e7e9803)


#### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/9b514e18-5074-45ce-bbc9-648837d29050)


#### LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/6112e019-bc14-4558-8109-b7e259411deb)


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on Onion Price
data.
