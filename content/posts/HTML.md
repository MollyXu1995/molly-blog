---
title: "HTML5的使用"
date: 2022-08-03T08:04:45+08:00
draft: true
---
## HTML5的简介
HTML5是用来描述网页的一种语言，被称为`超文本标记语言`。用HTML5编写的文件，后缀以`.html`结尾。  
HTML是一种标记语言，标记语言是一套标记`标签`。标签是由尖括号包围的关键字，例如：`<html>`  
标签有两种表现形式：
- **双标签**，例如：`<html></html>`
- **单标签**，例如：`<img>`

---
## HTML5的DOCTYPE声明
DOCTYPE是 document type（文档类型）的缩写。`<!DOCTYPE html>`是H5的**声明，位于文档的最前面，处于标签之前**。  
**他是网页必备的组成部分**，避免浏览器的怪异模式。
```
<!DOCTYPE html>
```
![例图](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/1659492647996.2dwvag9vb6v4.webp)

---
## HTML5基础骨架
```html
<!DOCTYPE html>
<html>
    <head>
        <meta>
        <title>…</title>
    </head>
    <body>…</body>
</html>
```
### html标签
定义HTML文档，这个元素我们浏览器看到后就明白**这是个HTML文档**了，所以你的其他元素要包裹在它里面，这个标签限定了`文档的开始点和结束点`。
```html
<!DOCTYPE html>
<html>
    
</html>
```
### head标签
head标签用于定义文档的头部，文档的头部描述了**文档的各种属性和信息**，包括文档的**标题、在Web中的位置以及和其他文档的关系**。  
绝大多数文档头部包含的数据都`不会真正作为内容显示给读者`。
```html
<!DOCTYPE html>
<html>

    <head>…</head>

</html>
```
### body标签
body元素定义文档的主体，包含`文档的所有内容`（**文本、超链接、图像、表格、列表等等**）。  
它是直接`在页面中显示出来，用户可以直观看到的内容`。

```html
<!DOCTYPE html>
<html>

    <head>…</head>
    <body>…</body>

</html>
```
### title标签
1. 可定义**文档的标题**
2. 它显示在浏览器窗口的标题栏或状态栏上
3. `<title>`标签是`<head>`标签中唯一**必须要求包含的东西**，就是说`写head一定要写title`
4. `<title>`的增加有利于SEO优化
> SEO是“搜索引擎优化”的英文缩写。通过对网站的内容调整，满足搜索引擎的排名需求。
```html
<!DOCTYPE html>
<html>
    <head>
        <title>百度下你就知道</title>
    </head>
    <body>
        我会显示浏览器中
    </body>
</html>
```
### meta标签
meta是*单标签*，用来**描述一个HTML网页文档的属性、关键词等**，例如：`charset="utf-8"`是说当前使用的是`utf-8`编码格式，在开发中我们会经常看到`utf-8`或是`gbk`，这些都是编码格式，通常使用`utf-8`
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>百度下你就知道</title>
    </head>
    <body>
        我会显示在浏览器中
    </body>
</html>
```

---
## 标签之标题
### 标签介绍与应用
标题（Heading）是通过`<h1>至<h6>`标签进行定义的  
`<h1>`定义最大的标题，`<h6>`定义最小的标题
```html
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
```
> 生成h1~h6快捷方式：写`h$*6 回车`
### VSCode插件
快速运行文件，打开浏览器  
- 安装：扩展->搜索open in browser->点击安装  
- 使用：鼠标右键->open in the default browser或open in the other browser
### 正确使用标题
1. 请确保将HTML标题标签**只用于标题**
2. 不要仅仅是为了生成粗体或大号的文本而使用标题
3. 正确使用标题有益于SEO
4. 应该将`<h1>`用作主标题（最重要的），其后是`<h2>`（次重要的），再其次是`<h3>`，以此类推  
![例图](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/1659503824736.77g7ogelsfk0.webp)

### 标题标签位置摆放
在标签中添加属性：`align="left|center|right"`默认居左
```html
    <h1 align="left">一级标题</h1>
	<h2 align="center">二级标题</h2>
	<h3 align="right">三级标题</h3>
	<h4>四级标题</h4>
	<h5>五级标题</h5>
	<h6>六级标题</h6>
