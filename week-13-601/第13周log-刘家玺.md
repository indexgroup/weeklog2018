本周一直在帮实验室申请今年的华为创新研究计划课题(HIRP), 我们申请的课题是用机器学习模型来学习数据库中的索引.

数据库索引主要是包含B树, hash-map和Bloom filters等方面. 其中B树用于range query, hash-map用于point query, bloom filter是用于existence query. 他们三种分别对应的机器学习问题是min max error回归问题, 分类问题.

我们还探讨了一些关于如何使用机器学习索引用于帮助数据库事务(如数据库查询)的方法.
