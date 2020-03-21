# Bayes' Theorem

* There are three ways to express Bayes' theorem:
    1. `P(y|x) = [P(x|y)*P(y)] / P(x)`, where `P(x) = P(x')P(x'|y_ + P(x)P(x|y)`.
    2. `π_k(y|x) = [f_k(x|y)π_k(y)] / f(x)`
    3. `posterior = priori * likelihood / evidence`.

----

### Priori

* The definition of priori is what can be known through an understanding of how certain things work, i.e. a hypothesis, ::rather than by observation::.
    * A previously held belief.
* `P(y)` is what we know to be the "population" probability of `y`, e.g., the probability of a person having breast cancer is `P(y)`, therefore the probability of the patient having breast cancer is also `P(y)`.
* `π_k(y)` is usually estimated from the observed probability in the training data. Here `k` is a specific value of `y`.

----

### Posterior

* The definition of posterior is what can be ::known by observation:: rather than through an understanding of how certain things work.
    * Updated belief in light of new information.
* `P(y|x)` is what we now know given the current data, e.g., given that the patient's test was positive, the probability of the patient having breast cancer is now `P(y|x)`.
* `π_k(y|x)` is what we want to maximize for `k` via maximum-likelihood estimation. This corresponds to how certain we are for the prediction.

----

### Likelihood

* Assuming that we already know the outcome, ::how **likely** are the data (or observations)::?
    * E.g., if we know that a patient has breast cancer, how likely is it that we get a negative test result? Although isn't impossible, it is probably unlikely.
* `P(x'|y) = P(x')*P(x',y)` can be interpreted as follows:
    * `P(x')`: Regardless of whether the patient has cancer, what is the probability that the test result is negative.
    * `P(x', y)`: What is the probability that the test result is negative **and** that the patient has cancer?
* `f_k(x|y)` is the ::conditional PDF:: of `x` when `y=k`.
    * E.g., if the underlying distribution of `x` is Bernoulli, then we can replace this function with `p^y * (1-p)^(1-y)`.

----

### Evidence

* `P(x)` encompasses ::all possible outcomes that can lead to the observation::.
    * E.g., if the test is positive, there are two possible outcomes. Either the test is correct and the patient has cancer, or the test is incorrect and the patient doesn't have cancer, i.e., `P(x|y)P(y)` and `P(x|y')P(y')` respectively.
* `f(x)` is the PDF of `x` for all possible values of `y`. It is usually represented as:
    * Discrete variable: `(k=1 to K)∑[f_k(x|y_k)π_k(y)]`.
    * Continuous variable: `∫f(x|y)f(y)dy`.

----

### Resources

* [Posterior Probability & the Posterior Distribution](https://www.statisticshowto.datasciencecentral.com/posterior-distribution-probability/)
<a href='PDFs/l06.pdf'>l06.pdf</a>
<a href='PDFs/nychka2a.pdf'>nychka2a.pdf</a>

