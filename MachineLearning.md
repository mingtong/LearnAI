## Machine Learning

- Machine Learning is the science (and art) of programming computers so they can learn from data.
- Machine Learning is the field of study that gives computers the ability to learn without being explicitly programmed.
- A computer program is said to learn from experience E with respect to some task T and some performance measure P, 
if its performance on T, as measured by P, improves with experience E.

### Machine Learning Type
  - Supervised(监督学习)
  - Unsupervised(非监督学习)
  - Semisupervised
  - Reinforcement
  - online
  - batch
  - instance-based
  - model-based
  
#### 监督学习
监督学习，训练数据包含目标结论(目标结论也叫“标签”)。
  - 监督学习的一个典型的任务是: 分类(Classification)，比如垃圾邮件过滤器，用很多垃圾邮件的案例来训练，然后学习如何分类新邮件。
  - 监督学习的另一个典型任务是: 回归(Regression)，预测(Predict)一个目标数值，比如二手车的价格，给出一组功能数据(里程数，车龄，品牌等)，这些数据叫做“预测器”(predictors)。
  训练系统时，需要提供很多二手车的案例数据，包括"预测器"和"标签(即价格)"。

回归算法和分类算法可以互用，逻辑回归(Logistic Regression)一般用于分类，因为它可以输出一个对应某个给定分类的概率值(比如20%概率为垃圾邮件)。
监督学习的重要算法有:
  - K最近邻算法(k-Nearest Neighbors)
  - 线性回归(Linear Regression)
  - 逻辑回归(Logistic Regression)
  - 支持向量机(Support Vector Machines (SVMs))
  - 决策树和随机森林(Decision Trees and Random Forests)
  - 神经网络(Neural networks)，(神经网络也可以是非监督学习)
  
#### 非监督学习
非监督学习，训练数据不包含目标结论(目标结论也叫“标签”)，系统不需要被教导如何学习。

非监督学习的重要算法有:
  - 聚类算法(Clustering)
    - k-Means 算法
    - 层次聚类算法(Hierarchical Cluster Analysis (HCA))
    - 最大期望算法(Expectation Maximization (EM))
  - 可视化和降维 (Visualization and dimensionality reduction)
    — 主成分分析(Principal Component Analysis (PCA))
    — 核心主成分分析(Kernel PCA)
    — 局部线性嵌入(Locally-Linear Embedding (LLE))
    — t-分布随机邻域嵌入算法(t-distributed Stochastic Neighbor Embedding (t-SNE))
  - 关联规则学习(Association rule learning)
    - Apriori 算法
    - Eclat 算法

- 比如有一些自己Blog的访客数据，聚类算法可以检测出相似的访客，算法在不提前知道访客属于哪个分类的情况下，可以找独立找出分类，
例如算法可以找出40%的访客是男性，并且在晚上访问自己的Blog，20%的访客是科幻小说迷，并且喜欢在周末访问自己的Blog。
使用层次聚类算法可以把这个分类拆分的更细。

- 可视化算法也是个好例子：给出大量复杂的无标签的数据，算法输出2D或3D的可以被绘制数据表现。
算法保存尽可能多的结构(比如在重合的可视化图中保持不同的聚类)，这样就可以理解数据如何组织并识别未知的模式。

- 一个降维的目标是：不丢失太多信息的前提下简化数据。
一种方式是，把几个想关的功能合并为一个，比如车的里程数与车龄非常相关，所以降维算法会把这些数据合并为一个数据：车的磨损。

- 另一个重要的任务是异常检测(Anomaly Detection)，
比如：检测信用卡的非正常交易以防止欺诈；捕捉生产缺陷，自动从数据集中移除异常值，以免进入另一个学习算法。
系统用正常数据训练，当检测新数据时可以判断是否正常。 

- 关联规则学习：目标是从大量数据中挖掘出感兴趣的关系。
比如运营一个超市时，在销售日志中可以发现发烤肉酱和土豆片的人通常还买牛排，这样就可以把这些东西的货架放置在一起。

#### 半监督学习
半监督学习，处理只有部分数据打标签的情况，一般是大量未标记的和少量标记的数据。
