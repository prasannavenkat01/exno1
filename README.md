# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file

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
<b>

  
```
import pandas as pd
df = pd.read_csv("SAMPLEIDS.csv")
df
  
```
![Screenshot 2024-08-17 045947](https://github.com/user-attachments/assets/9b21a511-74e7-4391-8fec-7d484d5c8db2)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/8684b84a-8dd1-4218-bed8-5286c8f0ffba)

```
df.isnull().any()
```
![Screenshot 2024-08-17 051202](https://github.com/user-attachments/assets/fe4d875b-11c6-40de-a772-a4505d35e056)

```
df.dropna()
```
![Screenshot 2024-08-17 051713](https://github.com/user-attachments/assets/4dd40918-2499-4e51-b7e8-93365c99b994)

```
df.fillna(0)
```
![Screenshot 2024-08-17 051915](https://github.com/user-attachments/assets/57581ab2-bd73-4ddb-afec-927f25e2267e)

```
df.fillna(method = 'ffill')
```
![Screenshot 2024-08-17 052515](https://github.com/user-attachments/assets/2a613548-327b-4001-b75e-a2ad60eb5e94)


```
df.fillna(method = 'bfill')
```
![Screenshot 2024-08-17 052653](https://github.com/user-attachments/assets/aaac5d62-cc49-44c1-878c-cd00e6eae96e)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/3d4e853c-95a2-456e-9358-afa1c76720fd)


```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot 2024-08-17 053307](https://github.com/user-attachments/assets/27c8b07d-51f0-47c2-a66b-b180b9537ba9)


IQR(Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/5fd7ef06-f4d1-488c-b667-c8fc619cb3ac)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/a427fe5f-d383-454e-8a62-b2fa5e00ba8d)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/c09097d6-dd5d-4f4d-9798-dbfff47de73b)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/df3e1f7f-9434-4681-b6ba-b9b5f6b22d74)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/11d0f6ab-9069-44f7-b3e3-4d9fb7d0e094)


```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/7a426a70-bf4e-4bce-9624-3b9f77aceade)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/98541071-6c0a-49ec-b337-3e03792fba2b)

</b>
<B>Z-SCORE<B/>

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("heights.csv")
dataset
```
![Screenshot 2024-08-17 055645](https://github.com/user-attachments/assets/0ef48b71-46f1-4b20-b3da-000ec195a73e)


```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

iqr = q3-q1
iqr
```
![Screenshot 2024-08-17 055924](https://github.com/user-attachments/assets/706cc8ea-66fb-462d-91bb-e32d28d92ffb)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/7f3c3f58-602f-4f9a-a18e-8da072188dcf)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/ea6c5afa-c262-46b0-a40b-71d44bd2eba7)


```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/b82fb361-8414-41eb-8798-99fe70ad9559)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/6ad54e9e-574f-4c98-804f-926f52f78240)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/1808aaf3-2a3d-4047-b204-50c04f926ffb)



# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
