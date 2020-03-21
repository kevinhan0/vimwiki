# Boosting

* Boosting is a family of sequential ensemble algorithms that convert weak learners to strong learners by adding more weight to previously mislabeled predictions.
* Boosting creates additive models of the form `(m=1 to M)∑[α_m * G_m(x)]`, where `M` is the number of boosting rounds, `α_m` is the weight assigned to the weak learner, `G_m(x)`.
* There are two ways in which boosting can give more weight to data:
    1. Re-weighting: only applies for base learners which are designed to handle example weights; can lead to early stopping.
    2. Re-sampling: applies for any base learner.
* Reduces bias and increases variance.
* e.g. AdaBoost, Gradient Boosting Tree.

