---
title: "HTML5知识总结"
date: 2022-08-10T12:02:47+08:00
tags: ['Language']
series: ['前端学习之旅']
---
## HTML简介
- 概述  
HTML5是用来描述网页的一种语言，被称为`超文本标记语言`。用HTML5编写的文件，后缀以`.html`结尾。标记语言是一套标记`标签`。

- HTML标签  
**标签是由尖括号包围的关键字**，例如：`<html>`  
标签有两种表现形式：
  - **双标签**，例如：`<html></html>`
  - **单标签**，例如：`<img>`
>1、双标签的第一个标签是开始标签，第二个标签是结束标签  
2、<标签>内容</标签>  
> 3、属性写在开始标签


## HTML基础
### 网页框架
```html
<!DOCTYPE html>      <!--声明为html5文档-->
<html lang="zh-CN">     <!--根元素  zh-CN中文语言网站  en英文语言网站-->
<head>               <!--头部-->
    <meta charset="UTF-8">       <!--元数据 网页编码格式为utf-8-->
    <!--兼容ie浏览器的（ie兼容性差）-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">     
    <!--宽度等于设备宽度：移动端网页开发的时候用到-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">   
    <title>Document</title>      文档的标题

    属性设置、链接其他文档
    不会真正作为内容显示给用户

</head>              
<body>                   
    
    用户可见的页面内容

</body>
</html>
```
>vscode快捷键：`!`回车

### 元素
元素和属性：
- 元素属性包含元素的额外信息，这些信息不会出现在实际的内容中；  
- HTML属性大致分为 3 类：全局属性(id、class、style、title)、某一类元素属性、某一个元素属性。  
- `属性写在 HTML 元素开始标签中`，与标签名用空格分隔。标签上可以同时存在多个属性，没有顺序之分。
- 属性一般为 `属性名=“属性值”`，属性值必须用双引号包裹，也有单独出现的属性如 input 的布尔属性 disabled。
- 大多数HTML元素可以嵌套（HTML元素可以包含其他HTML元素）

#### 块级元素、行内元素(内联元素)
在 HTML 中有两种你需要知道的重要元素类别，块级元素和行内元素。

两者区别:
| 块级元素 | 内联元素 |
| :--: | :--: |
| 块元素会在页面中独占一行（自上向下垂直排列），其后的内容也会被挤到下一行展现 | 行内元素不会独占页面中的一行，只占自身的大小|
| 可以设置width，height属性 | 行内元素设置width，height属性无效 |
| 一般块级元素可以包含行内元素和其他块级元素 | 一般内联元素包含内联元素但不包含块级元素 |


> 常见块级元素：  
div、p、h1~h6、ul、li、dl、dt、dd、  
form、hr、table、   
 >
 >
>常见行内元素：  
a、span、em、i、strong、 
>
>
>行内块级元素：button、img、input、  
 （特点：不换行、能够识别宽高）

#### 区块布局
HTML 可以通过 `<div>` 和 `<span>`将元素组合起来。

1. `<div>` 元素是块级元素，可包裹分隔其他块级元素

    - 没有特定的含义。可用于组合其他 HTML 元素的容器
    - 与 CSS 一同使用，可用于对大的内容块设置样式属性
    - 常见的用途是文档布局

2. `<span>` 元素是行内元素，可包裹分隔其他行内元素

    - 没有特定的含义。可用于组合文档中的行内元素
    - 与 CSS 一同使用，可用于为部分文本设置样式属性

```html
<div>
  <h2>区块标题</h2>
  <p>区块描述文字</p>
</div>

<span>作者：xxx</span>
<span>发布时间：xx-xx-xx</span>
<span>浏览量：xxxx</span>
```
```html
<div id="container" style="width:500px">
 
<div id="header" style="background-color:#FFA500;">
<h1 style="margin-bottom:0;">主要的网页标题</h1></div>
 
<div id="menu" style="background-color:#FFD700;height:200px;width:100px;float:left;">
<b>菜单</b><br>
HTML<br>
CSS<br>
JavaScript</div>
 
<div id="content" style="background-color:#EEEEEE;height:200px;width:400px;float:left;">
内容在这里</div>
 
<div id="footer" style="background-color:#FFA500;clear:both;text-align:center;">
版权 © runoob.com</div>
 
</div>
```
![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220811/image.7hpcrwydoq80.webp)

#### 基础元素
- 标题  
```html
<h1>一级标题</h1>     <!--定义最大的标题-->
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>     <!--定义最小的标题-->
```

