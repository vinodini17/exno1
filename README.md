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
NAME : KAVIYA D
REG NO : 212223040089
```

```
import pandas as pd
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp.head()
```

![image](https://github.com/user-attachments/assets/f4a6b2a1-2b65-4636-9a21-2eeb078236ad)


```
exp.head(5)
```
![image](https://github.com/user-attachments/assets/4dd0a95f-c054-4ddb-a850-ad87f299c3ba)


```
exp.tail(5)
```
![image](https://github.com/user-attachments/assets/c0bd8d76-6d98-40dc-bd53-92bbe703ef49)


```
exp.isnull().sum()
```
![image](https://github.com/user-attachments/assets/b0cd6dea-e226-4dd8-abc9-794c845d1b63)


```
exp.isnull().any()
```

![image](https://github.com/user-attachments/assets/b78f98dc-5aa1-45c8-b44d-87e3c89384bb)


```
exp.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/e9953349-7bb1-4b31-8ad1-18235d3353eb)





![image](https://github.com/user-attachments/assets/02ee089f-4ce9-47b4-8c84-fae650714ca8)

```
exp.fillna(50)
```
![420750698-63dd4505-8952-4284-ab10-aa99b743086e](https://github.com/user-attachments/assets/4ae5fb27-5c27-45d6-9d1a-ce1e556bd521)


![420750732-b6061196-c97f-4a66-b8ca-0d67f81c1ce3](https://github.com/user-attachments/assets/d7a339ba-c012-4fa6-beeb-ef1454656162)

```
exp.fillna(method='ffill')
```
![420750782-bc03a320-dd35-4d77-80a2-f98b5f4cf82a](https://github.com/user-attachments/assets/85033de2-8c77-4017-b9d8-31e8bff4090d)


![420750818-7874a207-7a1b-4943-8a84-0855441f7ff6](https://github.com/user-attachments/assets/d1704ed1-d581-4fa1-9faf-bd32a27880c8)


```
exp.fillna(method='bfill')
```
![420750924-8aa12dfb-c830-49aa-ac4b-5e0be68e83f7](https://github.com/user-attachments/assets/3cc7f316-6c2d-4b83-af93-00a2536e640e)


```
lab.fillna({'GENDER':'MALE','NAME':'PRAKASH','ADDRESS':'POONAMALEE','M1':'50','M2':'89','M3':'75','M4':'82','TOTAL':'896','AVG':'89.00000'})
```

![420751033-1b02e0ae-accb-4728-b787-5aad7d360e5e](https://github.com/user-attachments/assets/8d54b2dd-a3d3-4330-a0a5-de54a4c6c360)


```
exp=pd.read_csv("/content/iris.csv")
exp
```

![420751828-fbd1ef1a-4cda-4949-8e4c-d190fa5d6351](https://github.com/user-attachments/assets/d1ec7c0e-e60c-4694-be01-c4e54fa0cf7d)


```
lab.describe()
```
![420751921-bef8f811-36ab-4e7f-bbb0-8bd8ca8e5c2b](https://github.com/user-attachments/assets/13b7ca5f-a9a6-427c-bfdf-0f6738945357)



```
import seaborn as sns
sns.boxplot(x='sepal_width',data=lab)
```

![420751978-ed471a98-21ef-47ec-bf23-b46f7dd75905](https://github.com/user-attachments/assets/19e2a370-8e53-40d3-b864-6e02c41486b2)


```
q1=lab.sepal_width.quantile(0.25)
q3=lab.sepal_width.quantile(0.75)
iq=q3-q1
print(iq)
```
![420752064-cbcc3301-28b0-48ea-a970-ea6053bbf32b](https://github.com/user-attachments/assets/1ef7faf2-a9bf-44b1-8682-01401cb6a227)


```
rid=lab[((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```

![420752153-d28c0937-992b-4f62-a27f-97e024e0d059](https://github.com/user-attachments/assets/a262db3a-ed95-468e-a3a5-d394493ca789)

```
depo=lab[~((lab.sepal_width<(q1-1.5*iq))|(lab.sepal_width>(q3+1.5*iq)))]
depo
```

![420752239-537c49fc-7535-476c-9d43-2504d991b062](https://github.com/user-attachments/assets/a521461c-549a-4d77-a8b8-8f894d2c51db)

```
sns.boxplot(x='sepal_width',data=depo)
```

![420752360-e93c6054-522b-4860-baa9-c9ea904a4bb0](https://github.com/user-attachments/assets/a47d15c0-8fcf-4c43-b26c-6127034e030a)


```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(lab.sepal_width))
z
```

![420752530-b12bca86-3276-4bf9-bdcf-722beaaef020](https://github.com/user-attachments/assets/cb3ff664-f7b8-4ef9-b91e-8e1208f243e0)


```
p=lab[z<2]
p
```

![420752627-153084b9-b5b5-4f23-a4b8-8c43a4be9364](https://github.com/user-attachments/assets/67ba96d4-cc45-4539-b647-08241dfacf69)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
