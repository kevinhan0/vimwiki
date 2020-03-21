# Mean Absolute Error

* `L(y,f(x)) = (1/n)*∑|y_i - f(x_i)|`.
* `∂L/∂f = 1 if f(x) > y, -1 if f(x) < y, UNF if f(x) = y`.
* Properties:
    * Robust to outliers.
    * Constant derivative makes it difficult to converge.
    * Should be paired with dynamic learning rate.
    * L1; median.

![](Images/1*JTC4ReFwSeAt3kvTLq1YoA.png)
