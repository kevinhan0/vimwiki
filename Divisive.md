# Divisive

* Divisive clustering begin with the entire data set as a single cluster, and recursively divide one of the existing clusters into two daughter clusters at each iteration in a top-down fashion.
* The main advantage of this method over agglomerative is if we're interested in partitioning the data into a ::relatively small number of clusters::.
* Algorithm:
    1. Initialize `x_i` as `(i) argmax d(G, x_i)`, and set `H={x_i}`.
    2. While `n_clusters != N`:
        * For `i=1` to `N`:
            * While `d(G, x_i) - d(H, x_i) > 0`:
                * Move `(i) argmax d(G, x_i)` from set `G` into set `H`.
* Properties:
    * Depends on starting configuration.
    * Would not necessarily produce a splitting sequence that possesses the monotonicity property required by dendrograms.
