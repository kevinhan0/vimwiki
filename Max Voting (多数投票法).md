# Max Voting (多数投票法)
	
* Generally used for binary or multi-class classification problems.
* Majority voting (绝多数投票法): final prediction must have votes from more than half the classifiers; otherwise, we reject the prediction.
* 绝多数投票法提供了拒绝选项，这::在可靠性要求很高的学习任务中是一个很好的机制。::
* Plurality voting (相对多数投票法): use the mode of class labels from multiple classifiers as the final prediction.
* Weighted voting (加权投票法): `∑(w_i*yhat_i)` where `w_i` are weights derived from domain knowledge or model performance.
* Soft voting (软投票): vote on the predicted probabilities instead.
* Hard voting (硬投票): vote on the predicted class labels.

```python
from sklearn.ensemble import VotingClassifier

lr = LogisticRegression(random_state=1)
dt = tree.DecisionTreeClassifier(random_state=1)

model = VotingClassifier(estimators=[('lr', lr), ('dt', dt)], voting='hard')
model.fit(x_train, y_train)
model.score(x_test, y_test)
```
