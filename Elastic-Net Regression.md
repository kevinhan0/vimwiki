# Elastic-Net Regression

* Elastic-net regression combines both ridge and lasso regression, i.e., elastic-net coefficients minimize the following:
    * `ß^{elastic} = (ß)argmin{((i=1 to N)∑[y_i - ß_0 - (j=1 to p)∑[x_ij * ß_j]])^2 + λ_1(j=1 to p)∑|ß_j| + λ_2(j=1 to p)∑ß_j^2}`.
* That is, both L1 and L2 regularization.

----

### Resources

* [Regularization Part 3: Elastic Net Regression](https://www.youtube.com/watch?v=1dKRdX9bfIo)
