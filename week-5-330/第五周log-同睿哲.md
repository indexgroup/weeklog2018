本周扫文两篇 
第一篇是《ZipG- A Memory-efficient Graph Store for Interactive Queries》
文中提出一个具有高吞吐量和低延时的图数据库。该数据库基于作者的以往发明的一个图数据库scihnit,
对图数据进行分布式和压缩（基于log-structured storge)，节省了空间。数据库的两大数据结构是EdgeFile
和NodeFile。这样的数据结构拥有时间和空间的平衡。

第二篇是《QIRANA- A Framework for Scalable Query Pricing》。当下的互联网世界，由于大数据时代的到来，
出现了一种新的角色，data brokers。具体来说，就是数据提供商（e.g. Facebook)和数据使用者（e.g. researchers)
的中间商。中间商应该如何为数据估价成为了一个重要的命题。文中列举了Price function的基本原则，提出了几种Price function，
并且通过寻找目标数据库的近邻，将一个NP问题近似化，取得了不错的效果。
