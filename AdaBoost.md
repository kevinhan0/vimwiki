# AdaBoost

* Algorithm:
1. Initialize the observation weights `w_i=1/N, i=1,2,...,N`.
2. For `m=1` to `M`:
    * ::(A):: Fit a "stump" `G_m(x)` to the training data using weights `w_i`.
    * ::(B):: Compute total error as: `err_m = [(i=1 to N)∑[w_i * I(y_i ≠ G_m(x_i))]] / [(i=1 to N)∑w_i]+ϵ`.
    * ::(C):: Compute `α_m = log[(1 - err_m) / err_m]`, where `α_m` is the weight (importance) assigned to "stump" `G_m(x)`.
    * ::(D):: `w_i <- w_i * exp[α_m * I(y_i ≠ G_m(x_i))], ∀i`, update the weights for each data point.
    * Misclassified observations have their weight scaled by a factor of `exp(α_m)`, and vice versa. 
    * In order to train the next stump using the weighted data, we either use a weighted Gini index or duplicate each data point by its weight ratio and then bootstrap the expanded dataset and use that as the training data.
3. Output `G(x) = sign[(m=1 to M)∑[α_m * G_m(x)]]`.

----

### Resources

	* [AdaBoost, Clearly Explained](https://www.youtube.com/watch?v=LsK-xG1cLYA)

![](Images/Screen%20Shot%202020-02-11%20at%203.55.48%20PM.png) 

![](Images/Screen%20Shot%202020-02-11%20at%204.09.14%20PM.png)
