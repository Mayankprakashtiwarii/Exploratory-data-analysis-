# Exploratory-data-analysis-
The Superstore Sales Analysis project aims to analyze sales data from a retail store to gain insights into the store's performance and identify opportunities for growth. The project will involve using Python and various data science libraries to clean, analyze, and visualize the data.


code --------



import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

dataset = pd.read_excel("/content/Superstore_USA.xlsx")

dataset.head(5)

dataset.shape  # ((((((WILL DISPLAY ROW,COLUMN)))



# 1  MISSING VALUE ANALYSIS
dataset.isnull().sum()  # it will identify all missiing values in our data

# FILLING OF MISSING VALLUE IN PRODUCT BASE MARGIN
dataset['Product Base Margin'].fillna(dataset['Product Base Margin'].mean(),inplace=True)

# 1  MISSING VALUE ANALYSIS
dataset.isnull().sum()  # it will identify all missiing values in our data



#.  ORDER PRIORITY ANALYSIS
# Now analysis part
# we cannot analyse using row id so moving to order priority
dataset['Order Priority'].value_counts()

dataset['Order Priority'].unique()

dataset["Order Priority"] = dataset["Order Priority"].replace("Critical ","Critical")

dataset['Order Priority'].value_counts()

plt.figure(figsize=(5,4))
plt.title("Count of Order Priority")
sns.countplot(x="Order Priority",data= dataset)
plt.show()
plt.savefig("Count of Order Priority.jpeg")


##. SHIPPING MODE



dataset['Ship Mode'].value_counts()

plt.figure(figsize=(5,4))
x= dataset['Ship Mode'].value_counts().index
y= dataset['Ship Mode'].value_counts().values
plt.pie(y,labels=x,startangle=60,autopct='%0.2f%%')
plt.legend(loc=3)
plt.show()

plt.figure(figsize=(5,4))
  sns.countplot( x= "Ship Mode",data=dataset)
  plt.show()

## hue - differentiates
  plt.figure(figsize=(5,4))
  sns.countplot( x= "Ship Mode",data=dataset,hue="Product Category")
  plt.show()

## CUSTOMER SEGMENT

## hue - differentiates
plt.figure(figsize=(6,5))
sns.countplot(x="Customer Segment",data=dataset)
plt.show()

#. PRODUCT CATEGORY
plt.figure(figsize=(10,6))
sns.countplot(x="Product Category",data = dataset[dataset["Product Category"]=="Office Supplies"],hue="Product Sub-Category")
plt.show()

##. TO KNOW SALES BY YEAR
dataset.info()

dataset["Order Year"] = dataset['Order Date'].dt.year
dataset.info()

dataset['Order Year'].value_counts()

plt.figure(figsize=(6,5))
sns.countplot(x="Order Year",data=dataset)
plt.show()

##. TO KNOW PROFIT BY YEAR
sns.barplot(x="Product Category",y="Profit",data=dataset,estimator='sum')
plt.show

#### orders/sales  by state
dataset['State or Province'].value_counts()

#### top 5 orders/sales  by state
dataset['State or Province'].value_counts()[:5]

# to find product base margin/product

sns.barplot(x="Product Category",y="Product Base Margin",data=dataset,estimator='sum')
plt.show

