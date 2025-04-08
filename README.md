# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 07.04.2025

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:


### OUTPUT:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
from statsmodels.tsa.stattools import adfuller

data = pd.read_csv("AirPassengers.csv")

df = pd.DataFrame(data)


ts.plot(title='Original AirPassengers Data')
plt.ylabel('Passengers')
plt.show()

ts_log = np.log(ts)
ts_log.plot(title='Log Transformed Data')
plt.ylabel('Log(Passengers)')
plt.show()

decomposition = seasonal_decompose(ts_log, model='multiplicative', period=12)
seasonal = decomposition.seasonal
trend = decomposition.trend
residual = decomposition.resid

decomposition.plot()
plt.suptitle("Seasonal Decomposition of Log Transformed Series")
plt.tight_layout()
plt.show()

ts_log_deseasoned = ts_log - seasonal
ts_log_deseasoned.plot(title='Seasonally Adjusted (Deseasoned) Data')
plt.ylabel('Deseasoned Log(Passengers)')
plt.show()

ts_log_deseasoned_diff = ts_log_deseasoned.diff().dropna()
ts_log_deseasoned_diff.plot(title='Regular Differencing (1st Order)')
plt.ylabel('Differenced')
plt.show()

result = adfuller(ts_log_deseasoned_diff)
print("ADF Statistic:", result[0])
print("p-value:", result[1])
print("Critical Values:")
for key, value in result[4].items():
    print(f"   {key}: {value}")

if result[1] < 0.05:
    print("✅ The series is stationary (p < 0.05)")
else:
    print("❌ The series is NOT stationary (p >= 0.05)")
```


ORIGINAL DATA:

![Screenshot 2025-04-08 083214](https://github.com/user-attachments/assets/7a441e0e-7694-4c75-8036-80fae44613ba)



REGULAR DIFFERENCING:

![Screenshot 2025-04-08 083251](https://github.com/user-attachments/assets/a5c54c8d-b426-4c35-a723-ac7221869a71)



SEASONAL ADJUSTMENT:


![Screenshot 2025-04-08 083243](https://github.com/user-attachments/assets/be6f1594-9cfc-4fa3-b8f4-fe21c2a908d9)



LOG TRANSFORMATION:


![Screenshot 2025-04-08 083221](https://github.com/user-attachments/assets/394a90d3-e8fa-4f4b-9a0a-512d2f09d7f9)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
