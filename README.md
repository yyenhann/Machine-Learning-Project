# Machine Learning Project: Predicting and Betting on the Group Stages of the 2022 FIFA World Cup
MIT 15.095 Machine Learning Under A Modern Optimisation Lens

## Problem Statement
The world cup is watched by half the world’s population, with cumulative betting valued at $155B for the 2018 FIFA World Cup in Russia.  However, the optimal betting strategy is often unclear for maximising returns due to the tradeoff between risk and reward. For example, betting on Argentina to win against Saudi Arabia will result in smaller winnings but a higher probability of winning (i.e., lower risk, lower reward). Conversely, betting on Saudi Arabia to beat Argentina will have higher returns but lower probability (i.e., higher risk, higher reward). Hence, for those seeking to make a profit by betting on the World Cup, what is the optimal betting strategy?

## Methodology & Approach
At the time of the project, the betting odds were only available for the group stages. Nonetheless, we sought to answer the aforementioned question through a betting framework that can be divided into two parts:

1. *Train ML models*: Random Forest, XGBoost, Light Gradient Boosting Machines, and Logistic Regression were used to predict the probabilities of each match outcome (win, draw, loss). These models were trained on a historical international match dataset consisting of ~4000 matches.

2. *Generate output probabilities that feed into the betting optimisation framework*: From the best performing model on the validation set, we use it to generate output probabilities p<sub>ij</sub> for the group stages that will be integrated into the betting optimisation framework. This would systematically determine which matches and outcomes are the best to bet on to maximise expected profit, based on a set of defined constraints.

3. 
