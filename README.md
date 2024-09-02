# EX.NO: 2 DS
## AIM:
To perform Exploratory Data Analysis on the given data set.
      
## EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
## ALGORITHM:
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
df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/56285485-2ba7-4a6b-928e-d22bed9d53cc)
```
df.info()
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/5333143e-56e5-4e24-8866-13ff10f3229a)
```
df.set_index("PassengerId",inplace =True)
df.shape
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/3dfc8d54-6e91-49c0-aee8-056d2c5a3da1)
```
df.nunique()
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/813ba8c4-8905-43fd-8385-0292788883e2)
```
df["Survived"].value_counts()
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/b318f714-0510-46e7-9095-98f0bd63e0cb)
```
per=(df['Survived'].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/5adb45f6-f9b7-4cb0-a7a0-dbb7981f8723)
```
sns.countplot(data=df,x="Survived")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/f36c79b3-c8f9-47d4-af5d-8c2444c8e4f5)
```
fig, ax1 = plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x= 'Survived', data=df)
graph.set_xticklabels (graph.get_xticklabels (), rotation=90)
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2., height + 0.1, height,ha="center")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/fc38c081-962c-4711-9088-d3b443b15295)
```
df.Pclass.unique()
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/4f0509d4-2373-4437-b968-08f72cb06877)
```
df.rename(columns = {'Sex':"Gender"},inplace=True)
df
```
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/42a850a4-0dcd-4b1b-a6c2-edd1bb011277)
```
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/43dcc76a-9dfd-4d75-b7b8-42abe1a76532)
```
fig, ax1 = plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=df,x="Survived", hue="Pclass", palette="rainbow")
graph.set_xticklabels (graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height+ 20.8, height,ha="left")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/9154f664-ab0a-43a0-930a-3c01f6851ae6)
```
df.boxplot(column="Age",by="Survived")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/861be1f2-2a96-44fb-a1e8-e7595f676844)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/25f070d2-f4b8-4994-8e53-92d81791294f)
```
sns.jointplot(x="Age",y="Fare",data=df)
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/814aadf3-b3c5-425f-a0b4-a31ab5b09a54)
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue="Gender",data=df)
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/b6c1708c-279b-4422-b271-731725d18ea9)
```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/cc02b5e1-c113-4230-8dfe-21d4f0d472c9)
```
g= sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass", kind = "count", legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax =g.facet_axis(0,0)
for p in ax.patches:
ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/1c43b392-2ae5-46ca-8255-1d29f5d566cd)
```
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/cdfa62eb-3cf3-4d6d-be7f-1bed42bb2fb6)
```
sns.pairplot(df)
```
![image](https://github.com/22008837/EXNO2DS/assets/120194155/66fdadf5-ee96-43da-8b08-2ceb7ccadb9c)


## RESULT
Thus, the outputs verifies that the data set has been applied the EDA process and methods.
