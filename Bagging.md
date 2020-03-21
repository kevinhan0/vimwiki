# Bagging (套袋法)

* Bootstrapping (自助法) is a sampling technique in which subsets of observations are randomly drawn from the original dataset with replacement (emphasis on re-**placement** rather than **replace**-ment). 
* `scikit-learn` API provides options such as `bootstrap`, `bootstrap_features`, `max_samples`, and `max_features` to further customize the dimensions of the subsets.
* Bagging, or bootstrap aggregating, is a parallel ensemble method that trains weak learners on these subsets (bags) and combine the predictions via averaging.
* Reduces variance and increases bias.
* 主要通过样本的扰动来增加基学习器之间的多样性，因此Bagging的基学习器应为那些::对训练集十分敏感的不稳定学习算法（unstable learners）::，例如：神经网络与决策树等。