```
> ***不推荐这么编写标题位置；后面学习CSS，用CSS来调整标题位置。***

---
## 标签之段落（p）、换行(br)、水平线(hr)
### 标签之段落
段落是通过`<p>`标签定义的
```html
<p>这是一个段落</p>
<p>这是另一个段落</p>
```
![例图](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/屏幕截图-2022-08-03-142417.6rx8e6fy4qs0.webp)
### 标签之换行
如果您希望在不产生一个新段落的情况下进行换行（新行），请使用`<br>`  
`<br>`元素是一个空的HTML元素，单标签，所以建议写成`<br/>`
```
<p>这个<br>段落<br>演示了分行的效果</p>
```
> <p>这个<br>段落<br>演示了分行的效果</p>

### 标签之水平线
`<hr/>`标签在HTML页面中创建**水平线**  
`<hr>`单标签，默认银灰色，可设置属性
```html
<hr color="" width="" size="" align=""/>
```
属性：
1. color:设置水平线的颜色，取值为red、green、blue……
2. width:设置水平线的宽度（长度）,单位px（像素）可省略不写
3. size:设置水平线的高度，单位px（像素）可省略不写
4. align:设置水平线的对齐方式（默认居中），可取值left|right

---
## 标签之图片
### 网站中最多的元素是图片  
`<img>`标签定义HTML页面中的图像
```html
<img src="" alt="" title="" width="" height="">
```
> 注意事项  
`<img>`是单标签，**不需要进行闭合操作**  
`图片`和`.html`文档，**必须在同一个文件夹下**  
可设置属性，图片被拉伸不好看，所以一般只设置宽度，不设置高度

属性：
1. src:路径（图片地址或名字加后缀）
2. alt:规定图像的替代文本，即图片无法显示时，才会显示替代文本
3. title:鼠标悬停在图片上给与提示
4. width:规定图像的宽度，单位px（像素）
5. height:规定图像的高度，单位px（像素）

---
## 图片路径详解
### 绝对路径 
绝对路径是电脑的盘符存储与访问的具体地址；  
即图片保存路径加名字与后缀，此时`图片`和`.html`文档，**不需要在同一个文件夹下** 
```html
<img src="D:\projects\itbaizhan_base\海绵宝宝.webp"> 
```
### 相对路径
两者相对关系，两者在同一路径下可以直接访问
1. 子级关系：`/`
    - 即图片在，与.html文档同级下的文件夹里
    - ```<img src="images/猪八戒.webp">```
2. 父级关系：`../`
    - 即图片与，.html文档所在的文件夹是同级
    - ```<img src="../路飞.webp">```
3. 同级关系：`./` （可省略）
    - 即`图片`和`.html`文档在同一文件夹，直接名字与后缀
    - ```<img src="小哥哥.jpeg">```

### 网络路径
直接填写图片的网络地址   
图片的网络地址：https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/image.3r2rcib7u5e0.webp
```html
<img src="https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/image.3r2rcib7u5e0.webp"> 
```

---
## 标签之超文本链接
### 超链接描述
HTML使用便签`<a>`来设置超文本链接  
超链接可以是一个字，一个词，一组词，一幅图像，您可以点击这些内容来跳转到新的文档  
```html
<a href="url">链接文本</a> 
```
### 超链接属性
在标签`<a>`中使用了`<href>`属性来表述**链接的地址**  
默认情况下，链接将以下形式出现在浏览器中：
1. 一个未访问链接显示为蓝色字体并带有下划线
2. 访问过的链接显示为紫色并带有下划线
3. 点击链接时，链接显示为红色并带有下划线
> 特别提示：   
***后期我们会通过CSS样式来修改这些效果***
### 超链接表现
当您把鼠标指针移动到网页中的某个链接上时，箭头会变成一只小手

---
## 标签之文本
### 常用文本标签
| 标签 | 描述 |
| :--: | :--: |
| `<em>` |  定义着重文字  |
| `<b>`  |  定义粗体文本  |
| `<i>`  |  定义斜体字    |
| `<strong>` | 定义加重语气 |
| `<del>`    | 定义删除字 |
| `<span>`   | 元素没有特定的含义 |
> 特别提示：   
常用文本和段落是不同的，段落代表一段文本，而文本标签一般表示文本词汇    
与段落标签等等，相互可以嵌套用  
***后期我们会通过CSS来增加效果***

---
## 列表标签之有序列表
### 有序列表
有序列表是一列项目，列表项目**使用数字进行标记**  
有序列表始于`<ol>`标签，每个列表项始于`<li>`标签
```html
<ol>
    <li>苹果</li>
    <li>哈密瓜</li>
    <li>香蕉</li>
</ol>
```
<ol>
    <li>苹果</li>
    <li>哈密瓜</li>
    <li>香蕉</li>
</ol>

### type属性
`<ol>`的属性type拥有的选项
1. 1 表示列表项目用数字标号（1,2,3…）
2. a 表示列表项目用小写字母标号 (a,b,c…)
3. A 表示列表项目用大写字母标号 (A,B,C…)
4. i 表示列表项目用小写罗马数字标号 (i,ii,iii…)
5. I 表示列表项目用大写罗马数字标号 (I,II,III…)
```html
<ol type="A">
    <li>苹果</li>
    <li>哈密瓜</li>
    <li>香蕉</li>
