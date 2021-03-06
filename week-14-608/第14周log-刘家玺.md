本周进行了ICDM的投稿, 在这篇论文中, 我们主要进行了使用多任务学习模型进行点击率和转化率预估的研究. 

点击率（CTR）和转换率（CVR）预测是在线广告的不同竞价模式中的关键挑战。目前的文献主要集中在通过建模各种特征学习来预测CTR或CVR。在本文中，我们考虑通过来自多任务学习（MTL）视角使用深度神经网络（DNN）来优化CTR和CVR预测。为了实现这一目标，我们提出了两个基本的MTL模型，特征共享和特征转移。特征共享模型公平对待两项任务，而特征转移则利用辅助任务来帮助学习主要任务。为了证明我们的MTL模型的有效性，并揭示点击和转换标签如何相互影响，我们对商业和人造数据集进行了三组消融实验。第一次初步实验是基于一个原始的商业数据，并且我们总结了一些关于制作更适用于MTL模型的同质数据的实践经验。第二组实验基于同质数据以及合成数据，一致的结果表明我们的MTL模型的优越性以及合成建模对印象转化路径的合理性。最后，为了回答关于CVR预测中两种广泛使用的方法之间差异的公开问题，我们最后设计了一个特殊的比较实验。根据三组消融实验，我们还提供了一个彻底的分析来描述背后的内在原因，并获得几个有意义的结论，这可能揭示了MTL在工业CTR / CVR预测中的应用。
