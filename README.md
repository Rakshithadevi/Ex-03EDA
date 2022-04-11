# Ex-03EDA

## AIM
To perform EDA on the given data set. 

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

# ALGORITHM
```
## STEP 1
Import the required packages(pandas,numpy,seaborn).

## STEP 2
Read and Load the Dataset

## STEP 3
Remove the null values from the data and remove the outliers.

## STEP 4
Remove the non numerical data columns using drop() method.

## STEP 5:
returns object containing counts of unique values using (value_counts()).

## STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

## STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

## STEP 8:
Save the final data set into the file.

```

# CODE
```

import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('titanic_dataset.csv')
df.head()
df.info()
df.isnull().sum()
df['Cabin']=df['Cabin'].fillna(df['Cabin'].mode()[0])
df['Age']=df['Age'].fillna(df['Age'].mean())
df['Embarked']=df['Embarked'].fillna(df['Embarked'].mode()[0])
df.isnull().sum()
df.boxplot()
cols = ['Age', 'Fare','SibSp','Parch','Fare']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
survived_count = df.groupby('Survived')['Survived'].count()
survived_count
plt.title('Grouped by survival')
sns.countplot(x="Survived",data=df)
df["Pclass"].value_counts()
plt.title('Grouped by pclass')
sns.countplot(x="Pclass",data=df)
df["Sex"].value_counts()
plt.title('Grouped by gender')
sns.countplot(x="Sex",data=df)
df["Embarked"].value_counts()
plt.title('Grouped by embarkation')
sns.countplot(x="Embarked",data=df)
sns.displot(df["Fare"])
plt.title('Survived female and male')
sns.countplot(x="Sex",hue="Survived",data=df)
sns.countplot(x="Pclass",hue="Survived",data=df)
sns.countplot(x="Sex",hue="Survived",data=df)
sns.displot(df[df["Survived"]==0]["Age"])
sns.displot(df[df["Survived"]==1]["Age"])
pd.crosstab(df["Pclass"],df["Survived"])
pd.crosstab(df["Sex"],df["Survived"])
df.corr()
sns.heatmap(df.corr(),annot=True)

```
# OUPUT
![image](https://user-images.githubusercontent.com/94165326/162748459-41528ee9-b31d-4ca1-a5ac-6438882992fd.png)

![image](https://user-images.githubusercontent.com/94165326/162748539-6dc36aeb-8639-4a94-937d-8f1b97011bf7.png)

![image](https://user-images.githubusercontent.com/94165326/162748607-cad60196-200b-4df3-a127-49f7be527a08.png)

![image](https://user-images.githubusercontent.com/94165326/162748653-f59cb56d-9116-4ff4-8de9-3d18cae4a214.png)

![image](https://user-images.githubusercontent.com/94165326/162748702-842733a6-7422-4fb3-8142-0d666e7da212.png)

![image](https://user-images.githubusercontent.com/94165326/162748745-bf8930a5-e0f8-4e35-ad8f-1aad3f67dc17.png)

![image](https://user-images.githubusercontent.com/94165326/162748812-cfc92382-1477-42a8-b156-32a8fa835d95.png)

![image](https://user-images.githubusercontent.com/94165326/162748863-d6312c67-973e-43e5-978b-a24af2065acb.png)

![image](https://user-images.githubusercontent.com/94165326/162748944-70eff2e5-06e7-4541-97c1-326e7d7dce54.png)

![image](https://user-images.githubusercontent.com/94165326/162748998-b5c60f8e-60d7-4747-bf05-ea2b14518966.png)

![image](https://user-images.githubusercontent.com/94165326/162749052-13ee0d53-d74a-44bd-866c-293148063059.png)

![image](https://user-images.githubusercontent.com/94165326/162749104-56c8fa8e-6f93-486d-bc16-9e3e366d24b3.png)

![image](https://user-images.githubusercontent.com/94165326/162749142-cc021657-63f6-49c9-8828-95c2f4ff74ee.png)

![image](https://user-images.githubusercontent.com/94165326/162749176-0a48712e-659f-4b8e-9dcd-eb6a854593fb.png)

![image](https://user-images.githubusercontent.com/94165326/162749231-187a61a3-eb75-417b-9b54-963779d7b44a.png)

![image](https://user-images.githubusercontent.com/94165326/162749282-dab7cd23-5947-407d-ae9a-890252cbba79.png)

