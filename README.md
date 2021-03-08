# Google Ads Search Queries Clustering

## Motivation

The objective of the project is to find the best clustering models for Pay Per Click Search Query extracted from Google Analytics.
Once each Query click costs money, clustering and labeling the search queries using information about user behavior and ecommerce metrics will give us valuable insights that could reduce the cost of the campaign, allocating the budget better to improve the results.
More than have a good score, here we are going to look for meaningful cluster labels.

## Overview

* Tested 4 different cluster algos to choose and label the search queries with the most meaningful cluster model to help online businesses to reduce costs in their campaigns.
* The data was exported from Google Analytics.
* Preprocessed  the data before de modeling analysing the correlation of the features and normalizing them.  
* Specified the number of clusters using silhouette score for each of the cluster algos. 
* Was tested the following cluster algos: K Means, Spectral Clustering, Agglomerative Clustering, Gaussian Mixture.
 

## Resources Used
 **Python Version**: 3.7<br/>
 **Packages**: pandas, numpy, ploty, sklearn 
## Data Cleaning and Preprocessing 
The data imported from Google Analytics are complete and no columns have null values. So, the unique cleaning processes required is to set the numbers as float or int. 
Before applying the ML cluster models in our data set, I needed to choose the best features and preprocess the data.
 To choose the features, I analysed the correlation of the features using the corr() method and scatter plot.

<br>
<p align="center">
<img src="GAds-CLU-IMG/scatter-plot.png" width="500" > 
</p>


 After dropping the most correlated ones I ended with the 4 following features.


Sessions
AVG. Session Duration 
Bounce Rate 
Revenue

To make it easy for the algorithme identify the clusters and minimize the effect of outliers and noise in the data, I transformed to normal distribution. For that, I used numpy log and after that I used sklearn preprocessing package to scale the data.

<br>
<p align="center">
<img src="GAds-CLU-IMG/box-plot.png" width="500" > 
</p>


## Cluster algorithms

K Means, Spectral Clustering, Agglomerative Clustering and Gaussian Mixture required a specified number of clusters. To choose the number of clusters in the project I used the Silhouette Score method. After setting the number of clusters I did an analise plotting the clusters in a few different ways for each of the 4 algos.


### Size - Bar Plot 
I use go.Bar to visualize the size of the labels 

<br>
<p align="center">
<img src="GAds-CLU-IMG/barplott.png" width="500" > 
</p>

### Mean Of The Features - Polar Plot
Linear Polar Plot to understand the feature mean of the labels.

<br>
<p align="center">
<img src="GAds-CLU-IMG/polar-plot.png" width="500" > 
</p>

### 5 Features Representation - 3D Plot

To plot all features in one single chart, I used the px.scatter_3d. 

<br>
<p align="center">
<img src="GAds-CLU-IMG/3d-plot.png" width="500" > 
</p>

### Principal Component Analysis (PCA)
For a bidimensional visualization, I used the Principal Component Analysis (PCA)

<br>
<p align="center">
<img src="GAds-CLU-IMG/pca.png" width="500" > 
</p>



## Conclusion 

The clusters identified for the algorithm are very consistentes in saying that there are 4 groups of queries.
* Queries with rejection - SQ_Rejection.
* Queries that bring buyers - SQ_Buyer.
* Queries that bring interested users - SQ_Intereste.
* Queries that bring a lot of sessions of minimally interested users. - SQ_Sessions_Minimally_Interested.

However, I choose the **Gaussian Mixture** for some reasons.<br/>

* **SQ_Buyer-GM** - Shows the higher revenue and also, this cluster algo was the unique that created a group with all buyers in only one label.
* **SQ_Intereste_User-GM** - Shows the smaller Avg. Session Duration and the Higher Bounce rate, however the amount is good enough once the Avg. Session Duration mean of the df is 2.45. The size of that cluster is the larger when compared with the others algos too.
* **SQ_Rejection-GM** - Shows the higher Bounce rate and the smaller Avg Session Duration and Session mean per SQ.
* **SQ_Sessions_Minimally_Interested-GM** - Shows the smaller Session mean. However the Total sessions is the higher, also that algo have the second higher Avg. Session Duration.
<br/>
With that information, it is possible to set strategies to reduce rejection. It's also possible to bring more sessions to the web site and last but not least, improve the revenue optimizing the budget of the campaigns.
 
<br>
Author: Erick C. Varela <br/>
Date: 09/01/2020 
