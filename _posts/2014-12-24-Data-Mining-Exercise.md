---
layout: post
title: Data Mining Exercise
---

## Introduction

This is an exercise project to fulfill the requirement of a data scientist job interview. The task is to conduct exploratory data analysis on a 72M CSV formatted dataset. The data set contains roughly 10k data points, with 561 numerical features, and are labelled into 6 categories. 

Below is a list of skills and tools I used in the exercise. 

Skills:

- Exploratory Data Analysis: _Pinciple Component Analysis (PCA)_.
- Classification: _KNN_, _Decision Tree_, _Random Forest_, _Support Vector Machine (SVM)_, _Neural Network_.
- Clustering: _K-means_, _Hierarchical Clustering_, _Spectral Clustering_. 
- Validation: _Precision/Recall_, _Rand Index_.

Tools and libraries: 

- __Python__:
    - [__scikit-learn__]() package for _Clustering_. 
- __R__:
    - [__class__](): _kNN_.
    - [__rpart__](): _Decision Tree_.
    - [__randomforest__](): _Random Forest_.
    - [__e1071__](): _Support Vector Machine (SVM)_.
    - [__nnet__](): _Neural Network_. 
    - [__shiny__](): _Data Visualization_.


## Exploratory Data Analysis and Preprocessing

To start with, the data contains 10299 observations, 561 features, each feature contains 561 N/A values. Two steps are taken as pre-process: firsst, the N/A values are smoothed to their feature's mean. Second, features' value are normalized to the range of [-1,1] so that the objective function works properly. The distribution of values ranges in [-1,1] so mean normalization is not used here. 

In order to have a quick understanding of the features and categories. Principle Component Analysis (PCA) is conducted on the data matrix. Results can be seen in TODO: __plot 1__. __plot 1__  shows the relation between features and labels. As the plot shows, feature comp1 seperates the dataset into two major components at the cut-off value of 0. Each components have 3 labels. comp1 and comp2 shows that data under each label roughly roughly follows 2d gaussian distributions.  

// Insert plot pca_comp1_comp2.pdf or plot app here. 


## Classification

Choosing which methods to use for classification depends on multiple factors. First, results from the preliminary data analysis show that many labels are not linearly seperable, so that means we need to choose non-linear classficiation methods, or linear classification methods with kernels. The dependent variables or labels are categorical, which suggests against regression methods.

### KNN

A popular non-linear classification is [K-nearest neighbors(KNN)](http://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm).  Since in our dataset there are more data points than features, it's feasible to start with 3NN. Here we examed the performance with Leave-One-Out-Fold-Cross-Validation. And 3NN gives a precision of 0.9657248. 

### Decision Tree

Next I used the [decision tree]() method. The benefits of using decision tree over KNN is that it only uses a small number of features to predict, so it's computational efficient. Also since it selects features to use based on how much information each feature provides, it assign weights on features by their importance. 

The plot below shows the relation between the size of tree and the relative error rate. The error rate improves slowly after 7 splits, and even slower after around 33 splits. So we prune the tree up until level 7. Examing the performance with 10-fold-cross vlaidation with 7 nodes gives a precision of 0.80766, with 33 nodes gives a precision of 0.949132. Results of the trees can be seen below.TODO: put plots here. 

### Random Forest

As can be seen from the decision tree results, shallow tree usually results in low percision. While deeper tree improves performace, it also consumes significantly more computational resources as the tree grows exponentailly. 

An alternative approache is to use ensemble methods. In the case of decision tree, the ensemble methods would be to use multiple shallow trees to vote on the results. 

The plot below shows the importance of features used. The Random forest built contains 500 trees, and achieved a precision of 97.5%. TODO: plot below.

### Support Vector Machine (SVM) 

Support vector machine (SVM) is another type of machine learning algorithm. TODO: add more here to describe the data. and reasoning to use SVM. 

Here we used randomly sampled 90% of data as training data, and the rest 10% as test data. Kernel-wise I used gaussian kernel. The SVM method results in an accuracy of .979. 

### Neural Network 

Neural Network is a layered percepton algorithm. Here we used the same training data and testing data as that of the SVM algorithm experiment. 

I built a 2-layer neural network, with 10 hidden units, and softmax tranformation function. After 10 iteration I evaluated the model on the testing data and results in an accuracy of 0.958. TODO: add reasoning. 

## Clustering

For the task of clustering, I choose to use Python's skit-learn package for performance reasons. 



## Validation and Summary

## Appendix
Code can be found at: 