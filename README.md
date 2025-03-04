# Name:Manimaran V
# Reg.no.212224220060
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
data=pd.read_csv("/content/SAMPLEIDS.csv")
data.head(7)
```
![Screenshot 2025-03-04 111154](https://github.com/user-attachments/assets/3d24b68d-414a-46ed-8949-211644ae22c9)
```
data.isnull()
```
![Screenshot 2025-03-04 111317](https://github.com/user-attachments/assets/f41c441f-3616-4118-843d-722b86b36d1a)
```
data.isnull().sum()
```
![Screenshot 2025-03-04 111418](https://github.com/user-attachments/assets/3a9c3604-c717-4cb3-82cd-41cbf8387a2f)
```
data.isnull().any()
```
![Screenshot 2025-03-04 111505](https://github.com/user-attachments/assets/294555e0-279b-4dba-b74a-cec15f92c5fb)
```
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data.tail(7)
```
![Screenshot 2025-03-04 111542](https://github.com/user-attachments/assets/7858c414-f334-4990-9d25-4fa2af83d9c9)
```
data.fillna(5)
```
![Screenshot 2025-03-04 111627](https://github.com/user-attachments/assets/3f1d0dff-2457-4f67-9fd5-79c51825eb00)
```
data.dropna(axis=0)
```
![Screenshot 2025-03-04 111742](https://github.com/user-attachments/assets/6eda901a-b1ba-49f8-acdc-7248a09f6922)
```
data.dropna(axis=1)
```
![Screenshot 2025-03-04 111826](https://github.com/user-attachments/assets/0e3805da-839d-4d8c-93fc-12c6de661cd3)
```
data.shape
```
![Screenshot 2025-03-04 111902](https://github.com/user-attachments/assets/0859cabb-c8b1-4648-9232-66b325e82ece)
```
data.info()
```
![Screenshot 2025-03-04 111939](https://github.com/user-attachments/assets/379362d3-93ba-46e3-a268-815a4e5edda0)
```
data.describe()
```
![{174FA54A-0071-4A36-9B67-34CEA0BBD455}](https://github.com/user-attachments/assets/0e2a277f-2856-4328-9b38-932b3f6e08d3)
```
data.fillna(method="ffill")
```
![{990D42C7-FE72-4284-ABB6-40F09AE5306A}](https://github.com/user-attachments/assets/f6852985-94cc-4c92-8c46-52239a8219da)
```
data.fillna(method="bfill")
```
![{FADBCD05-275B-4221-A51F-85AEEE953DCB}](https://github.com/user-attachments/assets/114819c3-e8d6-49b0-a010-2dbe5544f5d9)
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![{0B4B73C1-6292-4828-ABF1-EA4377CAD3C4}](https://github.com/user-attachments/assets/56586647-827d-4c91-9662-3d59288c6e06)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![{E1664756-BCE9-4A05-B191-398247183243}](https://github.com/user-attachments/assets/043268ce-9a40-4f7a-93cc-8a8fc192d7ba)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![{6CE0305F-030F-4A48-919A-FF82271DE99B}](https://github.com/user-attachments/assets/9db79812-a477-4f35-a6ab-7603e8ec7b2d)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![{7D63A4F0-2455-4952-B221-B1DB9DDBA3CF}](https://github.com/user-attachments/assets/a4dff01f-300e-411e-98b8-9e702dae2fa6)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![{34EDCCBF-C4DC-4C4A-B788-77AED922A708}](https://github.com/user-attachments/assets/b9746014-0fb1-4be4-af10-877f2c1c9da5)
```
sns.boxplot(x='sepal_width',data=delid)
```
![{D6A6DDE5-30A4-494B-8A91-76DD555DEFF8}](https://github.com/user-attachments/assets/a844ad61-f002-4055-874f-4fccff25aef4)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![{FFAC7F75-A79B-484F-9662-5546D665551E}](https://github.com/user-attachments/assets/fe47a759-b208-4f3f-a5f3-37bdc19cc61c)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![{DC5BF97E-05EE-4AEE-AE1B-A810CCD0D979}](https://github.com/user-attachments/assets/31502842-e0f7-4079-b8cb-b361ce82cabf)
```
low = q1 - 1.5*iqr
low
```
![{1BB24A93-EA91-4C82-9B5D-AF8B522A86A6}](https://github.com/user-attachments/assets/2f4995f8-ec3f-41fd-8faf-a4c30eb34c8b)
```
high = q3 + 1.5*iqr
high
```
![{5BD74F48-A5E4-4AE2-8BC6-1F10F17DC8D5}](https://github.com/user-attachments/assets/edbc4f4c-a6ad-421e-8ae6-b73e484338e5)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![{D6178023-B95D-4D88-B679-74A0CC18AF44}](https://github.com/user-attachments/assets/d1d2c637-1f88-4667-8c02-89bd0227aa3c)
```
z = np.abs(stats.zscore(df['height']))
z
```
![{B671BA08-383A-4834-8EC0-71852BCE22FE}](https://github.com/user-attachments/assets/58310005-e21a-4f82-a1a1-b84e686b9f43)
```
df1 = df[z<3]
df1
```
![{C504B75D-5DA6-4036-97B3-5355BCAC4149}](https://github.com/user-attachments/assets/f88bf36c-c09c-4868-a8c1-278f4099407f)

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
