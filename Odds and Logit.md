# Odds and Logit

* The ::odds for:: or ::odds of:: some event reflect the likelihood that the event will take place, while ::odds against:: reflect the likelihood that it will not.
* The odds of an event A is calculated as the ratio of the number of occurrences of A divided by the number of occurrences of not A, e.g.,
    * In a total of 8 games played, player A won 5 games and lost 3. The odds for player A winning is 5:3 = 1.67 while the odds against player A winning is 3:5 = 0.6.
    * Probability is different from odds in the sense that in calculating the probability of A winning, the denominator is the total number of games played, i.e., P(A) = 5 / (5 + 3) = 5/8.
* Since the odds for an unlikely event will always be between `[0, 1)`, and for that of a likely event will always be in `(1, ∞)`, it is difficult to compare odds since they are ::not on the same scale::.
* ::Logit::, or the logarithm of the odds, solves this problem.
    * Logit < 0: for unfavorable odds.
    * Logit > 0: for favorable odds.
    * Logit = 0: if equally likely.
