# 第六周工作日志

在这周继续调查时空大数据方面的相关研究。

扫了AAAI近几年的相关文献，阅读了几篇。

下面摘录一篇：[1].	Jauhri, A., et al., Space-Time Graph Modeling of Ride Requests Based on Real-World Data, in AAAI Conference on Artificial Intelligence (AAAI). 2017.

文章研究的是挖掘ride-share的模式，也就是共享单车的在不同时间不同地区的使用频率，应用场景可以是对于需求大的地方设立公交车，文章称之为ride pool。

文章先对一个地区的骑行记录建立一个动态的图模型，ride request graphs (RRG)。RRG中的节点与边的构建方法是：
首先在空间上将地区划分成网格（100m x 100m），在时间上分时段（5min)，然后将一个时段内的骑行的起点和终点所在的网格，作为ride request graphs (RRG) 中的节点，相应的两个节点之间也就存在边，边权可以由节点间骑行request的数量而决定。

不过“边权”在这篇文章中没有过多设计，文章发现的结论是：RRG中边和节点的个数存在着称之为：densification power law的规律，也即是：

两个参数C和\alpha 可以算作每个城市的属性，这个原因可能是： clustered/connected communities, perhaps reflecting the small world effect .

后文一方面是关于Ride Request Poolability的定义与计算，以及人工模拟这个RRG图，未详看。
