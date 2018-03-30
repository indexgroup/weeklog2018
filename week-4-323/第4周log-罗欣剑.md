#### 主要工作内容
---

1. 本周主要完成另一篇Journal论文FR-Index的收尾和完善工作，以及另一篇教学论文poster的撰写与投稿工作。
总体来说工作量不大。
2. 本周读了SIGMOD的几篇paper，虽然在distributed session里面，但是感觉跟我们研究的论文内容相关不大，在此不做进一步描述。

#### 给同学们的建议
---
1. 读论文时，要做好笔记工作。当我们阅读完大量文章之后，很容易把之前的内容忘记，这个时候翻看笔记对你大有裨益。
论文笔记宜简短，清楚明了，包括记录下当时的感受。每个人记的笔记，可以有自己的风格。贴上一篇我的paper log，供大家参考：

        Distributed Algorithms on Exact Personalized PageRank
        
        分布式算法，计算Personalized PageRank Vector (PPV)，考虑the load balance, the communication cost, and the computation cost of each machine三个方面。在查询时仅需要在每台机器和协调器之间通信一次。通信开销被bounded，负载均衡。实验在5个real数据集上进行。

        与PageRank模型不同的是，Personalized PageRank (PPR)模型允许用户定义一组偏好节点。在偏好节点集的限定下，PPR计算结果叫做PPV。

        挑战：1.计算复杂度太高，不适用于online应用。
        大多数应用选择计算PPV的近似值，以牺牲精确度来加速PPV的计算过程。
        2.设计一种高效且可扩展的分布式算法来在多台机器上并行计算PPV，该算法有较低的通信开销，并且可以实现负载均衡。图算法经常触发极大地网络通信开销，并且locality较差。

        Proposal：本文算法基于graph partitioning，计算的是PPV准确值。在一个基于协调器的非共享分布式计算平台上实现。

        Observation 1.可以将图分割成相似大小的不相邻的子图，来分布PPV的计算资源。本文提出一种graph partition based algorithm，简写GPA。
        Observation 2.如果将每个子图看做一个独立的图，然后使用GPA计算这个子图限定的local PPV，最后可以使用local PPV来构造global PPV。

        To the best of our knowledge, this is the first work that is able to compute exact PPVs efficiently in a distributed manner with reasonable space cost.

        Contributions:本文算法比power iteration方法快10~100倍，具有高精确度和负载均衡性，通信开销很低。
        实验数据集：采用了public real-life网络数据集—Email，Web，YouTube，PLD，Meetup。都是图数据。

2. 新同学初接触论文阅读工作，会碰到两个问题，就是`读不懂`和`读得慢`的问题。
- **读得慢**：同学们应该明白我们的母语不是英语，刚接触时读得慢很正常。想加快速度，唯有多读，熟能生巧，持之以恒，别无二法。
- **读不懂**：读不懂的论文也分两种，一种是非自己领域的文章，一种是自己领域的文章。对于非自己领域的文章，你只需要浅尝辄止，读一下摘要和简介，对这篇文章做了什么有一个大致的印象即可。
如果是自己领域的文章，读不懂时需要你找一下这篇文章后面的引用，一般来说年代越久远的文章，所用的知识也越简单，也就越容易读懂。你需要从头开始，把这个领域的知识树弄明白，那么以后读不懂这个问题也就迎刃而解了。
