##### 兼容HTML
不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown；只要直接加标签就可以了。

要制约的只有一些 HTML 区块元素――比如 div、table、pre、p等标签，必须在前后加上空行与其它内容区隔开，还要求它们的开始标签与结尾标签不能用制表符或空格来缩进。
***
# 一、快速入门
***
#### 1. 标题
Markdown 支持两种标题的语法，Setext 和 atx 形式。Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题，注意不是下划线）任何数量的等号和减号都会产生效果；Atx 形式在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶。

**Setext**形式：

一级标题
=======
二级标题
-------

**Atx**形式：

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
一共六级标题，建议在#后面加个空格

下面的格式都需要注意文本和符号之间的空格：
#### 2. 无序列表，星号、加号和减号作为项目标记
- 无序
* 无序
+ 无序
- 无序

#### 有序列表，直接加1., 2.等，注意是英文句点。
1. 有序
2. 有序
3. 有序

如果列表项之间加入了空行，则所有的列表项被当成一个单独的段落进行处理。<br>
当然列表项中也可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

1.	This is a list item with three paragraphs.
	
	> This is the second para, and is also a quote.	
	
	This is the third paragraph.
2. Suspendisese id sem.

注意列表项中的区块代码需要比列表项多缩进一次。
#### 3. 尖括号（大于号）表示引用(区块引用)，这与email中用>的引用方式相同。
> >这是引用
> ## This is an H2 in a blockquote.

引用可以嵌套，亦可以使用其他Markdown语法。Markdown 也允许你偷懒只在整个段落的第一行最前面加上>。

#### 4. 图片与链接、引用
图片为\!\[]()，链接为\[]()，区别只在于一个叹号。链接的圆括号中也可以使用相对路径。例如：
[百度](http://www.baidu.com "With a title")(这个超链接带有title属性)。

<img src="001.jpg">

	![借东西的小人阿莉埃蒂](/001.jpg "This is a title")

参考式链接可以放在文件中任何一个地方，可以放在链接出现的段落后面，也可以放在文件最后面，就像注解一样：

> I get 10 times more traffic from [google][1] than from [yahoo][2] or [msn][3]. 

注意连接名称不但可以用1 2 3，字母数字和空格都可以用，但不区分大小写。
[1]: http://google.com/ "google(this is a title)"
[2]: http://search.yahoo.com/
[3]: http://search.msn.com/

#### 5. 粗体和斜体（修辞和强调）
使用星号和下划线来标记需要强调的区段。两个*包含就是粗体，一个\*包含就是斜体，例如：

**粗体**
*斜体*

> Some of these words _are emphasized also_.<br>
> Or, if you prefer, __use two underscores instead__.

如果你的`*`和`_`两边都有空白的话，它们就只会被当成普通的符号。
如果要在文字前后直接插入普通的星号或者下划线，可以在前面加上**反斜线**。
#### 6. 表格
后续再整

#### 7. 代码框
一般的代码文字中使用反引号\`来标记代码区段，例如：
`using namespace std`。

块代码，每行前面都加4个空格或一个Tab

	#include<iostream.h>
	using namespace std;
	int main(int argc, char * argv[]){
	
	}

#### 8. 分割线
你可以在一行中用三个以上的星号\*、减号\-、下划线\_来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

	***
	* * *
	- - - 
	___

# 二、详细教程
***
#### 1. 区块元素
##### 段落和换行
一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行。
<br>当然也可以强制插入换行符br，例如本段开始的地方。

#### 2. 区段元素
##### 图片
Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： 行内式和参考式。
**行内式**的图片语法看起来像是：

	![Alt text](/path/to/img.jpg)
	![Alt text](/path/to/img.jpg "Optional title")
 
**参考式**的图片语法则长得像这样：

	![Alt text][id]

图片参考的定义方式则和连结参考一样：

	[id]: url/to/image  "Optional title attribute"

到目前为止， Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的 `<img>`标签。
#### 3. 其他
##### 自动链接
对于网址和电子邮箱地址，可以直接用`<>`括起来，Markdown就会自动把它转成链接。例如：

	<http://example.com/>
Markdown会将其转成：

	<a href="http://example.com/">http://example.com/</a>
邮址的自动链接也很类似，只是Markdown会先做一个编码转换的过程，把文字字符转成16进位码的HTML实体，这样的格式可以避免直接传送邮箱的明文，在一定程度上防止垃圾邮件的接收。

##### 反斜杠
Markdown支持在以下这些符号前面加上反斜杠来将其变成普通的符号：

	\   反斜线
	`   反引号
	*   星号
	_   底线
	{}  花括号
	[]  方括号
	()  括弧
	#   井字号
	+   加号
	-   减号
	.   英文句点
	!   惊叹号