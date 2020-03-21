# Random Forest (随机森林)

* Algorithm:
1. For `b=1` to `B`:
    * ::(A):: Draw a bootstrap sample `Z*` of size `N` from the training data.
    * ::(B):: Grow a random-forest tree `T_b` to the bootstrapped data, by recursively repeating the following steps for each terminal node of the tree, until the minimum node size `n_min` is reached.
        * **(i)** Select `m` variables at random from the `p` variables.
        * **(ii)** Pick the best variable/split-point among the `m`.
        * **(iii)** Split the node into two daughter nodes.
    * Note: in simplest terms, we use a special technique to build the tree, i.e., we use a different set of randomly selected features for each level of the tree.
2. Output the ensemble of trees `(b=1 to B) {T_b}`.
3. To make a new prediction:
    * ::Regression:: Use the average of the predictions from the trees.
    * ::Classification:: Majority vote.

----

### Properties

* Bagging, parallel ensemble algorithm.
* Trees are identically distributed (i.d.), which means that the expectation of an average of `B` such trees is the same as the expectation of any of them.
* Thus, the bias of bagged trees is the same as that of the individual trees, and the only hope of improvement is through variance reduction.
* This is achieved by the random selection of the input variables during the tree-growing process, which reduces the correlation between the trees.
* Intuitively, reducing `m` will also achieve this.

----

### Proximity Plot

* A ::proximity matrix:: (`p x p`) measures the "similarity" between every possible pair of input variables.
* For every tree, any pair of out-of-bag (OOB) observations sharing a terminal node has their proximity increased by one.
* The proximity matrix is can be represented in two dimensions using multidimensional scaling, which allows us to make a proximity plot.
* The ::proximity plot:: gives an indication of which observations are effectively close together in the eye of the random forest estimator.
* Proximity plots for random forests often look very similar, irrespective of the data. They tend to have a star shape (see figures below), one arm per class, which is more pronounced the better the classification performance.
* Points that are closer to the conjoining of the arms are closer to the decision boundary, and vice versa, as can be seen in the plot on the right.

![](Images/Screen%20Shot%202020-02-11%20at%202.12.13%20PM.png)

----

### Missing Value Imputation

* Random Forest algorithm can handle missing values in both the training data as well as unseen data by:
    1. For each feature, initially fill its missing values with either the mean or mode of either the entire feature or the subset of the feature of the corresponding class that the missing values are in (for classification).
    2. Iteratively improve the quality of the imputation until the imputed values converge via the following steps:
        * Build a random forest using the previously imputed data.
        * Get the proximity matrix.
        * For each missing value, choose its corresponding column and the row with the highest sum of proximity value row-wise.
        * Impute the missing value as a weighted average of that row.

----

### Variable Importance

* At each split in each tree, the ::improvement in the split-criterion (Gini index or information gain) is the importance measure attributed to the splitting variable::, and is accumulated over all the trees in the forest separately for each variable.
* Random forest also use the OOB samples to construct a different variable-importance measure to measure the prediction strength of each variable.
* When the _b_th tree is grown, the OOB samples are passed down the tree, and the prediction accuracy is recorded. Then the values for the _j_th variable are randomly permuted in the OOB samples, and the accuracy is again computed.
* The ::decrease in accuracy:: as a result of the permuting is averaged over all trees, and is used as a measure of the importance of variable _j_ in the random forest.
* This measure leads to more uniform variable importance plots.

![](Images/Screen%20Shot%202020-02-11%20at%202.59.26%20PM.png)

----

### Resources

* [StatQuest: Random Forests Part 1 - Building, Using and Evaluating](https://www.youtube.com/watch?v=J4Wdy0Wc_xQ)
* [StatQuest: Random Forests Part 2: Missing data and clustering](https://www.youtube.com/watch?v=sQ870aTKqiM)

![](Images/Screen%20Shot%202020-02-11%20at%202.13.38%20PM.png)
