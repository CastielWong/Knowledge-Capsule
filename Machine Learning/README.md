
This is the Knowledge Capsule for Machine Learning domains.

- [Statistics](#statistics)
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
    - [ROC](#roc)
    - [List \& Gains](#list--gains)
    - [Calibration Curve](#calibration-curve)
- [Machine Learning](#machine-learning)
  - [ML Pipeline](#ml-pipeline)
  - [Model](#model)
    - [Generative Model](#generative-model)
    - [Discriminative Model](#discriminative-model)
  - [Regression](#regression)
  - [Classification](#classification)
  - [Clustering](#clustering)
  - [Deep Learning](#deep-learning)
- [Article](#article)
- [Reference](#reference)


# Statistics

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

| y \ x | x1 | x2 | x3 | p(Y) |
| --- | --- | --- | --- | --- |
| y1 | 1/21 | 2/21 | 3/21 | 6/21 |
| y2 | 4/21 | 5/21 | 6/21 | 15/21 |
| p(X) | 5/21 | 7/21 | 9/21 | 21/21 |

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

| Mean | Formula | Example | Value |
| --- | --- | --- | --- |
| Arithmetic | (x<sub>1</sub> + ... + x<sub>n</sub>) / n | [1, 8, 8] | 17/3 = 85/15 |
| Harmonic | n / (1/x<sub>1</sub> + ... + 1/x<sub>n</sub>) | [1, 8, 8] | 12/5 = 36/15 |
| Geometric | (x<sub>1</sub> * ... * x<sub>n</sub>)^(1/n) | [1, 8, 8]] | 4 = 60/15 |

General:
- MAE (Mean Absolute Error): average of the absolute value of errors
- MSE (Mean Squared Error): average of the squared errors
- RMSE (Root Mean Absolute Error): root of MSE
- R-Squared: coefficient of determination, how much variance the model accounts for, between 0 and 1
- cross-entropy
- Log Loss (Logarithmic Loss): measures the performance of a classification model where the prediction input is a probability value between 0 and 1

### F-score
Normally, the F-score refers to F1-score, which is a way of combining the precision and recall of the model. It's defined as the harmonic mean of the model's precision and recall.

The adjusted F-score F<sub>β</sub> allows to weight prevision or recall more highly if one of either is more important:
- F<sub>β</sub> = (1 + β<sup>2</sup>) * (precision * recall) / (β<sup>2</sup> * precision + recall)
- When β is equal to 1, then we will have the standard F1-score: 2 * (precision * recall) / (precision + recall)
- Factor β indicates how much more important recall is than precision


## Confusion Matrix
A confusion matrix is used to describe the performance of a classification model.

| Actual \ Predicted | 1 | 0 | |
| --- | --- | --- | --- |
| 1 | TP | FN | Actual Positive |
| 0 | FP | TN | Actual Negative |
| | Predicted Positive | Predicted Negative |  |

- TP: True Positive (1 -> 1), the correctly predicted cases which are positive
- FN: False Negative (1 -> 0), the incorrectly predicted cases which are positive
- FP: False Positive (0 -> 1), the incorrectly predicted cases which are negative
- TN: True Negative (0 -> 0), the correctly predicted cases which are negative

| Indicator | Formula | Also Known as |
| --- | --- | --- |
| __Accuracy__      | = (TP + TN) / Total Cases |  |
| __Error Rate__    | = (FP + FN) / Total Cases |  |
| __Precision__     | = TP / Predicted Positive | __Positive Predicted Value__ |
| __Recall__        | = TP / Actual Positive    | __Sensitivity__, __TPR__ (True Positive Rate), Hit Rate |
| __Specificity__   | = TN / Actual Negative    |  |

### Precision
Precision calculates the ratio of the number of correctly predicted positive examples divided by the total number of positive examples that were predicted. Maximizing the precision will __minimize the false positives__.

### Recall
Recall is also known as __Sensitivity__, __True Positive Rate__ (TPR) and Hit Rate.

Recall predicts the ratio of the total number of correctly predicted positive examples divided by the total number of positive examples that could have been predicted. Maximizing recall will __minimize false negatives__.



## Charts
The better the model is expected to be if:
- the higher the __AUC__
- with less data, the higher the __Lift__ value
- with less data, the higher the __Gains__ value

### ROC
__ROC__, the Receiver Operator Characteristic curve, for whose value is the ratio of __True Positive Rate__ (ordinate) over __False Positive Rate__(abscissa):
- = True Positive Rate / False Positive Rate
- = (TP / Actual Positive) / (FP / Actual Negative)
- = (TP / Actual Positive) / (1 - TN / Actual Negative)
- = Sensitivity / (1 - Specificity)

AUC (Area Under the Curve), which is the Area Under the Receiver Operating Characteristic curve (AUROC).

To draw the ROC, the model predicted score and actual label for each item is needed. Below shows the sample, which is ordered by model score from highest to lowest:
| Item | Label | Score |
| --- | --- | --- |
|  1 | p | .9   |
|  2 | p | .8   |
|  3 | n | .7   |
|  4 | p | .6   |
|  5 | p | .55  |
|  6 | p | .54  |
|  7 | n | .53  |
|  8 | n | .52  |
|  9 | p | .51  |
| 10 | n | .505 |
| 11 | p | .4   |
| 12 | n | .39  |
| 13 | p | .38  |
| 14 | n | .37  |
| 15 | n | .36  |
| 16 | n | .35  |
| 17 | p | .34  |
| 18 | n | .33  |
| 19 | p | .30  |
| 20 | n | .1   |


Both of the __Actual Positive__ and __Actual Negative__ are 10. Assuming drawing ROC via the score for each decile, then:
| Score Threshold | TP | FP | TPR | FPR |
| --- | --: | --: | --- | --- |
| .9  |  1  |  0  | .10 | 0   |
| .8  |  2  |  0  | .10 | 0   |
| .7  |  2  |  1  | .20 | .10 |
| .6  |  3  |  1  | .30 | .10 |
| .5  |  6  |  4  | .60 | .40 |
| .4  |  7  |  4  | .70 | .40 |
| .3  | 10  |  9  | 1   | .90 |
| .2  | 10  |  9  | 1   | .90 |
| .1  | 10  | 10  | 1   | 1   |
| .0  | 10  | 10  | 1   | 1   |


### List & Gains
__Lift Chart__ = Predicted Rate / Average Rate, which shows how much better you can expect to do with the generated model compared to without a model in terms of accuracy.

__Gains Chart__  = Model Gains / Average Gains, which shows for each percentile of the data set, how much better the model is expected to perform compared against a random selection model.

To illustrate, below is the sample showing the difference between Lift Chart and Gains Chart:
| Data Size | Average Prediction | Model Prediction | Gains | Lift |
| --: | --: | --: | --: | --: |
| 10,000 | 1,000 | 2,000 | 2000 / 1000 = 2.00 | 2000 / 1000 = 2.00 |
| 20,000 | 2,000 | 3,900 | 3900 / 2000 = 1.95 | 1900 / 1000 = 1.90 |
| 30,000 | 3,000 | 4,500 | 4500 / 3000 = 1.50 | 600 / 1000 = 0.60 |
| 40,000 | 4,000 | 4,800 | 4800 / 4000 = 1.20 | 300 / 1000 = 0.30 |
| 50,000 | 5,000 | 5,000 | 5000 / 5000 = 1.00 | 200 / 1000 = 0.20 |

### Calibration Curve
Calibration Curve is also known as Reliability Graph:
- It is used to display the confidence of a predictive model
- If a classifier assigns a score of s to a population of instances, then fractionally about s of that population should truly be positive
- The abscissa axis is the probability range from 0 to 1, which is the probability the model predict for positive cases (Predicted Probability)
- The ordinate axis is the ratio of the actual positive case over the predicted positive cases in that probability (Actual Probability)
- A well-calibrated classifier would have all points on a diagonal line from (0,0) on the left to (1,1) on the right

To illustrate:
| Label | Predicted Probability |
| --- | --- |
| 0 | .2 |
| 0 | .1 |
| 0 | .3 |
| 0 | .2 |
| 1 | .2 |
| 1 | .2 |
| 0 | .9 |
| 1 | .7 |
| 1 | .7 |
| 1 | .5 |

| Predicted Probability | # of Positive | # of Negative |
| --- | --- | --- |
| .1 | 0 | 1 |
| .2 | 2 | 2 |
| .3 | 0 | 1 |
| .5 | 1 | 0 |
| .7 | 2 | 0 |
| .9 | 0 | 1 |

Hence, points in Calibration Curve are: (.1, 0), (.2, .5), (.3, 0), (.5, 1), (.7, 1), (.9, 0).



# Machine Learning
- Sigmoid
- Cost Function
- Gradient Descent: alters model predictions to decrease the error by using calculus
- Overfitting: In practice, overfitting is shown by a model having high accuracy on a training set, but low accuracy on the test set.
- Validation sets: are used alongside training set during training, rather than test sets which are used after training

## ML Pipeline
1. Problem Definition
2. Data Ingestion
3. Data Preparation
4. Data Segregation
5. Model Training
6. Candidate Model Evaluation
7. Model Deployment
8. Performance Monitoring



## Model
There are two types of model, Generative Model and Discriminative Model:
- 生成模型：
  - 学习得到联合概率分布 P(x,y)，即特征 x 和标记 y 共同出现的概率，然后求条件概率分布，能够学习到数据生成的机制
  - 所有 P(x,y) 的和为 1
- 判别模型：
  - 学习得到条件概率分布 P(y|x)，即在特征 x 出现的情况下标记 y 出现的概率
  - 所有 P(y|x) 的和为 1

Example 1: 确定一个羊是山羊还是绵羊
- 判别式模型：从历史数据中学习到模型，然后通过提取这只羊的特征来预测出这只羊是山羊的概率，是绵羊的概率
- 生成式模型：根据山羊的特征首先学习出一个山羊的模型，然后根据绵羊的特征学习出一个绵羊的模型，然后从这只羊中提取特征，放到山羊模型中看概率是多少，在放到绵羊模型中看概率是多少，哪个大就是哪个
- 判别式模型是根据一只羊的特征可以直接给出这只羊的概率（比如 Logistic Regression，这概率大于 0.5 时则为正例，否则为反例），而生成式模型是要都试一试，最大的概率的那个就是最后结果

Example 2:

| sample | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| x | 0 | 0 | 1 | 1 |
| y | 0 | 0 | 0 | 1 |

- Generative Model:

  |  | y = 0 | y = 1 |
  | --- | --- | --- |
  | x = 0 | 1/2 | 0 |
  | x = 1 | 1/4 | 1/4 |

- Discriminative Model:

  |  | y = 0 | y = 1 |
  | --- | --- | --- |
  | x = 0 | 1 | 0 |
  | x = 1 | 1/2 | 1/2 |

### Generative Model
The theoretical basis of Generative Model is based on statistics and Bayes' theorem.

- Naive Bayes
- Gaussian Mixture (GMM)
- Hidden Markov (HMM)

### Discriminative Model
- Perceptron
- K Nearest Neighbor (KNN)
- Decision Tree
- Logistic Regression
- Maximum Entropy
- Support Vector Machine (SVM)
- Boosting: like AdaBoost
- Conditional Random Field (CRF)
- Convolutional Neural Network (CNN)



## Regression
- Linear Regression
- Polynomial Regression



## Classification
- Logistic Regression
- Support Vector Machines (SVM)



## Clustering
- K-Means Clustering
- Spectral clustering



## Deep Learning
- Recurrent Neural Networks (RNN): provide the ability for models to better use recent historical data for predictions.
    - Long Short-Term Memory (LSTM)
    - Gated Recurrent Unit (GRU)
- Deep Neural Networks
    - Convolutional neural networks (CNN)


# Article
- 熵: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651640884&idx=3&sn=33c5193dc2039afe1309b5020c2ee7b9
- 数学之美番外篇：平凡而又神奇的贝叶斯方法: http://mindhacks.cn/2008/09/21/the-magical-bayesian-method/
- 逻辑回归：从入门到精通: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651640992&idx=1&sn=865a67e910e78ade51af745499a30cd7
- 12条可视化的秘密准则: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651647207&idx=1&sn=05803530428bb5ca6d65783b51d72ea7
- 十五个数据可视化的奇妙例子: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651642820&idx=1&sn=2cb294a4dbf9b2d3baeacc39e8a33792
- 谷歌首席决策工程师的一分钟入门指南: https://mp.weixin.qq.com/s/a-5YesGVuqzVUOghwrZKHw
- 数据库种类：https://mp.weixin.qq.com/s/lzm0_tZIpYW2yehEvJ9EeA
- Classification Model Pros and Cons: https://github.com/ctufts/Cheat_Sheets/wiki/Classification-Model-Pros-and-Cons


# Reference
- Imbalanced Classification With Python: https://machinelearningmastery.com/imbalanced-classification-with-python-7-day-mini-course/
- Understand Automated Machine Learning Results: https://docs.microsoft.com/en-us/azure/machine-learning/how-to-understand-automated-ml
- What does AUC stand for and what is it: https://stats.stackexchange.com/questions/132777/what-does-auc-stand-for-and-what-is-it
- What's Lift curve: https://www.quora.com/Whats-Lift-curve
- Classification probability calibration: https://www.kaggle.com/residentmario/notes-on-classification-probability-calibration
- Not yet another article on Machine Learning: https://towardsdatascience.com/not-yet-another-article-on-machine-learning-e67f8812ba86
- 分类模型的性能评估——以 SAS Logistic 回归为例:
  - (1) - 混淆矩阵: https://cosx.org/2008/12/measure-classification-model-performance-confusion-matrix/
  - (2) - ROC 和 AUC: https://cosx.org/2008/12/measure-classification-model-performance-roc-auc/
  - (3) - Lift 和 Gain: https://cosx.org/2009/02/measure-classification-model-performance-lift-gain
- ROC 曲线怎么画: https://www.zhihu.com/question/22844912
- Understanding Gain Chart and Lift Chart: https://www.geeksforgeeks.org/understanding-gain-chart-and-lift-chart/
- What is the F-score: https://deepai.org/machine-learning-glossary-and-terms/f-score
- 联合概率、边际概率、条件概率: https://blog.csdn.net/libing_zeng/article/details/74625849
- 生成模型 VS 判别模型 （含义、区别、对应经典算法）: https://blog.csdn.net/u010358304/article/details/79748153
- 机器学习“判定模型”和“生成模型”有什么区别: https://www.zhihu.com/question/20446337/answer/256466823
- 14 Different Types of Learning in Machine Learning: https://machinelearningmastery.com/types-of-learning-in-machine-learning/
