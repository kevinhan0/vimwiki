# k-Nearest Neighbor
	* Algorithm:
		1. Compute all pairwise distances between two points in the data.
		2. To make an prediction on an observation, find the _k_-nearest neighbors to that point.
		3. For classification, use ::majority voting:: to decide the class label. For regression, use ::average:: to decide the value.
	* To ::break ties:: in majority voting, one can use any of the following three methods:
		* (A) Randomly select a class out of the majority classes.
		* (B) Use the class with the highest prior, i.e., class count.
		* (C) Use the 1-nearest neighbor's class label.
	* The decision boundary created by k-NN is a Voronoi diagram, in which a hyperplane is partitioned into ::non-overlapping regions::
		* Points at the boundary are equidistant to the region centers of the boundary.
	* _k_ is a hyperparameter that can only be found via cross-validation.
		* `k -> ∞`: ::bias increases:: as k-NN becomes a priori classifier, wherein every prediction is the class with the highest count.
		* `k -> 0`: ::variance increases:: as algorithm fits perfectly to the training data.
	* Since k-NN fits using the distance metric, features need to be on the ::same scale:: before fitting.
	* Algorithm can be optimized using the following methods:
		* K-D tree
		* Inverted list
		* Fingerprinting
![](k-Nearest%20Neighbor/vd.png)

- - - -

### Advantages

	* Easy to update for online learning.
	* Non-parametric model and can fit complicated decision boundaries.
	* Very few assumptions on the data, and they are:
		* Implied by the distance metric.
		* Smoothness.

- - - -

### Disadvantages

	* ::Computationally expensive::, i.e., although computational cost at training time is `O(1)`, the computational cost at prediction time is `O(nxp)`, where `n` is the number of observations and `p` is the number of features.
		* Also need to store all training data.
	* ::Bad at extrapolation::, i.e., predicting outside the range of training data (boundary problem).
	* Sensitive to both ::class outliers:: and ::irrelevant features::.
	* Missing values need to be ::imputed::.

- - - -

### Distance Metrics

	* Hamming distance for ::categorical variables:::: `D(x, x') = (d)∑I(x_d≠x_d')`.
	* Minkowski distance (p-norm): `D(x, x') = [(d)∑|x_d - x_d'|^p]^(1/p)`.
		* `p=2` is the Euclidean distance, which has the following properties:
			* Symmetrical
			* Spherical
			* Treats all dimensions equally.
			* Sensitive to deviations in a single attribute, which is why scaling the features is important.
		* `p=1` is the Manhattan distance.
		* The figure below shows the isosurfaces for different values of `p`
	* Comparing the differences between `p=0.7` and `p=2` shows how distance metrics affect k-NN.
		* In the figure below, the dashed lines are the isosurface of `p=2` and the solid lines are the isosurface of `p=0.7`. Points on the same line have the same distance (radius) to A.
		* Euclidean distance considers points B and C to have the same effect on point A.
		* However, C varies in two features, whereas all the variation in B are in one feature.
		* `p=0.7` treats points D and C to have the same effect on A, whereas B is closer to A.
![](k-Nearest%20Neighbor/1500px-2D_unit_balls.svg.png)
![](k-Nearest%20Neighbor/Screen%20Shot%202020-02-26%20at%2012.01.59%20PM.png)

- - - -

### K-D Tree

	* K-D tree is not suitable for finding the nearest-neighbors in high-dimensional data.
	* The basic idea behind the algorithm is to build a tree in the following way:
		1. Randomly pick a dimension.
		2. Split on the median of that dimension.
		3. Repeat until convergence.
	* The computational complexity of k-d tree is approximately `O(nlog(n))`.
![](k-Nearest%20Neighbor/370px-Kdtree_2d.svg.png)![](k-Nearest%20Neighbor/370px-Tree_0001.svg.png)

- - - -

### Inverted List

	* The inverted list data structure is used on ::high-dimensional sparse and discrete:: data. It is usually used in the context of ::document classification::.
	* Unlike k-d tree, it is an ::exact:: method.
	* The basic idea behind the data structure is:
		1. For each word in the corpus, create a list of indices of the document that the word has appeared in.
		2. To find the nearest-neighbor of a new document, find and concatenate the list of indices for each word in the document. The top _k_ most frequent indices in the resulting list are the k-nearest documents.
![](k-Nearest%20Neighbor/Screen%20Shot%202020-02-26%20at%2012.55.00%20PM.png)

- - - -

### Comparison with Parzen-Rosenblatt Window

	* Each point `x_i` and its _k_-nearest neighbors create a region of space `R(x)` with ::size proportional to the distance between the point and its furthest neighbor::.
	* The size of this region is ::dynamic::, whereas in Parzen-Rosenblatt window, the size of this region is ::fixed:: for all points, as shown in the figure below.
	* We can derive an equation that gives us a posterior probability, i.e., `P(o|x) = 1/|R(x)| * (x_i∈R(x))∑I(y_i=o)`, where `o` is an observation.
		* This can be rewritten as `P(o|x) = ∑[I(y_i=o)*I(x_i∈R(x))] / ∑I(x_i∈R(x))`.
![](k-Nearest%20Neighbor/Screen%20Shot%202020-02-26%20at%2012.13.07%20PM.png)

- - - -

### Kernel Method

	* k-NN have hard decision boundaries. However, if there are a lot of points around the decision boundary, as shown below, small changes in the boundary can lead to drastically different predictions.
		* It would be nice if these points can be somehow included.
	* The main intuition behind applying a kernel is that ::weights should decrease or increase with distance:: rather than having a hard cut-off.
	* `P(o|x) = ∑[K(x_i, x)*y_i] / ∑K(x_i, x)`.
![](k-Nearest%20Neighbor/Screen%20Shot%202020-02-26%20at%2012.19.05%20PM.png)![](k-Nearest%20Neighbor/Screen%20Shot%202020-02-26%20at%2012.18.58%20PM.png)

- - - -

### Resources

	* [Victor Lavrenko: Nearest Neighbour Methods](https://www.youtube.com/watch?v=k_7gMp5wh5A&list=PLBv09BD7ez_68OwSB97WXyIOvvI5nqi-3&index=1)
	* [Regression: Kernel and Nearest Neighbor Approach](https://towardsdatascience.com/regression-kernel-and-nearest-neighbor-approach-6e27e5e955e7)

#machine_learning #supervised