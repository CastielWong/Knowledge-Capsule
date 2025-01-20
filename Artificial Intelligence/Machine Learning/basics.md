
- [ML Pipeline](#ml-pipeline)
- [Model](#model)
  - [Generative Model](#generative-model)
  - [Discriminative Model](#discriminative-model)
- [Regression](#regression)
- [Classification](#classification)
- [Clustering](#clustering)
- [Deep Learning](#deep-learning)


Bias is the gap between predicted value and actual value, whereas variance describes
how dispersed the predicted values are.

- Sigmoid
- Cost Function
- Gradient Descent: alters model predictions to decrease the error by using calculus
- Overfitting: In practice, overfitting is shown by a model having high accuracy on a
training set, but low accuracy on the test set.
- Validation sets: are used alongside training set during training, rather than test
sets which are used after training


## ML Pipeline
There are 3 primary repositories: data, code, model.

1. Problem Definition
2. Data Ingestion
3. Data Preparation
4. Data Segregation
5. Model Training
6. Candidate Model Evaluation
7. Model Deployment
8. Performance Monitoring

| Process          | Input                                | Output                  |
|------------------|--------------------------------------|-------------------------|
| Data Preparation | processing code                      |                         |
| Model Build      | training data, training code         | candidate model         |
| Model Evaluation | candidate model, test data           | metrics, selected model |
| Model Selection  | selected model, metadata             | deploy-ready model      |
| Deployment       | deployed-ready model, inference code |                         |
| Monitoring       | code and model                       | production data         |


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
|--------|---|---|---|---|
| x      | 0 | 0 | 1 | 1 |
| y      | 0 | 0 | 0 | 1 |

- Generative Model:

  |       | y = 0 | y = 1 |
  |-------|-------|-------|
  | x = 0 | 1/2   | 0     |
  | x = 1 | 1/4   | 1/4   |

- Discriminative Model:

  |       | y = 0 | y = 1 |
  |-------|-------|-------|
  | x = 0 | 1     | 0     |
  | x = 1 | 1/2   | 1/2   |

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

The metrics for Classification are: Accuracy, Precision, Recall, F1, AUC-ROC


## Clustering
- K-Means Clustering
- Spectral clustering

The metrics for Classification are: Mean Squared Error, R Squared


## Deep Learning
- Recurrent Neural Networks (RNN): provide the ability for models to better use recent historical data for predictions.
    - Long Short-Term Memory (LSTM)
    - Gated Recurrent Unit (GRU)
- Deep Neural Networks
    - Convolutional neural networks (CNN)
