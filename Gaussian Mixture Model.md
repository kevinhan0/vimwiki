# Gaussian Mixture Model

* The Gaussian mixture model has the form shown below. It is essentially a linear combination of Gaussian distributions with mean `μ_m` and covariance matrix `∑_m`.
    * The weights `α_m` sum up to 1.
* In general, mixture models can use ::any component densities in place of Gaussian::.
* Using Bayes' theorem, the mixture model provides an estimate of the probability that `rhat_im` that observation `i` belongs to component `m`.
    * The weight `α_m` is the ::prior:: of `m`.
    * The PDF `Φ(x_i;μ_m, ∑_m)` is the ::likelihood:: of `x_i` if the underlying distribution is `Φ(•)`
    * The denominator is the ::evidence::, i.e., all possibilities of `x_i` belonging to another class.
* The parameters, `α_m`, `μ_m`, and `∑_m` can be obtained using maximum likelihood estimation. However, this is numerically challenging due to the logarithm term inside the summation.
    * Therefore, we use the expectation-maximization (EM) algorithm as an alternative. 

![](Images/Screen%20Shot%202020-02-24%20at%206.06.16%20PM.png)

![](Images/Screen%20Shot%202020-02-24%20at%206.07.02%20PM.png)

![](Images/Screen%20Shot%202020-02-24%20at%206.07.11%20PM.png)

----

### Expectation-Maximization (EM) Algorithm

* Algorithm for two-component Gaussian mixture:
    1. Initialize the parameters `{μ_1, μ_2, σ_1^2, σ_2^2, π}`, where
        * `μ_1` and `μ_2` are two randomly chosen `y_i`.
        * `σ_1^2` and `σ_2^2` can be set equal to the ::overall sample variance::.
        * `π` can be started at the value 0.5, and the prior for the other component is simply `1-π`, which is also 0.5.
    2. **Expectation step**: compute the responsibilities, i.e., for each observation `x_i`, what is the probability that it belongs to 𝓝(μ_1, σ_1^2), and the probability that it belongs to 𝓝(μ_2, σ_2^2)?
        * Note: in the binary case, the probability for the other component is simply `1 - p`. However, when there are more than two components, we need to calculate this separately for each component.
        * Note: if we were to convert GM into a hard clustering algorithm, we would set the maximum probability to one and the rest to zero.
    3. **Maximization step**: compute the weighted means and variances.
        * Note: in the hard-clustering case, this would simply mean computing the mean and variances of all the points that belong to each component.
        * However, since in soft-clustering, each point "belongs" to every component, for each component, we calculate a weighted mean of how much each point "belongs" to the component.
        * Note: this is equivalent to shifting the cluster centroid in k-means clustering.
    4. Iterate steps 2 and 3 until convergence.

![](Images/Screen%20Shot%202020-02-24%20at%205.58.34%20PM.png)

----

### Comparison with k-Means Clustering

* Differences:
    1. k-Means clustering is a ::hard:: clustering algorithm, that is, each observation is assigned to ::one and only one:: cluster, whereas GM is a ::soft:: clustering algorithm, that is, each observation is assigned a ::probability of membership:: to each cluster.
        * A threshold is needed for a clearcut cluster assignment for GM.
    2. The "distance" metric (covariance matrix and prior) changes for GM in each iteration. GM and k-Means clustering would have the ::same outcome if we fix the covariance matrix and the prior::.
    3. There isn't an elbow curve or silhouette score method to select the best number of components.
* Similarities:
    1. Sensitive to changes in starting point.
    2. Local optima rather than global optima.

----

### Resources

* [Gaussian Mixture Models for Clustering](https://www.youtube.com/watch?v=DODphRRL79c)
* [Victor Lavrenko: Mixture Model Playlist](https://www.youtube.com/watch?v=REypj2sy_5U&list=PLBv09BD7ez_4e9LtmK626Evn1ion6ynrt&index=1)

