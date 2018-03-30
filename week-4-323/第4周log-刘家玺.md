### 统计学习方法
本周学习了李航的统计学习方法的支持向量机里面的内容, 我发现李航的书讲的比较简单直接, 以干货为主

### 算法题
本周给研究生的算法课程除了期中考试的试卷, 也很多算法题. 发现自己写代码能力亟待提高= =. 比如前几天面试遇到一个题, 里面需要设计一个子函数, 把两个字符串表达的数字
加起来, 得到一个新的数字 这里我再临场发挥写一下这个代码
``` cpp
//其实用stoi()库函数更方便
string add(const string & s1, const string & s2) {
	string res;
	int i = s1.size() - 1, j = s2.size() - 1, flag = 0, tmp = 0; // flag表示是否进位
	while (i >= 0 or j >= 0 or flag == 1) {
		tmp = (i >= 0 ? (s1[i--] - '0') : 0) + (j >= 0 ? (s2[j--] - '0') : 0) + flag;
		res.push_back(tmp % 10 + '0');
		flag = tmp / 10;
	}
	reverse(res.begin(), res.end());
	return res;
}
```