- 段落、换行、水平线
```html
<p>这个<br>段落<br>演示了分行的效果</p>

这个
段落
演示了分行的效果

<hr color="" width="" size="" align=""/>
<!--单标签，默认银灰色，可设置属性-->
```
- 文本格式化
```html
<b>加粗</b>           
<u>下划线</u>
<i>倾斜</i>
<s>删除线</s>

<!--语义：具有突出重要性的强调语境 -->
<strong>加粗</strong>
<ins>下划线</ins>
<em>倾斜</em>
<del>删除线</del>
```
- 超链接
```html
<a href="地址">链接文本</a>               
<!--"链接文本"不必一定是文本。图片或其他HTML元素都可以成为链接-->

<a href="https://www.baidu.com/" target="_blank">百度一下</a>     
 <!--target属性，目标网页的打开形式
         _blank 在新窗口中跳转（保留原网页）
         _self 默认值，在当前窗口中跳转（覆盖原网页）-->
```

- 图像
```html
<img src="图片地址" alt="替换文本" title="鼠标悬停提示信息" width="50px" height="40px"/>

<!-- 一般只设置width，同时设置图片会变形 -->
<!-- title属性不仅可以用于图片标签，还可以用于其他标签 -->
```

#### 列表
- 有序列表
```html
<ol type="A">              <!--ol标签定义 有序列表-->
    <li>苹果</li>
    <li>哈密瓜</li>        <!--li标签定义 列表项-->
    <li>香蕉</li>
</ol>
```

- 无序列表
```html
<ul type="square">         <!--ul标签定义 无序列表-->
    <li>椅子</li>          
    <li>沙发</li>      
    <li>电视机</li>
</ul>
```

- 自定义列表
```html
<dl>         <!--dl标签定义 自定义列表-->
    <dt>家具家电</dt>     <!--dt标签定义 列表的主题-->     
    <dd>沙发</dd>       
    <dd>电视机</dd>       <!--dd标签定义 列表项-->
    <dd>冰箱</dd>         <!--dd默认显示缩进效果-->
    <dd>衣柜</dd>
</dl>
```

> 1、ul ol标签，只允许包含 li  标签；dl标签，只允许包含dt/dd标签   
2、li dt dd 标签可以包含任何内容  
3、列表可以进行嵌套  
>
>应用场景
>- 无序列表：网页导航  
>- 自定义列表：网页底部






#### 表格
|名称|标签|说明|
|:--|:--|:--|
|表格|table|表格整体|
|标题|caption|写在table标签内部，默认顶部居中|
|行|tr|包裹th、td|
|表头|th|默认加粗居中|
|列/单元格|td|内容|
|水平合并|colspan||
|垂直合并 |rowspan||

表格样式效果：用`CSS`设置

```html
<!--3行2列 成绩单-->    
<!--border：设置表格的边框-->

<table border="1" width="400px" height="200px">
    <caption>同学成绩单</caption>
		<tr>
			<th>姓名</th>                   
			<th>成绩</th>
		</tr>
		<tr>
			<td>张三</td>
			<td>98</td>
		</tr>
    <tr>
			<td>李四</td>
			<td>76</td>
		</tr>
</table>
```

```html
<!--水平合并：colspan ；保留左边 删除右边
    垂直合并：rowspan ； 保留上边 删除下边 -->

<!--合并单元格5和6；12和16；13和14和15；3和4和7和8--> 


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

#### 表单
在Web网页中用来给用户填写信息，从而能采集到用户信息，使网页具有交互的功能。如登陆、注册、搜索框

```html
<form> </form>
```

| 属性名称 | 描述 |
| :-- | :--|
| name | 表单的名称 |
| `action` | 表单数据接收地址 |
| target | 打开 url 的方式，_blank 新窗口，_self 当前窗口 |
| method | 数据传送方法，get:通过 url 地址传送参数,网址中可以看到数据，post:后台传送 |
| enctype |	发送前如何将数据进行编码，仅与 method=“post"配对使用 |
| application/x-www-form-urlencoded | 默认值，发送前对所有字符进行编码：空格转+号，特殊字符传 ASCII 16 进制值 |
| multipart/form-data | 不对发送字符进行编码，在上传文件时，必须设置 |
| text/plain | 纯文本方式，仅将空格转为”+“号，不对特殊字符编码 |


- 表单域input的属性

| 属性名称 | 描述 |
| :-- | :-- |
| `type `| 元素的类型，如 text 文本框、radio 单选按钮、select 下拉框等 |
| `name `| 元素的名称，主要用于服务端数据传送；对单选框有分组功能，有相同name属性值的单选框为一组，一组中只能有一个被选中 |
|`placeholder`|占位符，提示用户输入内容的文本|
| checked | 默认先选中的选项|
| value	| 元素的默认值，可当占位符 |
| multiple	| type属性文件选择中，用于多文件选择 |
| size | 以字符计算的元素可见宽度，注意，不是像素或百分比 |
| maxlength | 元素允许的最大字符长度 |
| disabled | 禁用该控件，此时，既不能选择，也不能点击 |
| readonly | 该控件字段内容只读，不允许修改 |


- type属性值  
input标签通过type属性值的不同，展示不同效果

```html
<input type="">
```
|标签| type属性值 | 说明 |
|:--| :-- | :-- |
|input|text|文本框，输入单行文本|
|input|password|密码框，用于输入密码|
|input|`radio`|单选框，多选一|
|input|`checkbox`|多选框，多选多|
|input|file|文件选择，用于之后上传文件|
|input|submit|提交按钮，用于提交|
|input|reset|重置按钮，用于重置|
|input|button|普通按钮，默认无功能，之后配合js添加功能|


```html
<!-- 单行文本 密码 -->
<form action="#">
用户名: <input type="text" name="user" placeholder="请输入用户名">     
  密码: <input type="password" name="password">
