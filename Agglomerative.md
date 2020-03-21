# Agglomerative

* Algorithm:
    1. Represent each data point as a singleton cluster.
    2. Calculate and store the distance between every possible pairs of points, i.e., the distance matrix.
    3. Merge the two closest clusters (least dissimilar) into a single cluster.
    4. Update the distance matrix.
        * Reducing computational cost: suppose A and B were merged into a cluster in the previous step. If in the successive step, the cluster of A and B is closest to C, then: `D(AB, C) ≤ D(A, C) + D(B, C)` by the triangle inequality.
    5. Repeat steps 2-4 until only one cluster remains.
* There are three common ways in which dissimilarity is measured, ::single-linkage::, ::complete-linkage::, and ::average-linkage::.
    * Let `G` and `H` be two distinct clusters.
    * The dissimilarity `d(G, H)` between `G` and `H` is computed from the set of pairwise observation dissimilarities `d_{ii'}`, where one member of the pair `i` is in `G` and the other `i'` is in `H`.

![](Images/Screen%20Shot%202020-02-17%20at%205.19.50%20PM.png)

----

### Single-Linkage

* Single-linkage agglomerative clustering takes the intergroup dissimilarity to be the ::closest (least dissimilar) pair:: (least common multiple).
* `d_{SL}(G, H) = (i∈G, i'∈H) min d_{ii'}`.
* Tends to ::violate the "compactness" property:: of clusters, wherein observations within each cluster are similar to each other.
* Tends to produce clusters with ::very large diameters::.

----

### Complete-Linkage

* Complete-linkage agglomerative clustering takes the intergroup dissimilarity to be the ::furthest (most dissimilar) pair:: (greatest common divisor).
* `d_{CL}(G, H) = (i∈G, i'∈H) max d_{ii'}`.
* Tends to ::violate the "closeness":: property of clusters, wherein observations from different clusters are dissimilar from each other.
* Tends to produce ::relatively compact:: clusters that are ::relatively far apart::.

----

### Single vs. Complete Linkage

* The sine curves below demonstrate the differences in their ::definition:::
    * Points that are to the left and right of an observation (on the same curve) are closer to the observation than points that are either above or below the observation (on the other curve).
    * Clusters produced by SL are on the curve, i.e., points that are closest pairs.
    * Clusters produced by CL are on the same locations of different curves, i.e., points that are furthest pairs.
* The "bird" scatterplot demonstrates the ::tendencies:: of each method:
    * The large cluster produced by SL violate the "compactness" property as points in this cluster are very dissimilar.
    * Multiple clusters produced by CL violate the "closeness" property as points in these clusters are very similar to each other.

![](Images/Screen%20Shot%202020-02-17%20at%204.10.59%20PM.png)

----

### Average-Linkage

* Group-average clustering uses the average dissimilarity between groups, i.e.,
* `d_{AG}(G, H) = (i∈G)(i'∈H)∑∑d_{ii'} / (N_G * N_H)`, where `N` represents the number of observations within the cluster.
