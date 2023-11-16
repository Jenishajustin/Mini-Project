# Mini Project
## AIM
To perform data analysis using various data analytic tools in the given dataset.
## EXPLANATION
Data analysis refers to the process of inspecting, cleaning, transforming, and interpreting data to discover valuable insights, draw conclusions, and support decision-making. A Data analysis has the ability to transform raw, available data into meaningful insights for your business and your decision-making. While there are several different ways of collecting and interpreting this data, most data-analysis processes follow the same six general steps.

1. Specify Data Requirements
2. Collect Data
3. Clean and Process the Data
4. Analyze the Data
5. Interpretation
6. Report
   
<img src="https://github.com/Jenishajustin/Mini-Project/assets/119405070/02877c93-a575-43c6-90e7-097062f664b4" height=450 width=475>

## ALGORITHM
### Step-1 
Import the necessary Python libraries.
### Step-2
Load the dataset using the Pandas library to read the dataset.
### Step-3
Store the dataset in another variable to protect the original data.
### Step-4
Perform data cleaning.
### Step-5
Remove outliers from the dataset for an efficient analysis.
### Step-6
Visualize the data using various data visualization tools.
### Step-7
Display the result.
## PROGRAM
```
Developed By: JENISHA.J
Reg.No: 212222230056
```
#### Import libraries
```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from scipy import stats
```
#### Load Dataset
```
df=pd.read_csv("/content/netflix.csv")
df
```
#### Store the dataset in another variable
```
af=pd.read_csv("/content/netflix.csv")
af
```
#### Check for the null values
```
af.isnull()
af.isnull().sum()
```
#### Replacing null values using mean() , median() and mode()
```
af['show_name']=af['show_name'].fillna(af['original_network'].mode()[0])
af
af['aired_on']=af['aired_on'].fillna(af['aired_on'].mode()[0])
af
af['original_network']=af['original_network'].fillna(af['original_network'].mode()[0])
af

af['rating']=af['rating'].fillna(af['rating'].mean())
af

af['watchers']=af['watchers'].fillna(af['watchers'].mean())
af
af['current_overall_rank']=af['current_overall_rank'].fillna(af['current_overall_rank'].median())
af
```
#### After Data Cleaning
```
af.isnull().sum()
```
#### Removal of Outliers
```
sns.boxplot(data=af)
plt.xticks(rotation=90)
sns.scatterplot(data=af)
q1=af['watchers'].quantile(0.25)
q1
q3=af['watchers'].quantile(0.75)
q3
iqr=q3-q1
iqr
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
af=af[((af['watchers']>=low) & (af['watchers']<=high))]
af
af.dropna()
af.head()
af['country'].value_counts()
af['original_network'].value_counts()
```
#### Ratings count using data visualization
```
sns.histplot(x="rating",data=af)
```
#### Shows the range of viewers in each network
```
stars=df.loc[:,["original_network","watchers"]]
stars=stars.groupby(by=["original_network"]).sum().sort_values(by="watchers")
sns.barplot(x=stars.index,y="watchers",data=stars)
plt.xticks(rotation=90)
plt.xlabel=("NETWORK")
plt.ylabel=("VIEWERS")
plt.show()

stars=df.loc[:,["original_network","rating"]]
stars=stars.groupby(by=["original_network"]).sum().sort_values(by="rating")
sns.barplot(x=stars.index,y="rating",data=stars)
plt.xticks(rotation=90)
plt.xlabel=("NETWORKS")
plt.ylabel=("RATINGS")
plt.show()

sns.violinplot(x='current_overall_rank',data=af)

sns.histplot(data=af,x='original_network',hue='country')
plt.xticks(rotation=90)
```
#### Heatmap
```
af.corr()
plt.subplots(figsize=(7,5))
sns.heatmap(af.corr(),annot=True)
```
## OUTPUT
![Screenshot 2023-11-16 220336](https://github.com/Jenishajustin/Mini-Project/assets/119405070/ff1a0286-2489-4e8d-9547-b334d0fe632a)
![Screenshot 2023-11-16 220427](https://github.com/Jenishajustin/Mini-Project/assets/119405070/4516c1c8-c5bf-44c6-86b5-b2695d5f3acd)
![Screenshot 2023-11-16 220504](https://github.com/Jenishajustin/Mini-Project/assets/119405070/f0000c88-e22a-4d00-b1cf-1145e6f48213)
![Screenshot 2023-11-16 220537](https://github.com/Jenishajustin/Mini-Project/assets/119405070/a8f16357-69e7-4386-be7d-d00f17fd50d0)
![Screenshot 2023-11-16 220559](https://github.com/Jenishajustin/Mini-Project/assets/119405070/64597a7e-e538-4d3f-bcdb-d201ce04a28d)
![Screenshot 2023-11-16 220626](https://github.com/Jenishajustin/Mini-Project/assets/119405070/1fdbb3ad-78fb-47f2-a830-6cffa9a4db96)
![Screenshot 2023-11-16 220659](https://github.com/Jenishajustin/Mini-Project/assets/119405070/681132de-5f86-4218-bcc4-a2a28e849d80)
![Screenshot 2023-11-16 220734](https://github.com/Jenishajustin/Mini-Project/assets/119405070/689b2adb-e1d2-4a91-b1d2-29bb916b6fbc)
![Screenshot 2023-11-16 220755](https://github.com/Jenishajustin/Mini-Project/assets/119405070/eb19baa7-e91e-4dd7-9880-8dd126e40dfb)
![Screenshot 2023-11-16 220821](https://github.com/Jenishajustin/Mini-Project/assets/119405070/502ce36a-2f49-4737-803e-aac92b968e4d)
![Screenshot 2023-11-16 220845](https://github.com/Jenishajustin/Mini-Project/assets/119405070/85a39367-5d74-4a74-bdfd-bba680ff4740)
![Screenshot 2023-11-16 220909](https://github.com/Jenishajustin/Mini-Project/assets/119405070/bd2e8223-54a1-4aa3-b892-8296fff9ef1b)
![Screenshot 2023-11-16 220930](https://github.com/Jenishajustin/Mini-Project/assets/119405070/0426be5b-ec3d-4ddb-8a64-d08c4f921061)
![Screenshot 2023-11-16 220953](https://github.com/Jenishajustin/Mini-Project/assets/119405070/a478236b-54f8-4af9-9147-38a55f70ac16)
![Screenshot 2023-11-16 221014](https://github.com/Jenishajustin/Mini-Project/assets/119405070/29b3ae6f-b2c4-41f6-9933-7f4b9a4ef96b)
![Screenshot 2023-11-16 221032](https://github.com/Jenishajustin/Mini-Project/assets/119405070/a85571bd-5bae-4028-bec7-06d045129ee6)
![Screenshot 2023-11-16 221114](https://github.com/Jenishajustin/Mini-Project/assets/119405070/20ecef7d-6d4e-4c3f-90f9-4de88ca2ac5b)
![Screenshot 2023-11-16 221144](https://github.com/Jenishajustin/Mini-Project/assets/119405070/dadaf209-7b22-4721-9d93-141d935ca8af)

## RESULT
Thus, the given dataset has been successfully analysed using different data analytic tools.
