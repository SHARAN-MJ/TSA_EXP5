### Developed By : SHARAN MJ
### Reg. NO . 212222240097
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average of Onion Price data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:


```py


import pandas as pd
from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

df = pd.read_csv('/content/OnionTimeSeries - Sheet1.csv')

print("First 5 Rows of the dataset:")
print(df.head())

df['Date'] = pd.to_datetime(df['Date'], format='%m/%d/%Y') 
df.set_index('Date', inplace=True)

df['Min'] = df['Min'].fillna(method='ffill')

decomposition = seasonal_decompose(df['Min'], model='additive', period=7)


plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='black')
plt.title('Observed')
plt.ylabel('Observed')
plt.savefig('observed_plot.png')
plt.show()


plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='brown')
plt.title('Trend')
plt.ylabel('Trend')
plt.savefig('trend_plot.png')
plt.show()

plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='blue')
plt.title('Seasonal')
plt.ylabel('Seasonal')
plt.savefig('seasonal_plot.png')
plt.show()

plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='pink')
plt.title('Residual')
plt.ylabel('Residual')
plt.savefig('residual_plot.png')
plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/11e7f101-6480-4308-b49e-5a481cb6aeb0)


#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/174f5dea-807f-43c0-bddd-4182cd483185)



#### TREND PLOT REPRESENTATION :

![Untitled](https://github.com/user-attachments/assets/462ed5eb-7c65-4370-923b-a880b8bc462e)

#### PLOTTING THE DATA:

![Untitled-1](https://github.com/user-attachments/assets/9ccba9c3-11b6-42a7-9941-40390bd56be1)

#### OVERAL REPRESENTATION:

![Untitled](https://github.com/user-attachments/assets/f0bd5ea2-d10c-40a4-b472-e3124280fab5)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition of the Onion Price data.
