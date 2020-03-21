# Multinomial Naive Bayes Classifier

* A feature vector in the multinomial naive Bayes classifier is a histogram, with each `x_i` counting the ::number of times:: that event _i_ was observed.
* This is typically used in ::document classification::, with events (features) representing the occurrence of a word in a single document.
* `Pr(x_j | C_k)` is the multinomial distribution PDF, shown below.
* Thus, the multinomial naive Bayes classifier is linear in log-space.

![](Images/Screen%20Shot%202020-02-23%20at%2012.27.41%20PM.png)

![](Images/Screen%20Shot%202020-02-23%20at%2012.28.12%20PM.png)