</ol>
```
<ol type="A">
    <li>苹果</li>
    <li>哈密瓜</li>
    <li>香蕉</li>
</ol>

### 有序列表嵌套
列表是可以嵌套的，但也不建议嵌套太多不利于维护
```html
<ol>
    <li>水果</li>
    <li>蔬菜
        <ol>
            <li>茄子</li>
            <li>青菜</li>
            <li>土豆</li>
        </ol>
    </li>
    <li>肉类</li>
</ol>
```
<ol>
    <li>水果</li>
    <li>蔬菜
        <ol>
            <li>茄子</li>
            <li>青菜</li>
            <li>土豆</li>
        </ol>
    </li>
    <li>肉类</li>
</ol>

---
## 列表标签之无序列表
### 无序列表实现
无序列表是一个项目的列表，此列项目使用粗体圆点（典型的小黑圆圈）进行标记  
无序列表始于`<ul>`标签，每个列表项始于`<li>`标签
```html
<ul>
    <li>椅子</li>
    <li>沙发</li>
    <li>电视机</li>
</ul>
```
<ul>
    <li>椅子</li>
    <li>沙发</li>
    <li>电视机</li>
</ul>

### type属性
`<ul>`的属性type拥有的选项  

- disc 默认实心圆
- circle 空心圆
- square 小方块
- none 不显示
```html
<ul type="square">
    <li>椅子</li>
    <li>沙发</li>
    <li>电视机</li>
</ul>
```
<ul type="square">
    <li>椅子</li>
    <li>沙发</li>
    <li>电视机</li>
</ul>

### 无序列表嵌套
列表是可以进行嵌套的
```html
<ul>
    <li>大小</li>
    <li>颜色
        <ul>
            <li>红色</li>
            <li>蓝色</li>
            <li>粉色</li>
        </ul>
    </li>
    <li>形状</li>
</ul>
```
<ul>
    <li>大小</li>
    <li>颜色
        <ul>
            <li>红色</li>
            <li>蓝色</li>
            <li>粉色</li>
        </ul>
    </li>
    <li>形状</li>
</ul>

### 常见应用场景
1. 无序的列表效果
2. 导航效果

### 导航效果
```html
<ul>
    <li>Xiaomi手机</li>
    <li>Redmi红米</li>
    <li>电视</li>
    <li>笔记本</li>
</ul>
```
无序列表比有序列表使用广泛  
***后期通过CSS调整成横向的左右摆放位置***
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/image.6exj1rpy06w0.webp)

> 快捷键：   
快速生成ul+li的布局：`ul>li*3`（数字根据自己需要的li数量修改）

---
## 标签之表格
### 表格展示效果
表格在数据展示方面非常简单整齐，并且表现优秀  
每行里面的单元格（列）数量是等同的
>**表格组成与特点**  
行、列、单元格  
单元格特点：同行等高、同列等宽  
>
>**表格标签**  
表格：`<table>`  
行：`<tr>`  
（单元格）列：`<td>`  

2行2列：
```html
<table>
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
</table>
```
<table>
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
</table>

> 快捷键   
快速生成表格结构：`table>tr*4>td*3{单元格}`  
（数字是行列的数量；花括弧是文本信息）

### 表格属性
1. border：设置表格的边框
2. width：设置表格的宽度
3. height：设置表格的高度
```html
<table border="1" width="400" height="200">
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
		<tr>
			<td>单元格</td>
			<td>单元格</td>
		</tr>
	</table>
```
> ***不推荐这么编写属性；后面学习CSS，用CSS编写表格属性。***

---
## 表格单元格合并
### 单元格合并属性
- 水平合并：`colspan`  ；保留左边 删除右边
- 垂直合并：`rowspan` ； 保留上边 删除下边

合并单元格5和6；12和16；13和14和15；3和4和7和8
```html
<table border="1" width="500" height="300">
		<tr>
			<td>单元格1</td>
			<td>单元格2</td>
			<td colspan="2" rowspan="2">单元格3和4和7和8</td>
		</tr>
		<tr>
			<td colspan="2">单元格5和6</td>
		</tr>
		<tr>
			<td>单元格9</td>
			<td>单元格10</td>
			<td>单元格11</td>
			<td rowspan="2">单元格12和16</td>
		</tr>
		<tr>
			<td colspan="3">单元格13和14和15</td>
		</tr>
	</table>
