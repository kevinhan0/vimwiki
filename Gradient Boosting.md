# Gradient Boosting

* Input: training set `{(x_i, y_i)}(i=1 to N)`, a differentiable loss function `L(y, F(x))`, number of iterations `M`, and learning rate `ν`.
* Algorithm:
1. Initialize model with constant value: `F_0(x) = (γ)argmin(i=1 to N)∑L(y_i,γ)`, i.e., a single prediction `γ` for `y_i, ∀i` that minimizes the loss function.
2. For `m = 1` to `M`:
    * ::(A):: Compute the pseudo-residuals: `r_im = -[∂L(y_i, F(x_i)) / ∂F(x_i)] | F(x)=F_{m-1}(x), ∀i`. 
        * The `∂F(x_i)` part simply means with respect to the prediction, i.e., plugging in the predicted values from `F_{m-1}(x)` into the first derivative of the loss function.
        * The negative gradient (partial derivative) is where gradient boosting got its name.
    * ::(B):: Fit a regression tree to the targets `r_im` (the pseudo-residuals of `F_{m-1}(x)`) giving terminal nodes `R_jm`, `j=1,2,...,J_m`.
    * ::C:: For `j=1,2,...,J_m`, compute:
        * `γ_jm = (γ) argmin (x_i∈R_jm) ∑ L(y_i, F_{m-1}(x_i) + γ`.
        * Since there could be more than one leaf at each branch, the calculation of `y_jm` is essentially aggregating those values into a single value that minimizes the loss.
        * The value of `γ_jm` can be found by solving the partial differential equation: `∂L(y_i, F(x_i)) / ∂γ = 0` for `γ`.
        * If the partial derivative is difficult to find, we can use the partial derivative of the Taylor approximation instead.
    * ::D:: Update `F_m(x) = F_{m-1}(x) + ν*(j=1 to J_m)∑[γ_jm * I(x∈R_jm)]`
        * There could be multiple terminal nodes that contain `x_i`, therefore `(x∈R_jm)` includes all possibilities.
3. Output `F_M(x)`.

----

### Regression

* The commonly used loss function in gradient boosting regression is `L(y, F(x)) = (1/2)(i=1 to N)∑(y_i - F(x_i))^2`.
* Some nice properties of using this loss function are:
    * For (1), the initialized value for `F_0(x)` is simply `(1/N)∑y_i`, i.e., the average value of `y`.
    * For (2A), the pseudo-residual is simply `∑y_i-F(x)`.
    * For (2C), the optimal value for `γ_jm` is again the average of all values within terminal node `j`.

----

### Classification

* The commonly used loss function in gradient boosting binary classification is `L(y, F(x)) = -(i=1 to N)∑[y_i*log(p)+(1-y_i)*log(1-p)]`, where `p` is the probability of the positive class.
* Recall that the formula to convert probability to logarithmic odds is `log(odds) = log(p / (1-p))` and the vice versa is, `p = exp(log(odds)) / [1 + exp(log(odds))]`.
* The loss function can be rewritten as `L(y, F(x)) = -(i=1 to N)∑[y*log(odds) + log(1 + exp(log(odds)))]`.
* Some nice properties of using this loss function are:
    * For (1), the initialized value for `F_0(x)` is the  `log(p / (1-p))`.
    * For (2A), the pseudo-residual is `∑(F_{m-1}(x_i) - y_i)`.
    * For (2C), we use the derivative of the second order Taylor approximation, which when simplified, is equal to `∑[r_im / F_{m-1}(x_i)(1-F_{m-1}(x_i))]`.
* Some important caveats to notice:
    * Since `r_im` is interpreted as a probability, we build regression trees even though that this is a classification task.
    * Because of this, the outputs at the terminal nodes are also probabilities.
    * However, since `F_{m-1}(x)` is expressed in terms of `log(odds)`, we need to convert the outputs of the trees into `log(odds)`.

----

### Resources

* [Gradient Boost Part 1: Regression Main Ideas](https://www.youtube.com/watch?v=3CC4N4z3GJc)
* [Gradient Boost Part 2: Regression Details](https://www.youtube.com/watch?v=2xudPOBz-vs)
* [Gradient Boost Part 3: Classification](https://www.youtube.com/watch?v=jxuNLH5dXCs)
* [Gradient Boost Part 4: Classification Details](https://www.youtube.com/watch?v=StWY5QWMXCw)
* [Gradient Boosting machines, a tutorial](PDFs/fnbot-07-00021.pdf)

![](Images/Screen%20Shot%202020-02-11%20at%2011.44.00%20AM.png)

