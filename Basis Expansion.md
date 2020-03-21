# Basis Expansion

* Basis expansion is a method that augments or replaces the vector of inputs  `X` with additional variables, which are transformations of `X`. This allows the existence of linear decision boundaries in `ℝ^m`  when such boundaries couldn't exist in `ℝ^n`, where `n<m`.
* Mathematically, `f(X) = (k=1 to K)∑[ß_k * h_k(X)]` where `h_k(X) : ℝ^n -> ℝ^m`, as opposed to the previously non-existent `f(X) = ∑[ß_i * x_i]` representation.
* Basis expansions can be computationally expensive. One such example is degree-d polynomial `h_m(X)`, in which the number of variables `n` grows exponentially with the degree of the polynomial, i.e., `O(n**d)`.

![](Support%20Vector%20Machine%20(%E6%94%AF%E6%8C%81%E5%90%91%E9%87%8F%E6%9C%BA)/Screen%20Shot%202020-02-09%20at%204.31.34%20PM.png)

