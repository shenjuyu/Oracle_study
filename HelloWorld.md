这是一个大标题
==============
这是一个小标题
______________

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

直接输入的文本就是普通文本，需要注意的是要换行的时候不能直接通过回车来换行，需要使用\<br/>。
<b>markdown支持一些html标签，你可以试试</b>这里使用了换行⬇⬇⬇⬇⬇<br/>当然如果你完全使用html来写的话，就丧失意义了，毕竟markdown并非专门做前端的，然而仅实现一般效果的话，它会比html写起来要简洁得多得多啦
显示标签要用转义字符"\" 例：\<br/><br/>
此外，要显示一个<b>超链接</b>的话，就直接输入这个链接的URL就好了。显示出来会自动变成可链接的形式的

单行文本  使用一个Tab符实现单行文本

	hello 大家好，我是伯爵
	
多行文本
多行文本和单行文本异曲同工，只要在每行行首加一个Tab<br/>

	苹果
	香蕉
	芒果
	西瓜
	
部分文字的高亮
如果你想使一段话中部分文字高亮显示，来起到突出强调的作用，那么可以把它用 `  ` 包围起来。注意这不是单引号，而是Tab上方，数字1左边的按键（注意使用英文输入法）。

Thank `You` . Please `Call` Me `Coder`

文字超链接
给一段文字加入超链接的格式是这样的 \[ 要显示的文字 \]\( 链接的地址 \)。比如
[我的博客地址](https://github.com/shenjuyu/Oracle_study.git)

你还可以给他加上一个鼠标悬停显示的文本。

[我的博客地址](https://github.com/shenjuyu/Oracle_study.git "悬停显示")

插入符号 圆点符

编辑的时候使用的是星号 * 记得在*后面加空格

* 西瓜
* 饺子
* 面包

此外还有二级圆点和三级圆点。就是多加一个Tab

* 西瓜
	* 饺子
		* 面包

缩进  缩进的含义是很容易理解的。。

>数据结构  
>>树  
>>>二叉树  
>>>>平衡二叉树  
>>>>>满二叉树


插入图片

来源于网络的图片

网上有很多README插入图片的教程了，经[此博主](https://blog.csdn.net/ljc_563812704/article/details/53464039)多次测试呢，发现可以使用的最简单，最基本的语法是

\!\[\]\(http://www.baidu.com/img/bdlogo.gif)

![](http://www.baidu.com/img/bdlogo.gif)

在方括号里可以加入一些 标识性的信息，比如

\!\[baidu\]\(http://www.baidu.com/img/bdlogo.gif\)
![baidu](http://www.baidu.com/img/bdlogo.gif)

这个方括号里的baidu并不会对图像显示造成任何改动，如果你想达到鼠标悬停显示提示信息，那么可以仿照前面介绍的文本中的方法，就是这样


\!\[baidu\]\(http://www.baidu.com/img/bdlogo.gif "百度logo"\)
![baidu](http://www.baidu.com/img/bdlogo.gif "百度logo")

GitHub仓库里的图片

有时候我们想显示一个GitHub仓库(或者说项目)里的图片而不是一张其他来源网络图片，因为其他来源的URL很可能会失效。那么如何显示一个GitHub项目里的图片呢？

其实与上面的格式基本一致的，所不同的就是括号里的URL该怎么写。

    https://github.com/ 你的用户名 / 你的项目名 / raw / 分支名 / 存放图片的文件夹 / 该文件夹下的图片

这样一目了然了吧。 <b>raw 不晓得是个啥意思，如果不知道自己的项目里的图片的URL的话可以到图片的位置，
复制浏览器地址栏的地址就可以了</b>  比如：   

\!\[]\(https://github.com/shenjunyu/Oracle_study/blob/master/images/2019-08-22_191557.png)

![](https://github.com/shenjuyu/Oracle_study/blob/master/images/2019-08-22_191557.png)

给图片加上超链接

如果你想使图片带有超链接的功能，即点击一个图片进入一个指定的网页。那么可以这样写
<br/>该方法已作废
\[\!\[baidu]]\(http://baidu.com)
\[baidu\]:http://www.baidu.com/img/bdlogo.gif "百度Logo"

该方法可用⬇⬇⬇⬇<br/>
[![]\(http://www.baidu.com/img/bdlogo.gif)]\(http://baidu.com)

[![](http://www.baidu.com/img/bdlogo.gif)](http://baidu.com)


插入代码片段
我们需要在代码的上一行和下一行用` `` 标记。\``` 不是三个单引号，而是数字1左边，
Tab键上面的键。要实现语法高亮那么只要在 \``` 之后加上你的编程语言即可（忽略大小写）。
c++语言可以写成c++也可以是cpp。看代码

	\```java

	public class Test{

		public static void main(String [] args){
		
			System.out.println("Hello World!!!");
			
		}
		
	}

	\```

```java
public class Test{
	public static void main(String [] args){
		System.out.println("Hello World!!!");
	}
}
```









