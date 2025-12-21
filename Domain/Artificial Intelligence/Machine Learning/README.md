- [Fitting](#fitting)
- [Article](#article)
- [Reference](#reference)

This is the Knowledge Capsule for Machine Learning domains.


ML is a subset of AI that focuses on developing algorithms and statistical models so
that computer systems can learn from data and make predictions or decisions without
being explicitly programmed.
ML models learn patterns and relationships from data rather than relying on hard-coded
rules for instructions.

- Supervised Learning
    - Classification
    - Regression
- Unsupervised Learning
    - Clustering
    - Dimensionality Reduction
- Reinforcement Learning

2 major components of deployable ML model:
- Model artifacts: the output of model training
- Inference code: the software that implements the model


ML Development Lifecycle:
1. Business goal identification
2. ML problem framing
3. Data processing
    - data collection
    - data preparation
        - data preprocessing
        - feature engineering
4. Model development (training, tuning, and evaluation)
5. Model deployment (inference and prediction)
6. Model monitoring
    - drift: data, concept (target)


## Fitting
- Bias: indicate how much the model is making erroneous assumptions about training data
- Variance: indicate how much the model is paying attention to noise in training data

| Bias / Variance |     low      |    high     |
|:---------------:|:------------:|:-----------:|
|       low       | well-fitted  | overfitting |
|      high       | underfitting |             |

Underfit models experience high bias—they give inaccurate results for both the training
data and test set.
On the other hand, overfit models experience high variance—they give accurate results
for the training set but not for the test set.
More model training results in less bias but variance can increase.

- Overfitting: when a model performs well on training data but fails to generalize to
new data
- Underfitting: when a model is too simple to capture the underlying patterns in data


## Article
- 熵: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651640884&idx=3&sn=33c5193dc2039afe1309b5020c2ee7b9
- 数学之美番外篇：平凡而又神奇的贝叶斯方法: http://mindhacks.cn/2008/09/21/the-magical-bayesian-method/
- 逻辑回归：从入门到精通: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651640992&idx=1&sn=865a67e910e78ade51af745499a30cd7
- 12条可视化的秘密准则: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651647207&idx=1&sn=05803530428bb5ca6d65783b51d72ea7
- 十五个数据可视化的奇妙例子: https://mp.weixin.qq.com/s?__biz=MjM5MTQzNzU2NA==&mid=2651642820&idx=1&sn=2cb294a4dbf9b2d3baeacc39e8a33792
- 谷歌首席决策工程师的一分钟入门指南: https://mp.weixin.qq.com/s/a-5YesGVuqzVUOghwrZKHw
- 数据库种类：https://mp.weixin.qq.com/s/lzm0_tZIpYW2yehEvJ9EeA
- Classification Model Pros and Cons: https://github.com/ctufts/Cheat_Sheets/wiki/Classification-Model-Pros-and-Cons


## Reference
- What Is Artificial Intelligence (AI): https://aws.amazon.com/what-is/artificial-intelligence/
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
