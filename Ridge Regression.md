
# Ridge Regression

* Ridge regression shrinks the regression coefficients by imposing a penalty on their size.
* The ridge coefficients minimize a penalized residual sum of squares:
    * `ß^{ridge} = (ß)argmin{((i=1 to N)∑[y_i - ß_0 - (j=1 to p)∑[x_ij * ß_j]])^2 + λ(j=1 to p)∑ß_j^2}`.
    * Equivalently, `ß^{ridge} = (ß)argmin{SSR}` subject to the constraint, `(j=1 to p)∑ß_j^2 ≤ t`.
* By imposing a size constraint on the coefficients, ridge regression is good at handling data that have many correlated variables.

----

### Resources

* [Regularization Part 1: Ridge Regression](https://www.youtube.com/watch?v=Q81RR3yKn30)
