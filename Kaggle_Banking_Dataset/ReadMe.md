# About the Data

link: https://www.kaggle.com/rashmiranu/banking-dataset-classification

There has been a revenue decline in a Portuguese Bank and they would like to know what actions to take. After investigation, they found that 
the root cause was that their customers are not investing enough for long term deposits. So the bank would like to identify existing customers 
that have higher chance to subscribe for a long term deposit and focus marketing efforts on such customers.

# Outliers

An outlier is any data point which differs greatly from the rest of the observations in a dataset.

Outliers are of two types:
1. Univariate: A univariate outlier is a data point that consists of extreme values in a variable only.
2. Multivariate: Multivariate outlier is a combined unusual scpre on at least two variables.

Outliers can impact the results of our analysis and statistical modelling in a drastic way. But here is the caveat: outleirs aren't always a bad thing.
It is very important to understand this. Simply removing outliers from your data without considering how they will impact the results is a recipe for
disaster.

# Outlier Detection Techniques

## Interquartile Range (IQR)

IQR is a measure of statistical dispersion by dividing the data set into quartiles and is also called as Midspread or H-spread. It shows how the data is spread. The data is sorted in ascending order and then divided onto quartiles.
1. Q1 represents the 25th percentile of the data.
2. Q2 represents the 50th percentile of the data.
3. Q3 represents the 75th percentile of the data.

IQR = Q3 - Q1

IQR can be used to identify outliers by defining a new range on the sample values:
1. Upper Limit = Q3 + 1.5 * IQR
1. Lower Limit = Q1 - 1.5 * IQR

This method is also called Extreme Value Analysis.

## Angle Based Object Detection (ABOD)

Angles are more stable than distances in high dimensional spaces for example the popularity of cosine-based similarity measures for text data.

ABOD considers the relationship between each point and its neighbors. The variance of its weighted cosine scores to all the neighnors could be viewed as the outlying score. It measures the vareiance of angle spectrum.

Small ABOD score equals to Outliers, whereas high ABOD scores mean no outliers.

ABOD performs well on multi-dimensional data.

## Density Based Spatial Clustering of Applications with Noise (DBSCAN)

DBSCAN is a non-parametric, density-based outlier detection technique used for one-dimensional or multi-dimensional feature space.

DBSCAN has three important concepts:
1. Core Points: In order to understand the concept of the core points, we need to visit some of the hyperparameters used to define DBSCAN job. First hyperparameter is min_samples. This is simply the minimum number of core points needed in order to form a cluster. Second important hyperparameter is eps (epsilon). eps is the maximum distance betweeen the two samples for them to be considered as in the same cluster.
2. Border Points: They are in the same cluster as core points but much further away from the centre of the cluster.
3. Noise Points: Everything else is called the noise points, those are the data points that do not belong to any cluster. They can be anomalous or non-anomalous and they need further investigation.

Downside with this method is that the higher the dimension, the less accurate it becomes. Also estimating the right values of epsilon can be challenging.

## Isolation Forest

Isolation forest is a non-parametric method, binary decision trees based outlier detection technique used for one-dimensional or multi-dimensional feature space.

Outliers are isolated by creating decision trees over random features.

The random partitioning produces noticeable shorter paths for outliers since:
1. Fewer instances (of outliers) result in smaller partitions.
2. Distinguishable attribute values are more likely to be separated in early partitioning.

Hence, when a forest of random trees collectively produces shorter path lengths for some points, then they are highly likely to be outliers.

Isolation Forest explicitly isolates anomalies instead of profiling and constructing normal points and regions by assigning score to each data points. It takes advantage of the fact that anomalies are the minority data points and they have attribute values that are very different from those of normal instances.

This algorithm works great with very high dimensional datasets and it proved to be a very effective way ofdetecting anonalies.

Isolation forest algorithm requires some of the below parameters:
1. Number of estimators: It is the number of base estimators in the ensemble.
2. Contamination: It refers to the proportion of outliers in the dataset. It is quite sensitive parameter and in the most cases it is used as 0.015 or 0.02. The default value is 'auto'.
3. Max features: It refers to the number of features to draw from the dataset to train each base estimators.
4. Max sample: It is the number of samples to be drawn to train each base estimator. 

## One Class SVM

SVM algorithm developed initially for binary classification can be used for one-class classification. When modelling one class, the algorithm captures the density of the majority classs and classifies examples on the extremes of the density function as outliers. This modification of SVM is referred to as One-Class SVM.

Although SVM is classification algorithm and one-class SVM is also a classification algorithm, but it can be used to discover outliers in input data for both regression and classification datasets.

The class provides the 'nu' argument that specifies the approximate ratio of outliers in the dataset.


## Local Outlier Factor (LOF)

A simple approach to identify outliers is to locate those examples that are far from the other examples in the feature space. It can work well with all feature space with low dimensionality, although it can become less reliable as the number of features is increased.

LOF is a technique that attempts to harness the idea of nearest neighbors for outlier detection. Each data point is assigned a score of how isolated or how likely it is ti be an outlier based on the size of its local neighborhood. Those examples with largest score are more liekly to be outliers.

## Minimum Covariance Determinant (MCD)

If the input variables have a gaussian distribution, then simple methods can be used to detect outliers. For example, if the dataset has two input variables and both are gaussian, then the feature space forms a multi-dimensional gaussian and knowledge of this distribution can be used to identify values far from the distribution.

This approach can be generalised by defining a hypersphere (ellipsoid) that covers the normal data, and the data that falls outside this space is considered an outlier. An efficient implementation of this technique for multivariate data is known as the MCD.

It provides the 'contamination' argument that defines the expected ratio of outliers to be observed in practice. 

# Summary