```

---
## Form表单
表单在Web网页中用来给用户填写信息，从而能采集到用户信息，**使网页具有交互的功能。**  
所有的用户输入内容的地方都用表单来写，如登陆注册、搜索框
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/image.7h0u56h29100.webp)

**表单是由容器和控件组成的**，一个表单一般应该包含用户填写信息的输入框、按钮等，这些输入框按钮叫做控件，表单就是容器，它能容纳各种各样的控件
```html
<form action="url" method="get|post" name="myform"></form>
```
> **属性说明**  
action 服务器地址  
name 表单名称  
>
> **method中get和post的区别**  
数据提交方式，get把提交的数据url可以看到，Post看不到  
get一般用于提交少量数据，post用来提交大量数据 
### 表单元素
一个完整的表单包含三个基本组成部分：表单标签、表单域、表单按钮  
1. 表单标签  
2. 表单域
3. 表单按钮
```html
<form>
		<input>
		<input type="submit">
</form>
```
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/image.1o2s0jdtqmps.webp)

---
## 表单元素
### 文本框
文本域通过`<input type="text">`标签来设定，当用户要在表单中键入字母、数字等内容时，就会用到文本域
### 密码框
密码字段通过标签`<input type="password">`来定义
### 提交按钮
当用户单击确认按钮时，表单的内容会被传送到另一个文件，表单的动作属性定义了目的文件的文件名，由动作属性定义的这个文件通常会对接收到的输入数据进行相关的处理  
简单来讲，就是说您按提交按钮，就会把数据提交给服务器
```html
<form>
		用户名：<input type="text">
		密码：<input type="password">
		<input type="submit" value="登录">
</form>
```
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/image.3orr5tt2x420.webp)

> 温馨提示  
密码字段字符不会明文显示，而是以星号或圆点替代

---
## 块元素与行内元素（内联元素） 
HTML5出现之前，经常把元素按照块级元素和内联级元素区分。在HTML5中，元素不在按照这种方式区分，而是按照内容模型来区分，分为元数据型、区块型，标题型、文档流型……  
详细参考地址：<https://developer.mozilla.org/zh-CN/>  

虽然HTML5的版本，元素分类更细致了，但是对初学者并不友好，所以我们仍然按照块元素和内联元素做区分，这对我们的布局起到了至关重要的作用

### 块元素与内联元素的区别
| 块级元素 | 内联元素 |
| :--: | :--: |
| 块元素会在页面中独占一行（自上向下垂直排列） | 行内元素不会独占页面中的一行，只占自身的大小|
| 可以设置width，height属性 | 行内元素设置width，height属性无效 |
| 一般块级元素可以包含行内元素和其他块级元素 | 一般内联元素包含内联元素但不包含块级元素 |

常见块级元素：
> div、form、h1~h6、hr、p、table、ul 等

常见内联元素（行内元素）：
> a、em、i、span、strong 等

行内块级元素（特点：不换行、能够识别宽高）：
> button、img、input 等

```html
    <h1>标题</h1>
	<p>段落</p>
	<ul>
		<li>无序列表1</li>
		<li>无序列表2</li>
	</ul>

	<a href="#">超链接</a>
	<span>内容</span>
	<em>注重语气</em>
	<img src="小哥哥.jpeg" alt="" width="100">
```
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/image.2k5re7gwvto0.webp)

---
## HTML5新增标签
`HTML5`是`HTML`最新的修订版本，2014年10月是由万维网联盟`w3c`完成标准制定  
在`HTML5`出现之前，我们一般采用`DIV+CSS`布局我们的页面。但是这样的布局方式不仅使我们的文档结构不够清晰，而且不利于搜索引擎爬虫对我们页面的爬取（不利于SEO）。为了解决上述缺点，新增了很多新的**语义化标签**
### 扩展知识
`<div>`容器元素，也是页面中见到最多的元素
### H5新标签
通过很多`<div>`标签进行将页面分块，比较繁琐，所以新增H5新标签  

1. `<header></header>` 头部
2. `<nav></nav>` 导航
3. `<section></section>` 定义文档中的节，比如章节、页眉、页脚
4. `<aside></aside>` 侧边栏
5. `<footer></footer>` 脚部
6. `<article></article>` 代表一个独立的、完整的相关内容块，例如一篇完整的论坛帖子，一篇博客文章，一个用户评论等  

> 有些用户使用的浏览器版本比较低，考虑网页能在所有浏览器中运行，可能有些公司还是采用了老版本的`<div>`标签。如果不考虑网页在各浏览器的兼容问题，就用H5新标签  


