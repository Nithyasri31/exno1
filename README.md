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
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![Screenshot 2025-04-15 103834](https://github.com/user-attachments/assets/13239fcf-d9bb-4703-bd78-9c2262f78b63)
```
df.isnull()
```
![Screenshot 2025-04-15 104035](https://github.com/user-attachments/assets/06e8942d-0ebd-4544-a962-e901cb19e7a0)
```
df.notnull()
```
![Screenshot 2025-04-15 110705](https://github.com/user-attachments/assets/4fd7c715-a22c-403e-aa29-109c47f80ade)
```
df.dropna(axis=1)
```
![Screenshot 2025-04-15 110828](https://github.com/user-attachments/assets/57bd1449-23d8-43bf-b9e3-52ac067b24b0)
```
df.dropna(axis=0)
```
![Screenshot 2025-04-15 111100](https://github.com/user-attachments/assets/2d07a19a-0992-4a7e-8585-352c983adb52)
```
dfs=df[df['TOTAL']>270]
dfs
```
![Screenshot 2025-04-15 111206](https://github.com/user-attachments/assets/a22c9729-c167-4b20-887e-8d333e171653)
```
dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
dfs
```
![Screenshot 2025-04-15 111506](https://github.com/user-attachments/assets/6bc7a460-b27c-49e2-bd35-5bd3ae36847b)
```
df.iloc[:4]
```
![Screenshot 2025-04-15 111630](https://github.com/user-attachments/assets/0245b0e5-2305-469e-af02-02cae2a8ac1b)
```
df.iloc[0:4, 1:4]
```
![Screenshot 2025-04-15 111721](https://github.com/user-attachments/assets/b0ea569d-2291-475c-aa94-59dfa13ad26f)
```
df.iloc[[1,3,5],[1,3]]
```
![Screenshot 2025-04-15 112051](https://github.com/user-attachments/assets/962c6ac3-464b-4fc2-8b1c-79bd30d57564)
```
df
```
![Screenshot 2025-04-15 112149](https://github.com/user-attachments/assets/f3363086-a2a8-403a-bdc8-0ed78a81563c)
```
dff=df.fillna(0)
dff
```
![image](https://github.com/user-attachments/assets/1033121c-5ace-4347-b2ef-d9ad0c86126c)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean())
```
![image](https://github.com/user-attachments/assets/a427c2a2-42e3-4263-a718-0b6fadcfd2ec)
```
dff
```
![image](https://github.com/user-attachments/assets/832c5777-abe8-41c1-8db6-c187aaf85fc1)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/c6e59b88-e6ef-4bc8-bea0-5da7a0c5ba0d)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/b1ef9ecb-8f9d-4ae0-abba-fce96f30dcdb)
```
df['TOTAL'].fillna(value=df['TOTAL'].mean(), inplace=True)

df
```
![image](https://github.com/user-attachments/assets/a0ed8d8a-95de-46d7-9e06-d36919f0de19)
```
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/42e01910-335f-4257-81db-2c679d98b1c1)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/cf5ac8d0-0125-4f7e-97f6-f13be2e719ae)
```            
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/a532f588-6975-4eee-a5eb-fae39c9d6c88)
```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/f5041228-35b7-46fa-be24-0d87a0eb6dfa)
```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/f38df096-7a70-4514-9d51-36ca89f527d6)
```
lower_bound=Q1-1.5*IQR
upper_bound= Q3+1.5*IQR

lower_bound
```
![image](https://github.com/user-attachments/assets/7483e161-6498-4399-9802-9f733d60ac61)
```
upper_bound
```
![image](https://github.com/user-attachments/assets/29f61fd5-76a5-4624-b202-72b5c1023c44)
```
outliers=[x for x in age if x < lower_bound or x > upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower bound:", lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/b5c0f07a-8dc5-4383-a0ff-e1aac4e7ef97)
```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/9ada0292-c227-414e-b62b-6db7fc96c7ac)
```
af.dropna()
```
![image](https://github.com/user-attachments/assets/d2ffdf48-12d3-452b-80ea-be79c12d28d5)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/8a719aee-1f86-415a-8bde-d8d69792285e)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/f66ca0da-1f87-4b07-ad5c-43ee5c1ba710)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/08221e9f-30f2-47b2-9566-8546eabd42f4)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/f1757345-b928-485b-895c-6cd5ad856ddc)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/43402628-396d-48ad-b79c-f0bcc885c356)
```
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]}

import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/5780c8f6-edf9-452c-8aed-601b06b45c5f)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/efee07f7-02df-4dc4-8b62-2d8b2e41c7a4)
```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,7
out=[]
def d_o(val):
ts=3
m=np.mean(val)
sd=np.std(val)
for i in val:
z=(i-m)/sd
if np.abs(z)>ts:
out.append(i)
return out
op=d_o(val)
op
```
![image](https://github.com/user-attachments/assets/8a4f6ee8-255f-46df-abc7-7fe46c3a30c9)
```
# Result
          the given data and perform data cleaning and successfully saved the cleaned data to a file.
