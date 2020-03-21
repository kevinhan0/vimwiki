# Radial Basis Function (RBF)

* The output of RBF can be interpreted as the relationship between `x` and `x'` in ::infinite dimensions::. The smaller the value, the "closer" the two points are in distance.
* Using the RBF as its kernel, the SVM classifies new examples based on weighted nearest neighbor, i.e., the label assigned to the examples are based on their "surrounding" points.
* `exp(-γ||x-x'||^2)` can be expressed as `exp[(-1/2)(x^2+x'^2)] * exp(xx')` when `γ=1/2`.
* If we expand `exp(xx')` as a Taylor series and multiply each term of the series by `exp[(-1/2)(x^2+x'^2)]`, we can express the RBF as `<BX, BX'>` , where `b_i = sqrt[exp[(-1/2)(x_i^2+x'_i^2)] / i!]`, where `i=1,2,..., N`, and `X=(x**0, x**1,..., x**N)`.
* This expression gives a better intuition behind the infinite dimensions as the dot product expands to `(xx', x^2x'^2, x^3x'^3,..., x^∞x'^∞)` approximately.
* The `γ` parameter defines how far the influence of a single training example reaches, with low values meaning "far" and high values meaning "close". The gamma parameters can be seen as the inverse of the radius of influence of samples selected by the model as support vectors.
