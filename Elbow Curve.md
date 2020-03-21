# Elbow Curve

* The elbow curve is used to determine to optimal number of clusters `k` to use for the data. It plots the within-cluster sum of squares on the y-axis and the number of clusters on the x-axis.
* When `k -> N`, where `N` is the number of observations, `W(C) -> 0` since each point becomes a cluster.
* The optimal number of clusters is where a sharp decrease in `W(C)` is followed by a much smaller decrease in `W(C)`, hence an elbow on the curve, as shown below (`k=3`).

![](Images/Screen%20Shot%202020-02-17%20at%202.48.07%20PM.png)
