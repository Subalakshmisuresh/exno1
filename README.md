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



# Result
        Thus the program is executed successfully.
