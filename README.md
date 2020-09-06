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

In this clustering coding challenge I used the <b>DBSCAN (Density Based Spatial Clustering of Applications with Noise)</b> algorithm to determine the number of clusters in the dataset provided to us by the `ClusterPlot.csv` file. The main intution behind my approach is that DBSCAN automatically detects the number of clusters in the dataset using just the input data and parameters. 

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
The following libraries were used in coding the <b>DBSCAN clustering algorithm</b>
* SciKit Learn
* Pandas
* Numpy
* MatplotLib

## Solution
In this solution the DBSCAN model that is built in inside the sklearn.cluster package is utilized. The code was written in Jupyter Notebook. The DBSCAN algorithm works by determining whether one point is part of another cluster by using two specific input values : eps and min_pts. <br />
EPS: This is the maximum radius that forms the neighbourhood of one point. Every point inside this radius then becomes part of the cluster. 
Min_pts: Minimum number of points inside an eps-neighbourhood that are needed to form a cluster. <br />

The algorithm for the DBSCAN algorithm is as follows:
* Select an arbitary point P in the graph
* Point P's epsilon-neighbourhood points are determined
* If it is more than min_pts a cluster is started 
* If any other point becomes a part of this cluster then all the epsilon neighbours of that point become part of the same cluster too. 
* This process is continued until all points have been visited.
* Those points that do not get covered under a cluster then get marked as noise and are made outliers to the data
<br />
An important thing to determine in this type of solution is the epsilon value of the algorithm as a greater epsilon value means less clusters than normal and a smaller epsilon value means a lot of unecessary clusters. There is a set way to calculate the Epsilon value for every dataset and it is done by calculating the elbow knee point which is calculated as follows: 

* Determine the nearest neighbours to every point and finding their distances
* Plotting those distances in a graph
* Selecting the y-axis value corresponding to the most curvature of the graph. 

![Image of Graph from matplotlib](https://github.com/varuncj02/Coding-Challenge/blob/master/epsilon.png)
As you can see the curvature is the maximum at around 0.3 so the epsilon value of 0.3 was selected. From there it was simply making sure that right values were entered into the model. I choose min_pts as 3 because it is a 2 dimensional graph and the min_pts is generally set to (k+1) where k is the number of coordinates. 

## Result
Based on this model that was implemented the number of clusters determined in this `ClusterPlot.csv` dataset is 2 with the DBSCAN algorithm also detecting the outliers to the clusters marking them in purple.
![Clustering Result](https://github.com/varuncj02/Coding-Challenge/blob/master/clustering%20result.png)
This result is correct as the program calculated the clusters based on the neighbouring points and since there were two major areas of close neighbouring points the algorithm classified that as 2 datasets showing that there is some sort of similarity between the values. Every point that comes under one epsilon value is added and the epsilon point for this program was not selected arbitrarily but calculated using a proven neighbouring neighbours calculation method. Since all the parameters were selected based on mathematical reasoning I conclude that the output of 2 clusters is the correct answer to this clustering problem.

## Improvements
This algorithm is still rudimentary and multiple improvements can be made. One of the improvements I would like to add is to perform a hard clustering algorithm like K-Means and then comparing the clusters made by both to come up with a final answers on the number of clusters and how they are clustered. This algorithm requires a lot of memory with its memory run time being O(n * d) where d is the average number of neighbours of every point and could be solved by the more complex but memory effecient OPTICS algorithm. The third and final improvement is capping and flouring the variables at 1 and 99 percentile to reduce the outliers as clustering is very sensitive to outlier data points.


Signing out at 3:15 AM, California. I loved this challenge and I am sure I will come up with more improvements in my dreams.
## Sources
https://www.aaai.org/Papers/KDD/1996/KDD96-037.pdf
https://blog.dominodatalab.com/topology-and-density-based-clustering/
https://towardsdatascience.com/understanding-dbscan-algorithm-and-implementation-from-scratch-c256289479c5

