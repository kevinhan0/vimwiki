# Hierarchical Clustering

* [[Agglomerative]]
    - Single-Linkage
    - Complete-Linkage
    - Single vs. Complete Linkage
    - Average-Linkage
* [[Divisive]]

----

### Context

* Hierarchical clustering is an algorithm produces hierarchical representations in which the clusters at each level of the hierarchy are created by merging clusters at the next lower level.
    * At the lowest level, each cluster contains a single observation.
    * At the highest level, there is only one cluster containing all the data.
* There are two paradigms in hierarchical clustering: ::agglomerative (bottom-up):: and ::divisive (top-down)::.
* Each level of the hierarchy represents a particular grouping of the data into ::disjoint:: clusters of observations.
* The entire hierarchy represents an ::ordered sequence:: of such groupings, that is, the dissimilarity between merged clusters is monotone increasing from the bottom to the top.
    * Thus, the ::height:: of each node is proportional to the intergroup dissimilarity between its two daughters. This is called a ::dendrogram::.
* Cutting the dendrogram horizontally at a particular height allows the user to specify the number of clusters based on the context of the problem.

![](Images/Screen%20Shot%202020-02-17%20at%205.19.26%20PM.png)

----

### Assumptions and Limitations

* Different  dissimilarity metrics, such as single-linkage or complete-linkage, as well as any small changes in the data, can lead to quite different dendrograms.
* Hierarchical methods impose a hierarchical structure on the data, whether or not such structure actually exists in the data.

----

### Resources

* [Clustering (2): Hierarchical Agglomerative Clustering](https://www.youtube.com/watch?v=OcoE7JlbXvY)
* Divisive algorithm in plain text:

> It begins by placing all observations in a single cluster `G`. It then chooses that observation whose average dissimilarity from all the other observations is largest. This observation forms the first member of a second cluster `H`. At each successive step that observation in `G` whose average distance from those in `H`, minus that for the remaining observations in `G` is largest, is transferred to `H`. This continues until the corresponding difference in averages becomes negative. These two clusters represent the second level of the hierarchy. Each successive level is produced by applying this splitting procedure to one of the clusters at the previous level.   
