#  Ex-04-Multivariate-Analysis

# AIM:
To perform Multivariate EDA on the given data set.

# EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
STEP 1
Import the built libraries required to perform EDA and outlier removal.

STEP 2
Read the given csv file

STEP 3
Convert the file into a dataframe and get information of the data.

STEP 4
Return the objects containing counts of unique values using (value_counts()).

STEP 5
Plot the counts in the form of Histogram or Bar Graph.

STEP 6
Use seaborn the bar graph comparison of data can be viewed.

STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

STEP 8
Save the final data set into the file

# PROGRAM:

```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

dt=pd.read_csv("/content/titanic_dataset.csv")
dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.describe()

dt.shape

dt.nunique()

dt["Survived"].value_counts()

per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per

sns.countplot(data=dt,x="Survived")

fig,ax1=plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x='Survived',data=dt)
graph.set_xticklabels(graph.get_xticklabels(),rotation=90)
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2.,height+0.1,height,ha="center")

dt

dt.Pclass.unique()

dt.rename(columns={'Sex':'Gender'},inplace=True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)

sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")

fig,ax1=plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=dt,x='Survived',hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2,height+20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x=dt["Age"],y=dt["Fare"])

fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")

g=sns.countplot(data=dt,col='Survived',x="Gender",hue="Pclass",kind="count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax=g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()-0.01,p.get_height()*1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

corr=dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
# OUTPUT:

![s1](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/9ec49c85-571d-4a05-80f5-4ab0c59afb11)

![s2](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/b9dd308b-3767-42cb-af63-15495207484f)

![s3](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/674ac423-cd06-4d88-9372-f63bbc306a45)

![s4](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/6af74ca7-72d3-4ac3-a0c6-499800f307b1)

![s5](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/4e2f6e7b-8765-42a6-af5f-26ac9507f051)

![s6](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/1a20b9b3-6d21-4695-851c-550bcfbabf9b)

![s7](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/1397c8d4-49ad-4ae2-9701-f896ae772247)

![s8](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/f1e098d3-5952-4896-ae1f-053bac5ed0b4)

![s9](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/0d0ac2a6-4e7d-4509-a9eb-d48492714b38)

![s10](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/5554793b-815d-4ac5-abbf-067dcb096a37)

![s11](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/021c4fd3-c53f-4ec5-9d9a-987f42b545b7)

![s12](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/2f5adf47-6771-430b-b73c-410fb397b555)

![s13](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/1816e87a-9830-4140-a576-b61da3f981a3)

![s14](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/f3eb2e3d-46b3-4749-bf34-8efce0dea7e1)

![s15](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/a82051e0-9ba5-4f3a-9175-05334e601d2a)

![s16](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/c36980fc-288e-43a8-8b05-a2767f32358a)

![s17](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/1d03b627-be10-4210-bdac-e9c63da42f27)

![s18](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/030ea31d-67d8-4fee-8cc2-9592958f0215)

![s19](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/0ddee718-072f-4d2c-b325-f36f58e48085)

![s20](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/c0057e0e-2fc2-4a73-8602-81830d81de5f)

![s21](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/5c7314c3-d54b-4f82-a216-054531a15f76)

![s22](https://github.com/SmritiManikand/Ex-04-Multivariate-Analysis/assets/113674204/97296cd1-7b11-4b1f-9295-eee086ec5af8)

# RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
