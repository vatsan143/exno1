# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

<h3 align="center">Data Cleaning</h3>

NAME: SRIVATSAN G 

REGISTER NO: 212223230216

```py
import pandas as pd
import numpy as np
df = pd.read_csv('SAMPLEIDS.csv')
df.head()
```
![image](https://github.com/user-attachments/assets/f44e8649-ee8a-414d-92b0-dd0d9f65e8be)

```py
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/ceb582b2-1277-4135-8dc7-411445b0aa53)

```py
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/deae6d6e-8c45-45f5-be72-4c495692fd93)

```py
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/157c8b98-36df-4c6a-a504-5cba2b2823db)

```py
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/b5d3d43c-7db3-44a9-b2f0-ce21a5ad5e01)

```py
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/c9631b32-2ca7-4608-95ce-9fa0529946d7)

```py
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/3ec2ed10-1f30-481e-8f37-e4884441f7b7)

```py
 df_dropped = df.dropna()
 df_dropped
```
![image](https://github.com/user-attachments/assets/44cead82-91b0-40a5-b9ac-113ee046fd21)

```py
df.fillna({'GENDER':'FEMALE','NAME':'PRIYU','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/c7e2a295-4135-4e02-951e-52e34108cb8c)


<hr><hr>

<h3 align="center">IQR(Inter Quartile Range)</h3>

```py
import pandas as pd
import numpy as np
import seaborn as sns
```
```py
ir = pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/ed22d468-5c28-473b-95ae-d320a20318ed)

```py
df.describe()
```

![image](https://github.com/user-attachments/assets/8f5c18cc-090b-4d2f-b7b8-d9c567075880)
```py
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/878c8eb5-0cb4-4bae-92b1-e009c7a0f2d5)

```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/fdeb48e0-9ff1-4797-a9d2-dd8cffa13ab0)

```py
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/66784894-6712-4158-9ab1-06141fa1afba)


```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/1c04e5dd-0c4e-4401-889a-904b868c669f)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/b9b8ca1c-75f1-412a-82ce-01fd46f8eb7f)


<hr><hr>

<h3 align="center">Z-Score</h3>

```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```py
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/5a8e71e5-679c-4701-b5e9-1b9ab3608f65)

```py
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```py
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/ced4f0f5-1ac0-4fb9-b95f-656d7d63803e)

```py
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/f1db4ad4-4c6b-4461-9eab-27cb09ceaa5c)

```py
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/49676c23-9961-4e90-bf6b-e1d41c22b4c6)

```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/72acbf1b-2c51-413b-b831-f81a3b4457ae)

```py
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/1fe0e609-cd7d-422c-8312-c0f963fc7a20)

```py
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/c3efb880-635b-47f5-a6dc-4e45d0f0a35b)

# Result
Hence the data was cleaned , outliers were detected and removed.
