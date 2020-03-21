# K-Means Clustering

* [[Elbow Curve]]
* [[Silhouette Analysis]]

----

### Context

* k-Means clustering is an iterative greedy descent clustering algorithm. It is a type of ::prototype-based:: clustering in the sense that its clusters are represented by prototypes, i.e., centroids.
* Contrary to Gaussian Mixture, k-Means clustering is a ::hard-clustering:: algorithm wherein each point gets assigned to one and only one cluster.
* Algorithm:
    * For `b=1` to `B`, where `B` is the number of iterations:
        1. Initialize k cluster centers as randomly selected points.
        2. For each observation:
            * ::(A):: Calculate the distance from the observation to each cluster center.
            * ::(B):: Assign the current observation to the cluster with the closest center.
        3. Calculate the mean of each cluster of observations.
        4. Assign the new means as the cluster centers.
        5. Repeat 2-4 until changes in the assignments are within a small tolerance threshold.
        6. Calculate `W(C_b) = (k=1 to K)∑[N_k] * (C_b(i)=k)∑||x_i - xbar_k||^2`, where `C_b` is cluster assignment for iteration `b`.
    * Choose the cluster assignment with the lowest within-point scatter, i.e., `(b) argmin W(C_b)`.

![](Images/Screen%20Shot%202020-02-17%20at%202.20.00%20PM.png)

![](Images/Screen%20Shot%202020-02-17%20at%202.22.23%20PM.png)

----

### Assumptions and Limitations

* k-Means clustering assumes that the inherit structure or natural grouping of the data to:
    * Have equal ::density::, ::variance::, and ::number:: of observations.
    * Be ::spherical:: in shape.
* Only applies for ::numerical:: data.
* ::To scale or not to scale:: Scaling the data for all attributes will cause each one of them to equally influence the clustering outcome. However, some attributes may be more relevant in segmenting or grouping the data than others, doing so might obscure the otherwise clear relationship, as shown below.
* As an iterative descent algorithm, k-Means clustering can only achieve ::local minimum:: at best. Increasing the number of iterations can help achieving a better result.
    * In the A3 dataset, 100 iterations are required to achieve the correct result. A 10 iteration result would look like the following figure.

![](Images/sphx_glr_plot_kmeans_assumptions_001.png)

![](Images/Screen%20Shot%202020-02-17%20at%202.09.05%20PM.png)

![](Images/BILDt.png)

----

### Vector Quantization Application

![](Images/Screen%20Shot%202020-02-17%20at%204.10.03%20PM.png)

