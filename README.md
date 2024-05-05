# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Data Preparation: Load and explore customer data.
2. Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
3. Apply K Means Clustering: Perform clustering on customer data.
4. Visualize Segmented Customers: Plot clustered data to visualize customer segments.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: S.Sajetha
RegisterNumber: 212223100049
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("C:/Users/admin/Downloads/printed pdfs/Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:,3:])
y_pred


data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/52529a7d-c082-40c3-90fc-218ed9428661)
![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/8f41a9d0-c4de-499b-8bad-ea396d84aef6)
![image](https://github.com/Sajetha13/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/138849316/a68efcfa-12a7-4a48-b663-7ef82f79400b)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