</form>

<!-- 单选按钮 -->
<input type="radio" name="sex" value="male">男
<input type="radio" name="sex" value="female" checked>女
<!-- 有相同name属性值的单选框为一组，一组中只能有一个被选中 -->
<!-- 用label标签，文字同按钮有同样效果，也可直接点击文字选择 -->
<label><input type="radio" name="sex" value="male">男</label>


<!-- 复选框 -->
<input type="checkbox" name="vehicle" value="Bike">我喜欢自行车
<input type="checkbox" name="vehicle" value="Car">我喜欢小汽车

<!-- 自定义按钮 -->
<input type="button" value="请点击" />
<!-- 提交按钮 -->
<input type="submit" value="请提交" />
<!-- 重置按钮 -->
<input type="reset" value="请重置" />

<!-- 图像按钮 -->
<input type="image" src="url" alt="图片说明" />


<!-- 下拉框 -->
<select name="address" id="address">
  <option value="bj">北京</option>
  <option value="" selected>上海</option>
  <option value="">天津</option>
  <option value="">广州</option>
  <option value="">深圳</option>
  <option value="">重庆</option>
</select>

<!-- 下拉框分组 -->
<select name="address" id="address">
  <optgroup label="直辖市">
    <option value="bj" selected>北京</option>
    <option value="">上海</option>
    <option value="">天津</option>
    <option value="">重庆</option>
  </optgroup>
  <optgroup label="省级">
    <option value="">广州</option>
    <option value="">深圳</option>
  </optgroup>
</select>

<!-- 文件上传 -->
<form action="" method="post" enctype="multipart/form-data">
  <!-- 支持批量上传 -->
  <input type="file" name="file" id="file" multiple />
</form>

<!-- 隐藏字段 -->
<!-- 用于存储一些字段的默认值，如ID，用户不可见 -->
<input type="hidden" name="id" value="1" />

<!-- label标签 -->
<!-- label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。
如果您在 label 元素内点击文本，就会触发此控件。
就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。-->
<form action="" method="post" name="form">
  <label for="MyName">姓名：</label>
  <input type="text" name="MyName" id="MyName" placeholder="请输入姓名" />
</form>

<!-- 文本域 -->  <!--cols:每行最多多少个字符
                     rows:可以显示多少行
                     resize:both:默认值
                     none:不允许调整尺寸
                     horizontal:仅允许水平调整宽度
                     vertical:仅允许垂直调整高度 -->
<textarea
  name="message"
  id="message"
  cols="30"
  rows="10"
  style="resize: both;">
</textarea>
```

#### 媒体
- 视频   
视频标签目前支持三种格式：MP4、WebM、Ogg
```html
<video src="#" controls></video>

<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4" />
  <source src="movie.ogg" type="video/ogg" />
  您的浏览器不支持 video 标签。
