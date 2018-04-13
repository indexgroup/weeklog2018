本周学习了一些和集成学习相关的内容, 具体总结如下

### 集成学习boosting和bagging

集成学习本质都是**加法模型**(additive model), $f(x)=\sum \alpha\_if\_i(x)$, 即由很多子模型的输出加起来的. 一般采用前向分步算法求解, 如求得第$m$个子模型$f\_m(x)$, 然后更新主模型, $f(x)=f\_{old}(x)+f\_m(x)$. 这里不同的损失函数对应着不同的算法.

### Adaboost

Adaboost采用的是指数损失函数, $L=\sum \exp(-y\_i(f\_{old}(x\_i)+f\_m(x\_i)))$, 在求第$m$个子模型$f\_m(x)$时, 可发现优化目标是找使得$\sum \exp(-y\_i(f\_{old}(x\_i))\cdot I(y\_i\neq f\_m(x\_i))$最小的$f\_m(x)$, 所以adaboost是把这个损失函数拆成两步, 一个是给每个样本赋予权重(即$\exp(-y\_i(f\_{old}(x\_i))$再加上归一化), 然后对于每个子模型都是最小化误差率(预测错误/总样本个数). 对于$\alpha\_m$, 也可以通过对损失求导得到.

Adaboost适用于分类问题, 原始流程如下: 每个样本赋予权重$\\{w\_i=1/N\\}$, 然后训练一个以最小化**带权的**误差率$e\_1$为目标的分类模型, 再根据$e\_1$更新样本权重$\\{w\_i\\}$和模型权重$\alpha_1$, 训练第二个模型.

### Boosting Tree(提升树)
提升树处理分类问题时, 和Adaboost是一样的; 处理回归问题时, 采用平方(均方)误差作为loss, 即$L=\frac{1}{2}\sum (y\_i-f\_{old}(x\_i)-f\_m(x\_i))^2=\frac{1}{2}(r\_i-f\_m(x\_i))^2$, 这里$r\_i$正好就是label的残差. 所以对于回归问题的提升树算法来说, 每次只需拟合之前模型的残差就行, 也不用设置什么样本权重和模型权重了.

### GBDT
在以上两个例子中, 指数loss和平方loss都是比较容易求导的loss, 对于其它损失函数, Freidman提出将$f_{old}(x)$的损失函数, 在每个样本输出的负梯度(导数), 作为$f\_m(x)$的目标函数的做法, 即将$-\partial L(y\_i,f\_{old}(x\_i))/\partial f\_{old}(x\_i)\rightarrow y\_i$, 以平方损失为例, 即$y\_i-f\_{old}(x\_i)$作为新的label.

### Bagging(bootstrap aggregating)

bagging是对数据集进行有放回地采样, 生成多个训练集, 然后对于每个训练集都训练一个模型出来. 在预测时, 对这些模型的输出做平均或投票. Bagging + 决策树 = 随机森林.

bagging在子模型不完全相同的时候, 可以减少模型的方差, 因为$Var(\frac{\sum X\_i}{n})=\frac{Var(X)}{n}$; 对于偏差, 则一般不能显著减少. 和bagging相反, boosting一般可以减小偏差, 但可能过拟合. 更多参见[知乎](https://www.zhihu.com/question/26760839).
