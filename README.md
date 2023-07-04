# Machine Learning Project: Predicting and Betting on the Group Stages of the 2022 FIFA World Cup
MIT 15.095 Machine Learning Under A Modern Optimisation Lens

## Problem Statement
The world cup is watched by half the world’s population, with cumulative betting valued at $155B for the 2018 FIFA World Cup in Russia.  However, the optimal betting strategy is often unclear for maximising returns due to the tradeoff between risk and reward. For example, betting on Argentina to win against Saudi Arabia will result in smaller winnings but a higher probability of winning (i.e., lower risk, lower reward). Conversely, betting on Saudi Arabia to beat Argentina will have higher returns but lower probability (i.e., higher risk, higher reward). Hence, for those seeking to make a profit by betting on the World Cup, what is the optimal betting strategy?

## Methodology & Approach
At the time of the project, the betting odds were only available for the group stages. Nonetheless, we sought to answer the aforementioned question through a betting framework that can be divided into two parts:

1. *Train ML models*: Random Forest, XGBoost, Light Gradient Boosting Machines, and Logistic Regression were used to predict the probabilities of each match outcome (win, draw, loss). These models were trained on a historical international match dataset consisting of ~4000 matches.

2. *Generate output probabilities that feed into the betting optimisation framework*: From the best performing model on the validation set, we use it to generate output probabilities p<sub>ij</sub> for the group stages that will be integrated into the betting optimisation framework. This would systematically determine which matches and outcomes are the best to bet on to maximise expected profit, based on a set of defined constraints.

We then benchmarked our betting framework against “God’s Eye,” whereby we assume perfect knowledge of each match outcome and bet the same amount accordingly.

## Results and Discussion
We selected XGBoost for generating output probabilities as it yielded the highest testing AUC, recall, precision, and F1-scores. To add explainability, we identified some of the most important features including: a team’s FIFA points, the midfield, attack, and defence scores, and etc. From the group stages, the overall profits were seen across all group stage:

| Total Bet Amount | Model (XGB) | God’s Eye |
|------------------|-------------|-----------|
| $5000            | $3,150      | $19,937.5 |

We also broke down the highest earning matches for both our model and God's Eye, summarised by the following table:

<table>
  <thead>
    <tr>
      <th colspan="2">Model (XGB)</th>
      <th colspan="2">God’s Eye</th>
    </tr>
    <tr>
      <th>Match</th>
      <th>Profit</th>
      <th>Match</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CAM v. BRA</td>
      <td>$1732.5</td>
      <td>ARG v. KSA</td>
      <td>$5880.0</td>
    </tr>
    <tr>
      <td>JPN v. CRC</td>
      <td>$1367.5</td>
      <td>CAM v. BRA</td>
      <td>$1732.5</td>
    </tr>
    <tr>
      <td>AUS v. DEN</td>
      <td>$1345.0</td>
      <td>JPN v. CRC</td>
      <td>$1367.5</td>
    </tr>
    <tr>
      <td>JPN v. ESP</td>
      <td>$1260.0</td>
      <td>AUS v. DEN</td>
      <td>$1345.0</td>
    </tr>
    <tr>
      <td>KOR v. POR</td>
      <td>$565.0</td>
      <td>GER v. JPN</td>
      <td>$1320.0</td>
    </tr>
  </tbody>
</table>

We also continued using the XGBoost model to predict the entire outcome of the World Cup: Round of 16, Quarter Finals, Semi Finals, and Finals (these are in the presentation). France was determined to be the eventual winner (we were close, even though we wanted Argentina to win it all!).

## Report
[15.095 Final Report](./ML-Report.pdf)

## Presentation
[15.095 Final Presentation](./ML-Presentation.pdf)

## Notebooks
- *01-modelling-and-predictions.ipynb*: Train, validate, and test various Machine Learning models to identify the best performing predictive model.
- *02-optimal-betting-framework.ipynb*: Formulated betting strategy or framework for the 2022 FIFA World Cup Group Stage matches (Julia, JuMP, Gurobi).
