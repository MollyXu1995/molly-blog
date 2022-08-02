---
title: "Markdown 的使用"
date: 2022-08-01T21:02:08+08:00
---

## 简介

Markdown 是一种轻量级的标记语言，可用于在纯文本文档中添加格式化元素。Markdown 由 John Gruber 于 2004 年创建，如今已成为世界上最受欢迎的标记语言之一。

1. 专注于文字内容；
2. 纯文本，易读易写，可以方便地纳入版本控制；
3. 语法简单，没有什么学习成本，能轻松在码字的同时做出美观大方的排版。

## 语法

### 标题

不同数量的`#`可以完成不同的标题，请用一个空格在 # 和标题之间进行分隔。如下：

```markdown
# 一级标题

## 二级标题

### 三级标题
```

# 一级标题

## 二级标题

### 三级标题

### 字体

粗体、斜体、粗斜体、删除线，需要在文字前后加不同的标记符号。如下：

```
**这个是粗体**

*这个是斜体*

***这个是粗体加斜体***

~~这里是删除线~~
```

**这个是粗体**

*这个是斜体*

***这个是粗体加斜体***

~~这里是删除线~~

### 段落
要创建段落，请使用空白行将一行或多行文本进行分隔。  
不要用空格（spaces）或制表符（ tab）缩进段落。如下：  
I really like using Markdown.

I think I'll use it to format all of my documents from now on.

### 换行
在一行的末尾添加两个或多个空格，然后按回车键,即可创建一个换行。


### 无序列表

无序列表的使用，在符号`-`或`*`或`+`后加空格使用。如下：

```
- 无序列表 1
- 无序列表 2
- 无序列表 3
```

- 无序列表 1
- 无序列表 2
- 无序列表 3

如果要控制列表的层级，则需要在符号`-`前缩进四个空格或一个制表符（Tab）。如下：

```markdown
- 无序列表 1
- 无序列表 2
  - 无序列表 2.1
  - 无序列表 2.2
```

- 无序列表 1
- 无序列表 2
  - 无序列表 2.1
  - 无序列表 2.2



### 有序列表

有序列表的使用，在数字及符号`.`后加空格后输入内容。如下：

```
1. 有序列表 1
2. 有序列表 2
3. 有序列表 3
```

1. 有序列表 1
2. 有序列表 2
3. 有序列表 3

### 引用

引用的格式是在符号`>`后面书写文字。  
块引用可以包含多个段落，为段落之间的空白行添加一个`>`符号。  
块引用可以嵌套，在要嵌套的段落前添加一个`>>`符号。

如下：
```
> 读一本好书，就是在和高尚的人谈话。 ——歌德

> 雇用制度对工人不利，但工人根本无力摆脱这个制度。 ——阮一峰
```

> 读一本好书，就是在和高尚的人谈话。 ——歌德

> 雇用制度对工人不利，但工人根本无力摆脱这个制度。 ——阮一峰
```
> Dorothy followed her through
>
>The Witch bade her
```

> Dorothy followed her through
>
>The Witch bade her 

```
> Dorothy followed her through
>
>>The Witch bade her
```
> Dorothy followed her through
>
>>The Witch bade her


### 链接

```markdown
微信公众号仅支持公众号文章链接，即域名为`https://mp.weixin.qq.com/`的合法链接。使用方法如下所示：

对于该论述，欢迎读者查阅之前发过的文章，[你是《未来世界的幸存者》么？](https://mp.weixin.qq.com/s/s5IhxV2ooX3JN_X416nidA)
```

微信公众号仅支持公众号文章链接，即域名为`https://mp.weixin.qq.com/`的合法链接。使用方法如下所示：

对于该论述，欢迎读者查阅之前发过的文章，[你是《未来世界的幸存者》么？](https://mp.weixin.qq.com/s/s5IhxV2ooX3JN_X416nidA)

### 网址和Email地址
使用尖括号可以很方便地把URL或者email地址变成可点击的链接。如下：
```
<https://markdown.com.cn>
<fake@example.com>
```
<https://markdown.com.cn>  
<fake@example.com>

### 图片

插入图片，格式如下：

```
![这里写图片描述](https://www.nginx.cn/wp-content/uploads/2020/03/qrcode_for_gh_82cf87d482f0_258.jpg)
```

![这里写图片描述](https://www.nginx.cn/wp-content/uploads/2020/03/qrcode_for_gh_82cf87d482f0_258.jpg)



支持 jpg、png、gif、svg 等图片格式，其中 svg 文件仅可在微信公众平台中使用，svg 文件示例如下：

```
![](https://markdown.com.cn/images/i-am-svg.svg)
```

![](https://markdown.com.cn/images/i-am-svg.svg)

注：支持图片 拖拽和截图粘贴 到编辑器中，仅支持 https 的图片，图片粘贴到微信时会自动上传微信服务器。
### 链接图片
给图片增加链接，请将图像的Markdown 括在方括号中，然后将链接添加在圆括号中。如下：
```
[![沙漠中的岩石图片](/assets/img/shiprock.jpg "Shiprock")](https://markdown.com.cn)
```

### 分割线

可以在一行中用三个减号（---）来建立一个分隔线，同时需要在分隔线的上面空一行。如下：

```

---
```



---



### 表格

可以使用冒号来定义表格的对齐方式。如下：

```
| 姓名   | 年龄 |     工作 |
| :----- | :--: | -------: |
| 小可爱 |  18  | 吃可爱多 |
| 小小勇敢 |  20  | 爬棵勇敢树 |
| 小小小机智 |  22  | 看一本机智书 |
```

| 姓名       | 年龄 |         工作 |
| :--------- | :--: | -----------: |
| 小可爱     |  18  |     吃可爱多 |
| 小小勇敢   |  20  |   爬棵勇敢树 |
| 小小小机智 |  22  | 看一本机智书 |



## 特殊语法

### 代码块

如果在一个行内需要引用代码，只要用反引号引起来就好。如下：

```
Use the `printf()` function.
```

Use the `printf()` function.



在需要高亮的代码块的第一行及最后一行使用三个反引号，同时 第一行反引号后面表示代码块所使用的语言。如下：

````
```java
// FileName: HelloWorld.java
public class HelloWorld {
  // Java 入口程序，程序从此入口
  public static void main(String[] args) {
    System.out.println("Hello,World!"); // 向控制台打印一条语句
  }
}
```
````

```java
// FileName: HelloWorld.java
public class HelloWorld {
  // Java 入口程序，程序从此入口
  public static void main(String[] args) {
    System.out.println("Hello,World!"); // 向控制台打印一条语句
  }
}
```


## 其它语法

### HTML

```
支持原生 HTML 语法，请写内联样式，如下：

<span style="display:block;text-align:right;color:orangered;">橙色居右</span>
<span style="display:block;text-align:center;color:orangered;">橙色居中</span>
```

<span style="display:block;text-align:right;color:orangered;">橙色居右</span>
<span style="display:block;text-align:center;color:orangered;">橙色居中</span>

