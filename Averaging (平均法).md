# Averaging (平均法)

----

### Averaging (简单平均法)
	
* For classification, average the predicted probabilities from multiple classifiers.
* For regression, average the predictions from multiple regressors.

----

### Weighted Average (加权平均法)

* `∑(w_i*yhat_i)` where `w_i` are weights derived from domain knowledge or model performance.
* 加权平均的权值都是::从训练数据中学习的::，由于真实情况下训练数据有缺失或者噪声，导致其得到的权值不一定真实可靠，所以从这个角度来说，::加权平均法不一定优于简单平均法。::其实有这样的一个思想：::对于差异不大的学习器，我们采用简单平均；差异较大的，我们采用加权平均。::