</video>
```

| 属性名称 | 描述 |  
|  :--- | :-- | 
| src | 路径 |
|  controls  | 向用户显示控件，如播放按钮 |
|  autoplay  | 自动播放（谷歌浏览器需配合muted实现静音播放） | 
| height | 高度 |
| width | 宽度 |
| loop | 循环播放 |
| muted | 静音 |
| poster | 未开始播放时显示的图像 |
| preload | 如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 “autoplay”，则忽略该属性 |


- 音频  
音频标签目前支持三种格式：`MP3`、Wav、Ogg
```html
<audio src="#" controls></audio>
```

| 属性名称 | 描述 |
| :-- | :--|
| src |音频路径 |
| controls | 向用户显示控件，如播放按钮 |
| autoplay | 自动播放 |
| loop | 循环播放（部分浏览器不支持） |
| muted | 静音 |
| preload | 如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 “autoplay”，则忽略该属性 |


## 扩展
### 路径
页面找图片、音频、视频，需要通过路径才能找到
1. 绝对路径
    - 从盘符开始出发，找目标的过程

2. 相对路径（常用）  
    - 从当前`项目文件`开始出发，找目标的过程
    - 同级目录`./`
    - 下级目录`../`

3. 网络路径
    - 网络地址

### 头部元素
一般放置于 `<head>` 区域的元素标签

| 标签 | 描述 |
| :-- | :-- |
| head | 定义了文档的信息 |
| title | 定义了文档的标题 |
| base | 定义了页面链接标签的默认链接地址 |
| link | 定义了一个文档和外部资源之间的关系 |
| meta | 定义了HTML文档中的元数据 |
| script | 定义了客户端的脚本文件 |
| style | 定义了HTML文档的样式文件 |

- `<link>` 标签定义了文档与外部资源之间的关系。通常用于链接到样式表:

```html
<head>
           <!-- CSS引入 -->
    <link rel="stylesheet" type="text/css" href="mystyle.css">

           <!-- JS引入 -->
    <script src="script.js"></script>

</head>    
```
> 链接到JavaScript部分，没必要非要放在文档头部; 实际上，把它放在文档的尾部（在 `</body>`标签之前）是一个更好的选择 ，这样可以确保在加载脚本之前浏览器已经解析了 HTML 内容（如果脚本加载某个不存在的元素，浏览器会报错）

- `<style>` 标签中可以直接添加样式来渲染 HTML 文档:

```html
<head>
    <style type="text/css"> 
        body {background-color:yellow}
        p {color:blue}
    </style>
</head>
```

- `<meta>` 标签描述了一些基本的元数据。元数据不显示在页面上，但会被浏览器解析。通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

```html
视窗设置：
<meta name="viewport" content="width=device-width, initial-scale=1.0" />

IE 浏览器版本渲染设置：
<meta http-equiv="X-UA-Compatible" content="ie=edge" />

<!-- SEO 搜索引擎三大标签 -->
为搜索引擎定义关键词
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
为网页定义描述内容:
<meta name="description" content="告诉搜索引擎网站的基本简介" />
<meta name="description" content="免费 Web & 编程 教程">
<title>网站标题</title>  

定义网页作者:
<meta name="author" content="Runoob">

每30秒钟刷新当前页面:
<meta http-equiv="refresh" content="30">
```

### 语义化标签
通过很多`<div>`标签进行将页面分块，比较繁琐。  
HTML5 提供了新的语义元素来明确一个Web页面的不同部分:  

1. `<header></header>` 头部
2. `<nav></nav>` 导航
3. `<section></section>` 定义文档中的节，比如章节、页眉、页脚
4. `<aside></aside>` 侧边栏
5. `<footer></footer>` 脚部
6. `<article></article>` 代表一个独立的、完整的相关内容块，例如一篇完整的论坛帖子，一篇博客文章，一个用户评论等  

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220811/image.3bhm2u1rgya0.webp)

### 字符实体
- 在 HTML 中，某些字符是预留的不能直接使用，如小于号（<）和大于号（>），直接使用会误认为它们是标签。  
- 所以如果我们希望正确地显示预留字符，那必须在 HTML 源代码中使用字符实体（character entities）。

| 显示结果 | 描述 |	实体名称 |
|:-|:-|:- |
|  | 空格 | `&nbsp;`|
|<|	小于号|	`&lt;`|
|>|	大于号|	`&gt;`|
|&|	和号	|`&amp;`|
|©|	版权符号|	`&copy;`|
|×	|乘号	|`&times;`|


### 颜色 
几种颜色的表示方式  
- 英语表示：blue
- 十进制表示 : rgb(255,255,255);
- 十六进制表示 : #000000;
- 带透明度十进制 : rgba(0,0,0,0.5);

具体参见：[HTML颜色](https://www.runoob.com/html/html-tables.html)

## 参考
{{< card "http://t.mb5u.com/html/" >}}        
{{< card "https://developer.mozilla.org/en-US/" >}}      
{{< card "https://www.runoob.com/html/html-tables.html" >}}     
{{< card "https://www.w3school.com.cn/index.html" >}}


