# Huber Loss

* `L_δ(y, f(x)) = (1/2)(y - f(x))^2 if |y - f(x)| ≤ δ else δ|y - f(x)| - (1/2)δ^2`.
    * `δ` is a hyperparameter that controls what value outside the bounds of which is the data ::considered an outlier::, and hence applies "MAE" instead of MSE to calculate the loss.
* When there are two different distributions for `y`, one accounts for 10% of the data with mean significantly different than the other, MSE will skew the predictions towards the 10% distribution (mean), whereas MAE will ignore it completely (median).
    * Huber loss effectively deals with this problem by treating these two distributions separately.
* As `δ -> 0`, `L_δ -> L_{MAE}`. Conversely, as `δ -> ∞`, `L_δ -> L_{MSE}`.

![](Images/1*jxidxadWSMLvwLDZz2mycg.png)
