
- [Probability](#probability)
  - [Probability Type](#probability-type)
  - [Event Type](#event-type)
  - [Bayesian](#bayesian)
- [Metric](#metric)
  - [F-score](#f-score)
- [Confusion Matrix](#confusion-matrix)
  - [Precision](#precision)
  - [Recall](#recall)
- [Charts](#charts)
  - [AUC-ROC](#auc-roc)
  - [List \& Gains](#list--gains)
  - [Calibration Curve](#calibration-curve)

## Probability
### Probability Type
- Marginal Probability: the probability of an event A occurring, i.e. P(A)
- Joint Probability: the probability of event A and event B occurring, i.e. P(A and B), P(A, B), or P(A ∩ B)
- Conditional Probability: the probability of event A occurring, given that event B occurs, i.e. P(A | B)
- Marginal Probability for event A =
  - for discrete: summation of __Conditional Probability__ of event A, given each event B
  - for continuous: integral calculus of __Conditional Probability__ of event A, given event B
- Joint Probability =
  - Conditional Probability * Marginal Probability
  - P(A, B) = P(A | B) * P(B)

Example:

| y \ x | x1   | x2   | x3   | p(Y)  |
|-------|------|------|------|-------|
| y1    | 1/21 | 2/21 | 3/21 | 6/21  |
| y2    | 4/21 | 5/21 | 6/21 | 15/21 |
| p(X)  | 5/21 | 7/21 | 9/21 | 21/21 |

- Marginal Probability
  - for Y: 6/21, 15/21
  - for X: 5/21, 7/21, 9/21
- Joint Probability: 1/21, 2/21, 3/21, 4/21, 5/21, 6/21
- Conditional Probability:
  - p(x1 | y1) = p(x1, y1) / p(y1) = 1 / 6
  - p(y1 | x1) = p(x1, y1) / p(x1) = 1 / 5
  - p(y2 | x3) = p(x3, y2) / p(y2) = 6 / 15

### Event Type
- Union         (A or B):     Additive Rule
  - Mutually Exclusive:         P(A ∪ B) = P(A) + P(B)
  - Not Mutually Exclusive:     P(A ∪ B) = P(A) + P(B) - P(A ∩ B)
- Intersection  (A and B):    Multiplicative Rule
  - Independent:                P(A ∩ B) = P(A) * P(B)
  - Dependent:                  P(A ∩ B) = P(A | B) * P(B) = P(B | A) * P(A)
- Complementary (not A):      Rule of Complement
  - :                           P(A<sup>c</sup>) = a - P(A)
- Conditional   (A given B):  Conditional Rule
  - Dependent:
    - P(A | B) = P(A ∩ B) / P(B)
    - P(B | A) = P(A ∩ B) / P(A)
  - Independent:
    - P(A | B) = P(A)
    - P(B | A) = P(B)

### Bayesian
- Prior Probability: from reason to result, P(result | reason)
- Posterior Probability: from result to reason, P(reason | result)


## Metric
There are different kinds of average in mathematics:
- Arithmetic Mean: is the sum of the array divided by n
- Harmonic Mean: is defined as the reciprocal of the arithmetic mean of the reciprocals of the array
- Geometric Mean: is obtained by multiplying them all together and then taking the nth root

| Mean       | Formula                                       | Example   | Value        |
|------------|-----------------------------------------------|-----------|--------------|
| Arithmetic | (x<sub>1</sub> + ... + x<sub>n</sub>) / n     | [1, 8, 8] | 17/3 = 85/15 |
| Harmonic   | n / (1/x<sub>1</sub> + ... + 1/x<sub>n</sub>) | [1, 8, 8] | 12/5 = 36/15 |
| Geometric  | (x<sub>1</sub> * ... * x<sub>n</sub>)^(1/n)   | [1, 8, 8] | 4 = 60/15    |

General:
- MAE (Mean Absolute Error): average of the absolute value of errors
- MSE (Mean Squared Error): average of the squared errors
- RMSE (Root Mean Absolute Error): root of MSE
- R-Squared: coefficient of determination, how much variance the model accounts for, between 0 and 1
- cross-entropy
- Log Loss (Logarithmic Loss): measures the performance of a classification model where
the prediction input is a probability value between 0 and 1

### F-score
Normally, the F-score refers to F1-score, which is a way of combining the precision and
recall of the model.
It's defined as the harmonic mean of the model's precision and recall.

The adjusted F-score F<sub>β</sub> allows to weight prevision or recall more highly if
one of either is more important:
- F<sub>β</sub> = (1 + β<sup>2</sup>) * (precision * recall) / (β<sup>2</sup> * precision + recall)
- When β is equal to 1, then we will have the standard F1-score:
2 * (precision * recall) / (precision + recall)
- Factor β indicates how much more important recall is than precision


## Confusion Matrix
A confusion matrix is used to describe the performance of a classification model.

| Actual \ Predicted | 1                  | 0                  |                 |
|--------------------|--------------------|--------------------|-----------------|
| 1                  | TP                 | FN                 | Actual Positive |
| 0                  | FP                 | TN                 | Actual Negative |
|                    | Predicted Positive | Predicted Negative |                 |

- TP: True Positive (1 -> 1), the correctly predicted cases which are positive
- FN: False Negative (1 -> 0), the incorrectly predicted cases which are positive
- FP: False Positive (0 -> 1), the incorrectly predicted cases which are negative
- TN: True Negative (0 -> 0), the correctly predicted cases which are negative

| Indicator       | Formula                   | Also Known as                                           |
|-----------------|---------------------------|---------------------------------------------------------|
| __Accuracy__    | = (TP + TN) / Total Cases |                                                         |
| __Error Rate__  | = (FP + FN) / Total Cases |                                                         |
| __Precision__   | = TP / Predicted Positive | __Positive Predicted Value__                            |
| __Recall__      | = TP / Actual Positive    | __Sensitivity__, __TPR__ (True Positive Rate), Hit Rate |
| __Specificity__ | = TN / Actual Negative    |                                                         |

### Precision
Precision calculates the ratio of the number of correctly predicted positive examples
divided by the total number of positive examples that were predicted.
Maximizing the precision will __minimize the false positives__.

### Recall
Recall is also known as __Sensitivity__, __True Positive Rate__ (TPR) and Hit Rate.

Recall predicts the ratio of the total number of correctly predicted positive examples
divided by the total number of positive examples that could have been predicted.
Maximizing recall will __minimize false negatives__.



## Charts
The better the model is expected to be if:
- the higher the __AUC__
- with less data, the higher the __Lift__ value
- with less data, the higher the __Gains__ value

### AUC-ROC
__ROC__, the Receiver Operating Characteristics curve, for whose value is the ratio of
__True Positive Rate__ (ordinate) over __False Positive Rate__(abscissa):
- = True Positive Rate / False Positive Rate
- = (TP / Actual Positive) / (FP / Actual Negative)
- = (TP / Actual Positive) / (1 - TN / Actual Negative)
- = Sensitivity / (1 - Specificity)

AUC (Area Under the Curve), which is the Area Under the Receiver Operating
Characteristic curve (AUROC).

To draw the ROC, the model predicted score and actual label for each item is needed.

Below shows the sample, which is ordered by model score from highest to lowest:
| Item | Label | Score |
|------|-------|-------|
| 1    | p     | .9    |
| 2    | p     | .8    |
| 3    | n     | .7    |
| 4    | p     | .6    |
| 5    | p     | .55   |
| 6    | p     | .54   |
| 7    | n     | .53   |
| 8    | n     | .52   |
| 9    | p     | .51   |
| 10   | n     | .505  |
| 11   | p     | .4    |
| 12   | n     | .39   |
| 13   | p     | .38   |
| 14   | n     | .37   |
| 15   | n     | .36   |
| 16   | n     | .35   |
| 17   | p     | .34   |
| 18   | n     | .33   |
| 19   | p     | .30   |
| 20   | n     | .1    |


Both of the __Actual Positive__ and __Actual Negative__ are 10.
Assuming drawing ROC via the score for each decile, then:
| Score Threshold | TP | FP | TPR | FPR |
|-----------------|---:|---:|-----|-----|
| .9              |  1 |  0 | .10 | 0   |
| .8              |  2 |  0 | .10 | 0   |
| .7              |  2 |  1 | .20 | .10 |
| .6              |  3 |  1 | .30 | .10 |
| .5              |  6 |  4 | .60 | .40 |
| .4              |  7 |  4 | .70 | .40 |
| .3              | 10 |  9 | 1   | .90 |
| .2              | 10 |  9 | 1   | .90 |
| .1              | 10 | 10 | 1   | 1   |
| .0              | 10 | 10 | 1   | 1   |


### List & Gains
__Lift Chart__ = Predicted Rate / Average Rate, which shows how much better you can
expect to do with the generated model compared to without a model in terms of accuracy.

__Gains Chart__  = Model Gains / Average Gains, which shows for each percentile of the
data set, how much better the model is expected to perform compared against a random
selection model.

To illustrate, below is the sample showing the difference between Lift Chart and Gains Chart:
| Data Size | Average Prediction | Model Prediction |              Gains |               Lift |
|----------:|-------------------:|-----------------:|-------------------:|-------------------:|
|    10,000 |              1,000 |            2,000 | 2000 / 1000 = 2.00 | 2000 / 1000 = 2.00 |
|    20,000 |              2,000 |            3,900 | 3900 / 2000 = 1.95 | 1900 / 1000 = 1.90 |
|    30,000 |              3,000 |            4,500 | 4500 / 3000 = 1.50 |  600 / 1000 = 0.60 |
|    40,000 |              4,000 |            4,800 | 4800 / 4000 = 1.20 |  300 / 1000 = 0.30 |
|    50,000 |              5,000 |            5,000 | 5000 / 5000 = 1.00 |  200 / 1000 = 0.20 |

### Calibration Curve
Calibration Curve is also known as Reliability Graph:
- It is used to display the confidence of a predictive model
- If a classifier assigns a score of _s_ to a population of instances, then
fractionally about _s_ of that population should truly be positive
- The abscissa axis is the probability range from 0 to 1, which is the probability the
model predict for positive cases (Predicted Probability)
- The ordinate axis is the ratio of the actual positive case over the predicted
positive cases in that probability (Actual Probability)
- A well-calibrated classifier would have all points on a diagonal line from (0,0) on
the left to (1,1) on the right

To illustrate:
| Label | Predicted Probability |
|-------|-----------------------|
| 0     | .2                    |
| 0     | .1                    |
| 0     | .3                    |
| 0     | .2                    |
| 1     | .2                    |
| 1     | .2                    |
| 0     | .9                    |
| 1     | .7                    |
| 1     | .7                    |
| 1     | .5                    |

| Predicted Probability | # of Positive | # of Negative |
|-----------------------|---------------|---------------|
| .1                    | 0             | 1             |
| .2                    | 2             | 2             |
| .3                    | 0             | 1             |
| .5                    | 1             | 0             |
| .7                    | 2             | 0             |
| .9                    | 0             | 1             |

Hence, points in Calibration Curve are: (.1, 0), (.2, .5), (.3, 0), (.5, 1), (.7, 1), (.9, 0).
