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









# Result
          <<include your Result here>>
