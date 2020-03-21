# Decision Tree (决策树)

* [[Entropy (熵)]]
* [[Information Gain (信息增益)]]
* [[Gini Index]]
* CART
* ID3
* Regression Tree
* Pruning

----

### Context

* Decision tree is a greedy machine learning algorithm that builds a tree where each node represents a feature (attribute), each branch represents a decision (rule) and each leaf represents an outcome (categorical or continuous).
* Root node (根节点): the entire population or sample and this further gets divided into two or more homogeneous sets.
	* Splitting: the process of dividing a node into two or more sub-nodes.
	* Decision node (非叶子节点 / 决策点): the node where a sub-node splits into further sub-nodes.
	* Leaf / terminal node (叶子节点): nodes with no children (no further split).
	* Pruning (剪枝): the process by which to reduce the size of decision tree by removing nodes (opposite of splitting).
	* Branch / sub-tree: a subsection of a decision tree.
	* Parent and child node: a node that is divided into sub-nodes is called parent node of the sub-nodes, whereas the sub-nodes are the child nodes.

----

### CART

* (C)lassification (A)nd (R)egression (T)ree.
    1. Calculate the Gini index for all features in the data set.
    2. Split on the feature with the lowest  Gini index into _n_ branches, where _n_ is the number of unique values that the feature has.
    3. Calculate the Gini index for each subsequent node (unique value of the chosen feature), i.e., for each subset of `data[data[feature]==val_i]`.
    4. Repeat steps 2 and 3 until no possible splits exist.

----

### ID3

* (I)terative (D)ichotomiser 3.
    1. Calculate the entropy `H(S)` for the entire data set.
    2. Calculate the average information entropy `(t∈T)∑[p(t) * H(t)]` for all features in the data set.
    3. Calculate the information gain for all features in the data set.
    4. Split the feature with the highest information gain into _n_ branches, where _n_ is the number of unique values that the feature has.
    5. Calculate the information gain for each subsequent node.
    6. Repeat steps 2-5 until no possible splits exist.

----

### Regression Tree

* Our data consists of `p` inputs and a response, for each of `N` observations: that is, `(x_i,y_i)` for `i = 1,2,..., N`, with `x_i = (x_i1, x_i2,..., x_ip)`. 
* Suppose we have a partition into `M` regions `R_1, R_2,..., R_M`, and we model the response as a constant `c_m` (leaf) in each region, then: `f(x) = (m=1 to M)∑[c_m * I(x∈R_m)]`.
* We model `c_m` by minimizing the sum of squared residuals in `R_m` and get the following formula: `chat_m = (c_m) min (i=1 to N)∑[(y_i * f(x_i))--2] = ave(y_i|x_i∈R_m)`, i.e., the average value of `y_i` within `R_m`.
* To find the splitting variable `j` and the splitting point `s`, such that `R_1(j, s) = {X| X_j ≤ s}` and `R_2(j, s) = {X| X_j > s}`, we solve the following:
* `(j, s)min[(c_1)min[SSR_(x_i∈R_1)]+(c_2)min[SSR_(x_i∈R_2)]]`, i.e., minimizing the sum of squared within both `R_1` and `R_2`.
* For any choice `j` and `s`, the inner minimization is solved by:
* `chat_1 = ave(y_i|x_i∈R_1)` and `chat_2 = ave(y_i|x_i∈R_2)`.
* Therefore, the algorithm can be summed up as:
    * For `p=1` to `P`:
        * For `i=1` to `N`:
            * Set `s=x_i` such that the SSR for `R(p, s)` is minimized.
        * Set `j=p` such that the SSR for `R(j, s)` is minimized.

----

### Pruning

* Cost-complexity (weakest-link) pruning is a method to reduce the variance of a decision tree by reducing its number of leaves based on minimizing a metric called tree score.
* The tree score is defined as `SSR + α-T`, where `T` is the number of terminal nodes or leaves that the tree has, and `α` is a multiplier that needs to be tuned.
* Suppose we have a tree with N terminal nodes. We iteratively remove branches in the tree and it with the average value of its leaves, and calculate the tree score of the resulting smaller tree until N becomes 1.
* We select the tree with the lowest tree score as the final pruned tree.

----

### Resources

* [StatQuest: Decision Trees](https://www.youtube.com/watch?v=7VeUPuFGJHk)
* 	[StatQuest: Decision Trees, Part 2 * Feature Selection and Missing Data](https://www.youtube.com/watch?v=wpNl-JwwplA)
* [Regression Trees, Clearly Explained!!!](https://www.youtube.com/watch?v=g9c66TUylZ4)
* [How to Prune Regression Trees, Clearly Explained!!!](https://www.youtube.com/watch?v=D0efHEJsfHo)
