[Untitled1 (1).ipynb](https://github.com/user-attachments/files/25074071/Untitled1.1.ipynb)# Exno:1
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
loan=pd.read_csv("/content/Loan_data.csv")
loan

```
<img width="1671" height="505" alt="image" src="https://github.com/user-attachments/assets/11997b97-a82b-4d56-9dfc-f503d3538a6e" />

```
loan.head()
```
<img width="1637" height="271" alt="image" src="https://github.com/user-attachments/assets/3ddcd1f5-83e2-4001-923f-bd142249b29f" />

```
loan.tail()
```
<img width="1628" height="255" alt="image" src="https://github.com/user-attachments/assets/7c58ff60-0db5-4079-9fba-03685d378e3e" />

```
loan.info()
```
<img width="1093" height="420" alt="image" src="https://github.com/user-attachments/assets/5a80b9ed-6a00-4ef9-8803-6ec792338715" />

```
loan.describe()
```
<img width="1358" height="359" alt="image" src="https://github.com/user-attachments/assets/cdfc0dfc-156f-4488-a482-54c4b74972d3" />

```
loan.isnull().sum()
```
<img width="769" height="552" alt="image" src="https://github.com/user-attachments/assets/43289ba6-2414-4545-88f7-8a1fe7022e1e" />

```
loan.isnull().any()
```
<img width="819" height="557" alt="image" src="https://github.com/user-attachments/assets/89ccea2e-46a8-49c6-a40b-7c4e42806a87" />

```
loan.dropna()
```
<img width="1673" height="518" alt="image" src="https://github.com/user-attachments/assets/604b8108-361f-4acf-8be7-674cb567e08f" />

```
loan.fillna(0)
```
<img width="1697" height="517" alt="image" src="https://github.com/user-attachments/assets/e4c7339c-52d9-4310-8388-a8c24287eef1" />

```
loan.fillna(method='ffill')
```
<img width="1677" height="517" alt="image" src="https://github.com/user-attachments/assets/b324ec98-4dca-46db-953a-479ce453fd87" />

```
loan.fillna(method='bfill')
```
<img width="1681" height="513" alt="image" src="https://github.com/user-attachments/assets/8d517643-e37b-4b6a-a4f2-1cb90fba1a74" />

```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```
<img width="1366" height="504" alt="image" src="https://github.com/user-attachments/assets/7011027b-d790-4bf8-8bc1-745d169287bd" />

```
ir.describe()
```
<img width="729" height="344" alt="image" src="https://github.com/user-attachments/assets/2d255cdb-712e-463f-bc0b-58f11a7311c6" />

```
import seaborn as sns
sns.boxplot(x='sepal_width', data=ir)
```
<img width="1237" height="576" alt="image" src="https://github.com/user-attachments/assets/3e4de7fb-429c-46d3-a3b3-0f42743dfab7" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```
<img width="737" height="35" alt="image" src="https://github.com/user-attachments/assets/364e512c-5b00-401f-ae2c-e8e6047ccee6" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```
<img width="525" height="237" alt="image" src="https://github.com/user-attachments/assets/338a282d-d197-4e79-9a41-941ccc873ce4" />

```
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```
<img width="933" height="551" alt="image" src="https://github.com/user-attachments/assets/5f638088-d4ec-4ee2-a0c3-5c1e8f54a74b" />

```
sns.boxplot(x='sepal_width',data=ran)
```
<img width="938" height="580" alt="image" src="https://github.com/user-attachments/assets/4c758886-93d5-46ee-b033-9cbea2aaeb9b" />

```
import numpy as np
import scipy.stats as stats

z=np.abs(stats.zscore(ir['petal_length']))
z
```
<img width="1360" height="651" alt="image" src="https://github.com/user-attachments/assets/4cdb0f3b-7e51-4ea6-9ce3-8cf59e61093a" />

```
ir1=ir[z<3]
ir1
```
<img width="975" height="504" alt="image" src="https://github.com/user-attachments/assets/3408683b-e13c-4546-8eff-352fae4f1ef5" />

# Result
    Thus the given data successfully performed data cleaning and saved the cleaned data to a file.     
