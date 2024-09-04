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

# Data Cleaning:
```py
   import pandas as pd
   df=pd.read_csv("/content/Data_set.csv")
   df
 ```
![Screenshot 2024-08-30 153058](https://github.com/user-attachments/assets/2163dce8-c03b-4036-b801-56f855868a64)
```py
   df.dropna(axis=1)
```
![Screenshot 2024-08-30 154002](https://github.com/user-attachments/assets/379ba1d6-4a80-4268-8d40-273d2797e7d6)
```py
  dfs=df[df['current_overall_rank']> 270]
  dfs 
```
![Screenshot 2024-08-30 155056](https://github.com/user-attachments/assets/151937b7-a64c-4893-bcce-12e53a3fff74)
```py
   df.iloc[:4]
```
![Screenshot 2024-08-30 155610](https://github.com/user-attachments/assets/fb83fbdc-333a-4b91-820f-56778378dd89)
```py
  df.iloc[0:4,1:4]
```
![Screenshot 2024-08-30 155811](https://github.com/user-attachments/assets/a8cd36b8-8750-4fb8-becc-388cd7151e96)
```py
  df.iloc[[1,3,5],[1,3]]
```
![Screenshot 2024-08-30 160015](https://github.com/user-attachments/assets/3f5e97e7-81e6-4151-96b6-a9b3ae1e3549)

```py
   df
```
![Screenshot 2024-08-30 160144](https://github.com/user-attachments/assets/14bebd5b-b11b-4a86-b597-28188d8e6d59)

```py
   dff=df.fillna(0)
   dff
```
![Screenshot 2024-08-30 160346](https://github.com/user-attachments/assets/4ca4c504-ff40-4089-b34c-1048880be9f0)
```py
  dff=df.fillna(method='ffill')
  dff
```
![Screenshot 2024-08-30 160609](https://github.com/user-attachments/assets/9b27b2fe-a598-4987-b881-25f83f5cce07)

```py
  dff=df.fillna(method='ffill')
  dff
```
![Screenshot 2024-08-30 160817](https://github.com/user-attachments/assets/eaa55ceb-decb-43ff-b69f-c5a53207abe7)

```py
  df['current_overall_rank'].fillna(value=df['current_overall_rank'].mean())
```
![Screenshot 2024-08-30 161151](https://github.com/user-attachments/assets/f36eb311-44ac-4fcc-be2e-8329637ab71a)

```py
  dfs=df['current_overall_rank'].fillna(value=df['current_overall_rank'].mean(),inplace=True)
  dfs
```
![Screenshot 2024-08-30 161914](https://github.com/user-attachments/assets/19c83670-94f3-4b52-988a-8ac53a25eb10)

# OUTLIER DETECTION AND REMOVAL USING IQR:

```py
  import pandas as pd
  import seaborn as sns
  import numpy as np
  age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
  af=pd.DataFrame(age)
  af
```
![Screenshot 2024-09-04 185951](https://github.com/user-attachments/assets/333f674a-eed1-41a0-9519-c0926f5f4471)

```py
 sns.boxplot(data=af)
```
![Screenshot 2024-09-04 190211](https://github.com/user-attachments/assets/e1fe40b0-13b1-4211-8a77-b467b788193e)

```py
 sns.scatterplot(data=af)
```
![Screenshot 2024-09-04 190530](https://github.com/user-attachments/assets/1039f11e-2b35-4763-bfd3-fb2cf7781247)

```py
  q1=af.quantile(0.25)
  q2=af.quantile(0.5)
  q3=af.quantile(0.75)
  iqr=q3-q1
  iqr
```
![Screenshot 2024-09-04 190626](https://github.com/user-attachments/assets/3216666b-fa75-4e2d-9924-2ef018cdbbcf)

```py
 Q1=np.percentile(af,25)
 Q3=np.percentile(af,75)
 IQR=Q3-q1
 IQR
```
![Screenshot 2024-09-04 190740](https://github.com/user-attachments/assets/6d3c2357-bf70-4032-b4e3-ee176c11cd72)

```py
 lower_bound=Q1-1.5*IQR
 upper_bound=Q3+1.5*IQR
 lower_bound
```
![Screenshot 2024-09-04 190907](https://github.com/user-attachments/assets/58af4389-52b4-422f-b5c0-50d30025e8a7)

```py
 upper_bound
```
![Screenshot 2024-09-04 191009](https://github.com/user-attachments/assets/2f6826a7-e2f3-46af-9662-d3e8d7a2d6eb)

```py
 outliers = [x for x in age if (x < lower_bound.iloc[0]) or (x > upper_bound.iloc[0])]
 print("q1",q1)
 print("q3",q3)
 print("iqr",iqr)
 print("lower bound",lower_bound)
 print("upper bound",upper_bound)
 print("outliers",outliers)
```
![Screenshot 2024-09-04 191103](https://github.com/user-attachments/assets/a85c5b0f-588a-4c8c-b9af-f0cc23c9c7fc)

```py
 af=af[((af>=lower_bound)&(af<=upper_bound))]
 af
```
![Screenshot 2024-09-04 191212](https://github.com/user-attachments/assets/e4e0700c-6627-493f-a418-daca9ae2e292)

```py
 af.dropna()
```
![Screenshot 2024-09-04 191310](https://github.com/user-attachments/assets/6c836f51-0bd4-4bbb-b2aa-00e4a7a97b4a)

```py
  data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
  mean=np.mean(data)
  std=np.std(data)
  print('mean of the dataset is',mean)
  print('std.deviation is',std)
```
![Screenshot 2024-09-04 191408](https://github.com/user-attachments/assets/371af59c-5c98-4d87-b209-c6c24cdb5bfa)

```py
 threshold=3
 outlier=[]
 for i in data:
   z=(i-mean)/std
   if z>threshold:
     outlier.append(i)
     print('Outlier in dataset is:',outlier)
```
![Screenshot 2024-09-04 191504](https://github.com/user-attachments/assets/200aa20a-9a52-48bb-a967-1b8d75ef6962)

```py
 import pandas as pd
 import numpy as np
 import seaborn as sns
 import pandas as pd
 from scipy import stats
 data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}

 df=pd.DataFrame(data)
 df
```
![Screenshot 2024-09-04 191609](https://github.com/user-attachments/assets/9a84d3af-37e5-4674-92b1-12505584e6dc)

```py
 z=np.abs(stats.zscore(df))
 print(df[z['weight']>3])
```
![Screenshot 2024-09-04 191702](https://github.com/user-attachments/assets/0047f5ea-5281-46a0-8906-9c907ddad62d)

```py
 val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]


 import numpy as np
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
![Screenshot 2024-09-04 191815](https://github.com/user-attachments/assets/f9b80f51-2f92-4a17-9263-be01cf1c4023)


# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
