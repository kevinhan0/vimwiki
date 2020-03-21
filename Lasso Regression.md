
### Lasso Regression

* One major difference between lasso and ridge regression is that because of the L1 regularization, lasso coefficients can be zero whereas ridge coefficients can only infinitesimally approach zero.
* `ß^{lasso} = (ß)argmin{((i=1 to N)∑[y_i - ß_0 - (j=1 to p)∑[x_ij * ß_j]])^2 + λ(j=1 to p)∑|ß_j|}`.
* Equivalently, `ß^{lasso} = (ß)argmin{SSR}` subject to the constraint, `(j=1 to p)∑|ß_j| ≤ t`.

----

### Resources

* [Regularization Part 2: Lasso Regression](https://www.youtube.com/watch?v=NGf0voTMlcs)
