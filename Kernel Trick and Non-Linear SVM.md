# Kernel Trick and Non-Linear SVM

* Non-linear SVM is a version of linear SVM in which  `X` is replaced with its basis expansion, i.e., `f(X) = [h(X)]T * ß + ß_0]`  as opposed to `f(X) = (X)T * ß + ß_0`.
* The Lagrange dual function, see figure below, allows us to rewrite `f(X)`  as `f(X) = (i=1 to N)∑[α_i * y_i * <h(x),h(x_i)>] + ß_0`.
* Since we only involve the `h(x)` via inner product, we need not specify the transformation `h(x)` at all, but require only the knowledge of a kernel function `K(x,x') = <h(x),h(x')>`. This is known as the ::kernel trick::.
* Commonly used kernels are:
    1. nth-degree polynomial: `K(x,x') = (1 + <x,x'>)^n`.
    2. Radial basis function: `K(x,x') = exp(-γ||x-x'||^2)`.
    3. Neural network: `K(x,x') = tanh(κ_1<x,x'> + κ_2)`.

![](Images/Screen%20Shot%202020-02-09%20at%204.18.05%20PM.png)
