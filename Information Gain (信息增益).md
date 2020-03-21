# Information Gain (信息增益)

* Information gain is the measure of the difference in entropy from before to after the set  `S`  is split on an attribute `A`. In other words, how much uncertainty in `S` was reduced after splitting set `S` on attribute `A` into set `T`.
    * Favors splits with smaller counts but higher number of unique values.
    * `IG(A,S) = H(S) * (t∈T)∑[p(t) * H(t)]`
        * `H(S)` : entropy of set `S`.
		* `T` : subset created by splitting set `S` by attribute `A` such that `S=(t∈T)⋃t`.
		* `p(t)` : the proportion of the number of elements in `t` to the number of elements in set `S`.
