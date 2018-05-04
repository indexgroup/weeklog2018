本周继续进行了腾讯社交广告算法比赛的参赛, 这里记录一下两种数据预处理的方法: `preprocessing.OneHotEncoder()`和`CountVectorizer()`, 都是sklearn里的.

### OneHotEncoder()

由于要使得类别型的变量能最终被模型直接使用, 必须使用one-of-k编码或者one-hot编码. 
这些都可以通过OneHotEncoder实现, 它可以将有n种值的一个特征变成n个二元的特征。


``` python
enc = preprocessing.OneHotEncoder()
enc.fit([[0, 0, 3], [1, 1, 0], [0, 2, 1], [1, 0, 2]])
enc.transform([[0,1,3]]).toarray()
```

### CountVectorizer()

至于CountVectorizer, 则是对有多个离散特征取值的样本进行编码

``` python
from sklearn.feature_extraction.text import CountVectorizer

texts=["dog cat fish","dog cat cat","fish bird", 'bird']
cv = CountVectorizer()
cv_fit=cv.fit_transform(texts)

print(cv.get_feature_names())
print(cv_fit.toarray())
#['bird', 'cat', 'dog', 'fish']
#[[0 1 1 1]
# [0 2 1 0]
# [1 0 0 1]
# [1 0 0 0]]
```
