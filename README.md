### Developed By : SHARAN MJ
### Reg. NO . 212222240097
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average of amazon stock Price data.

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

from google.colab import drive
drive.mount('/content/drive')

# Make sure the path below reflects the actual location of your file in your Google Drive
data = pd.read_csv('/content/drive/MyDrive/time series/AMZN.csv') 

print("First 5 Rows of the dataset:")

# You were using a variable df which was not defined. Changed to data
print(data.head())

# Check the column names and correct 'Min' if necessary
print(data.columns) # Print the columns to verify the correct name

data['Date'] = pd.to_datetime(data['Date'], format='%Y-%m-%d') # Changed the format to %Y-%m-%d
data.set_index('Date', inplace=True)

# Access the correct column name for 'Min' (e.g., data['min'], data['Minimum'], etc.)
data['Low'] = data['Low'].fillna(method='ffill')

decomposition = seasonal_decompose(data['Low'], model='additive', period=7)


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

![Screenshot 2024-09-25 154432](https://github.com/user-attachments/assets/47e821c6-eafe-41e5-a238-ec34f739c9a3)


#### SEASONAL PLOT REPRESENTATION :

![Screenshot 2024-09-25 154451](https://github.com/user-attachments/assets/70bef172-3a4c-4c5b-bb48-117843a9f25c)



#### TREND PLOT REPRESENTATION :
![Screenshot 2024-09-25 154508](https://github.com/user-attachments/assets/7d317b2b-1d0e-43f1-b50d-82abee82161e)


#### PLOTTING THE DATA:
![Screenshot 2024-09-25 154523](https://github.com/user-attachments/assets/4ffd7ebb-4b83-46f1-a5a8-95343342a105)


#### OVERAL REPRESENTATION:

![Screenshot 2024-09-25 154532](https://github.com/user-attachments/assets/31277e0e-b983-4735-b677-8ba9e2913405)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition of the Onion Price data.
