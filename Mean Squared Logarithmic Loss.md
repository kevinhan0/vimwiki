# Mean Squared Logarithmic Loss

* `L(y,f(x)) = (1/n)∑[log(f(x_i)+1) - log(y_i+1)]`.
* Properties:
    * Only cares about the ::relative difference:: between the prediction and the true value.
    * ::Penalizes underestimates more:: than overestimates.

![](Images/1*6pqV-PiVEECIocecXKEr7g.png)

----

### Resources

* [Mean squared logarithmic error (MSLE)](https://peltarion.com/knowledge-center/documentation/modeling-view/build-an-ai-model/loss-functions/mean-squared-logarithmic-error-(msle))
* [What’s the Difference Between RMSE and RMSLE?](https://medium.com/analytics-vidhya/root-mean-square-log-error-rmse-vs-rmlse-935c6cc1802a)

