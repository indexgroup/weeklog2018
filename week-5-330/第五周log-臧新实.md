# 第五周工作日志

在这周初步的调查时空大数据方面的相关研究。

关于时空大数据，下面摘录了清华李建副教授的一些介绍：
>时空大数据有很多的种类，比如说GPS的定位数据，比如说网约车 ——滴滴、Uber的订单的数据，社会网络上的数据，更宏观的国民经济的数据，比如人口密度、人口迁徙的数据。这些数据的共同特点是它既有时间的属性也有空间的属性。时空大数据可以理解是一种带有空间相关性的时间序列。

>深度学习研究时空大数据是当前的研究热点。应用深度学习进行时空大数据挖掘，第一个挑战就是如何抓住时空的关联性。这里面涉及到几个问题：第一，你用什么样的学习框架，监督学习还是非监督学习，还有多任务学习、在线学习、增强学习……很多种方法，你用哪一种框架。这里并没有一个很成熟的做法，比如图像就用CNN；第二，你想用深度学习，什么样的网络结构比较好；第三，我刚才说了有很多的数据源，不同的数据源会产生不同的因子，我们如何构造一个网络，能够将这些不同质的因子综合起来，并且希望这个网络能够易于拓展，易于应用；第四，我们可能还要处理一些噪音很大，或者说数据缺失的问题。

>深度学习在时空大数据的四个经典应用:
**网约车供需的预测**
**出行时间的预测**
**商店选址**
**预测到访**


扫了几篇相关文献，这里记录两篇笔记。

## [1].	Wang, D., et al., When Will You Arrive? Estimating Travel Time Based on Deep Neural Networks, in AAAI Conference on Artificial Intelligence (AAAI). 2018.
文章用深度学习进行交通出行时间（轨迹时间）的预测。每条出行轨迹是GPS坐标序列，也即是一条具有空间相关性的时间序列。除了轨迹的时空特性，外部的因素也会有重要影响，包括Driver, week,weather，这些信息也作为轨迹的特性。

现有研究可以大概分为：局部分割预测（individual）与全局综合预测（collective)，前者将轨迹进行分段预测再综合，存在问题是段与段间复杂的连接:  road intersections, traffic lights, and
direction turns，而且存在涉误差累积问题。全局综合预测问题是轨迹的稀疏性。这篇文章的设计兼顾着这两点。

文章提出了DeepTTE（ Travel Time Estimation ）框架，分为三个部分，Spatio-temporal learning component, Attribute component, Multi-task learning component。

1) Attribute Component
使用Embedding method将每一个高维属性转化成低维向量
2) Spatio-temporal learning component:
使用“geo - conv”卷积，提取局部轨迹特征（feature map， spatial correlation）；

精巧之处在于how to apply ？一种思路（grid cut, 2D-CNN），问题：粒度太粗，作者使用了一个非线性映射，将二维坐标映射成16维（how???）。接着就是常规卷积（1D-CNN，NLP），另外人工辅助列，新添每一个local path的距离。

使用两层堆叠的LSTM，进行轨迹时间特性的提取(temporal correlation)；
3) Multi-task learning component
所谓的多任务指的是，既进行分段时间的learning, 又进行整体的learning。分段learning，使用fully-connected进行分类。难点是整体的learning的输入，文章使用 attention mechanism，也即是加权mean pooling（每一段非等权），来得到分类的”输入“。在这里”想当然式“分析很厉害hh。
另外还是用了 Residual fully-connected NN 进行分类。

最后是实验部分，已有一份成都的数据集和论文的代码。

## [2].	Yu, B., H. Yin and Z. Zhu, Spatio-Temporal Graph Convolutional Networks: A Deep Learning Framework for Traffic Forecasting. arXiv, 2018.
文章设计了Graph Convolutional networks来进行traffic forecasting (speed, volume, density)。 细节部分的Fourier & Chebyshev等数学运算较为深奥，待。

Mid-and-long term traffic prediction的研究分为两类，一类是dynamical model, 一类是data-driven methods。前者使用数学工具（一大堆公式）以及物理知识进行计算模拟，这存在的问题是计算复杂度，还有不合理的假设与简化。后者又分为classic statistical 和 machine learning，后前者以 autoregressive integrated moving average (ARIMA) 来进行统计学分析，存在的问题是时间序列的静止假设；后后者就包括者SVM，KNN， NN等。

对于DL，存在的问题是很难将时空特征综合提取。现有的研究比如1D-CNN + LSTM，FC-LSTM，存在的局限性在于使用CNN来进行general graph的特征提取，LSTM的难训和计算复杂（time-consuming iterations & complex gate mechanisms & slow response to dynamic changes）。


针对上面的局限性，这篇文章采用了purely convolutional structures，一是使用了 spectral graph convolutions（类似于时频域转换）来进行卷积-特征提取，二是使用了entire convolutional structures on time-axis 来提取时间特征。

现有的关于Convolutions on general Graph的研究分为两种基本方法，一种是expand the spatial definition of a convolution，一种是manipulate in the spectral domain。文章采用的是后者，细节部分的Fourier & Chebyshev等数学运算较为深奥，待。 

文章的神经网络结构是：顶层是两层堆叠的ST-Conv Block -> 里层是 sandwich structure: 两个Temporal Gate-Conv和一个Spatial Graph-Conv


文章提到了重要的一些“小东西”，residual connection, bottleneck strategy（sandwich结构即是）, layer normalization（防止过拟合）

最后，模型有了泛化的意义，问题的本质特征是对于structured time series的特征提取。
