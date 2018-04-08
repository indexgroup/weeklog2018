本周研究了几篇和相似人群扩展(lookalike)相关的文献, 相似人群扩展主要采用三种模型来进行建模, 分别是Simple similarity-base M, Regression-Based model, Segment approximation-based model.

Simple similarity-based Model是直接考察任意两个用户(样本)之间的相似度, 是一种无监督学习的方法, 有点类似kNN, 注意到在kNN中, 如果k的值选取太小, 会是的偏差变小, 方差变大, 即过拟合. 如果k值选的比较大, 则会偏差增大, 方差减小.

Regression-Based model是一种有监督学习的方法, 其首先需要根据业务规则构造一些正样本和负样本, 然后把这个问题看成二分类问题, 进行有监督学习. 这里面比较关键的是如何构造样本, 如何进行特征的学习.

Segment approximation-based model是一种比较强依赖于业务规则的方法, 可能在企业中用的比较多, 但是由于其不是非常学术化, 所以可能在比赛中的指导意义不是很大.
