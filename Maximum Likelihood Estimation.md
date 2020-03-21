# Maximum Likelihood Estimation

* Maximum likelihood estimation entails finding the ::set of parameters for which the probability of the observed data is the greatest::. 
* The MLE equation is derived from the ::probability distribution of the dependent variable::.
    * In the binary class case, `y` follows a Bernoulli distribution, and in the multi-class case, `y` follows a Binomial distribution.
    * Bernoulli: `f(k;p) = p^k(1 - p)^k`.
    * Binomial: `f(k;n, p) = nCk * p^k * (1 - p)^(n-k)`.
* Thus, `(θ)argmax L(θ) = (i=1) ∏[p(x_i; θ)^(y_i) * (1 - p(x_i; θ))^(1 - y_i)]`, where
    * `θ` is the set of parameters `{ß_{10}, ß_1T, ß_{(K-1)0}, ß_{K-1}T}`.
    * Taking the logarithm makes it easier to find the derivative later `(i=1)∑[(y_i)log(p(x_i; θ)) + (1 - y_i)(log(1 - p(x_i; θ)))]`.
* The MLE equation is solved by the partial differential equation `∂L/∂θ = 0`, which is a transcendental equation that can only be solved numerically.
    * One such approach is the ::Newton–Raphson algorithm::, wherein the parameters are updated iteratively via,
    * `θ^{new} = θ^{old} - (∂^2L/∂θ∂θT)^-1 * (∂L/∂θ)`.
