# EXNO2DS
# AIM:
  To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv("drive/MyDrive/titanic_dataset.csv")
dt
```
![image](https://github.com/user-attachments/assets/250da70b-a80a-4165-a8de-244f3ef9f633)
```
dt.info()
```
![image](https://github.com/user-attachments/assets/c3210a08-7008-43cd-9689-095e5242e053)
```
dt.set_index("PassengerId",inplace=True)
dt["Survived"].value_counts()
dt.describe()
```
![image](https://github.com/user-attachments/assets/5432bc48-0afa-4e14-91f8-1fbc4c3d963f)
```
dt.shape
```
![image](https://github.com/user-attachments/assets/d85f7922-4908-4900-891f-eaa8e08bffe6)

# CATEGORICAL ANALYSIS
```
dt.nunique()
```
![image](https://github.com/user-attachments/assets/309c8ee1-8d36-4311-80dc-e1fcbcdfaed5)
```
dt["Survived"].value_counts()
```
![image](https://github.com/user-attachments/assets/7cc491b4-ed7c-44c8-ba32-fad424747281)
```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
print(per)
```
![image](https://github.com/user-attachments/assets/e0664247-c526-4fc7-89b4-cb0171f9235d)

# UNIVARIATE ANALYSIS

```
sns.countplot(data=dt,x="Survived")
```
![image](https://github.com/user-attachments/assets/a9c2177d-fe16-454d-88fb-9364dfd3e528)
```
dt
```
![image](https://github.com/user-attachments/assets/7464fc74-2692-4188-83b2-841add35dcff)

# BIVARIATE ANALYSIS

```
dt.rename(columns={"Sex":"Gender"},inplace=True)
dt
```
```
sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")
```
![image](https://github.com/user-attachments/assets/ecf73db7-86ba-4e8a-8c18-843961b880e0)
```
dt.boxplot(column="Age",by="Survived")
```
![image](https://github.com/user-attachments/assets/96ddff26-c034-40be-98b2-548f1c016c17)
```
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![image](https://github.com/user-attachments/assets/a04f1ad6-3d61-4dd7-bbad-1ab901615385)
```
sns.jointplot(x=dt["Age"],y=dt["Fare"])
```
![image](https://github.com/user-attachments/assets/3d161a64-fab5-4ba3-83a8-b4c2bd1a989f)

# MULTIVARIATE ANALYSIS
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass",y="Age",hue="Gender",data=dt)
```
![image](https://github.com/user-attachments/assets/c7ae087b-0c05-4c74-8569-667629883652)
```
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/user-attachments/assets/2be0fd05-377d-4c27-8901-f504f8abebd4)
```
numerical_dt = dt.select_dtypes(include=np.number)
corr = numerical_dt.corr()
sns.heatmap(corr, annot=True)
```
![image](https://github.com/user-attachments/assets/6c1a8073-c1ee-487e-b769-8e195266edc1)
```
sns.pairplot(dt)
```
![image](https://github.com/user-attachments/assets/adaf9978-a7b0-4cd1-81be-7d3b0bd139f7)


# RESULT
 Hence performing Exploratory Data Analysis on the given data set is successful
