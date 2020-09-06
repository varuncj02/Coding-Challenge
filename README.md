# ACM Research Coding Challenge (Fall 2020)

## No Collaboration Policy

**You may not collaborate with anyone on this challenge.** You _are_ allowed to use Internet documentation. If you _do_ use existing code (either from Github, Stack Overflow, or other sources), **please cite your sources in the README**.

## Submission Procedure

Please follow the below instructions on how to submit your answers.

1. Create a **public** fork of this repo and name it `ACM-Research-Coding-Challenge`. To fork this repo, click the button on the top right and click the "Fork" button.
2. Clone the fork of the repo to your computer using . `git clone [the URL of your clone]`. You may need to install Git for this (Google it).
3. Complete the Challenge based on the instructions below.
4. Email the link of your repo to research@acmutd.co with the same email you used to submit your application. Be sure to include your name in the email.

## Question One

![Image of Cluster Plot](ClusterPlot.png)
<br/>
Given the following dataset in `ClusterPlot.csv`, determine the number of clusters by using any clustering algorithm. **You're allowed to use any Python library you want to implement this**, just document which ones you used in this README file. Try to complete this as soon as possible.

Regardless if you can or cannot answer the question, provide a short explanation of how you got your solution or how you think it can be solved in your README.md file.


## Summary

In this clustering coding challenge I used the DBSCAN (Density Based Spatial Clustering of Applications with Noise) algorithm to determine the number of clusters in the dataset provided to us by the `ClusterPlot.csv` file. The main intution behind my approach is that DBSCAN automatically detects the number of clusters in the dataset using just the input data and parameters. 

## Introduction
With a strong background in Data Structures and Algorithms in java, I spent this summer exploring python and its numpy and pandas library for data science. This is my first time working on a clustering problem so I had to do a little bit of research after I came across this challenge at 6:30 PM. 
Clustering is the process of partitioning or grouping a given set of patterns into disjoint clusters. 

## Approach
After doing some initial research it became clear that there are several types of clustering algorithms. Some of them are:
* Connectivity Models (Hard Clustering) - Hierarchial
* Centroid Models (Hard Clustering) - K Means
* Distributed Models (Soft Clustering) - Expectation Maximization
* Density Models (Soft Clustering) - DBSCAN / OPTICS
<br />
My initial idea was to implement a K-Means clustering algorithm as it is the most popular one. However, K-Means algorithm does not perform well when applied on non-globular clusters and it requires a pre-determined number of clusters as input from the users. An improvement on K-Means, Gaussian Mixture Model (GMM) ,could be used.However that also requires an input into the number of clusters required essentially making the model dependent on the users perception. Another factor that was considered was the choice of using either a Hard Clustering Model or a Soft clustering model. Soft clustering implies that a single point can be part of multiple clusters and is not restricted to one cluster unlike Hard clustering. That means soft clustering is a more versatile approach and this is the one that I have followed to determine the number of clusters. <br />
The Dataset that is supposed to be analyzed is a non-globular dataset and neightbourhood clustering algorithms like DBSCAN can effectively determine whether each point is closer to its neighbour in the same cluster or whether it is closer to its neighbouring data points in other clusters. Since DBSCAN is a density based model it scans and visits every point and can come up with arbitrarily shaped clusters without the need for the user inputting the number of clusters.

## Libraries Used


