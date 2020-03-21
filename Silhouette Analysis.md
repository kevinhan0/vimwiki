# Silhouette Analysis

* The silhouette analysis is another method by which the optimal number of clusters can be found. The silhouette score is calculated as follows:
    1. Calculate the cluster cohesion `a_i` as the average distance between a sample `x_i` and all other points in the cluster.
    2. Calculate the cluster separation `b_i` from the next closest cluster as the average distance between the sample `x_i` and all other samples in that cluster.
    3. Calculate the silhouette score `s_i=(b_i-a_i)/max{b_i,a_i}` , where `s_i∈[-1, 1]`.
* The smaller `a_i` is, the more similar points are within each cluster. On the other hand, the greater `b_i` is, the more dissimilar points within different clusters are to each other.
    * Thus, the ideal silhouette score is 1, where `b_i >> a_i`.
* [Selecting the number of clusters with silhouette analysis on KMeans clustering](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html#sphx-glr-auto-examples-cluster-plot-kmeans-silhouette-analysis-py)

![](Images/Screen%20Shot%202020-02-17%20at%202.56.48%20PM.png)
