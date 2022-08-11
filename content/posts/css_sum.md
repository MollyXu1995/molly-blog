---
title: "Css知识总结"
date: 2022-08-10T12:11:27+08:00
tags: ['Language']
series: ['前端学习之旅']
---
## 简介
1. CSS 指**层叠样式表** (Cascading Style Sheets)
    - 样式表文件后缀名为`.css` 
    - 定义如何显示 HTML 元素的样式
    - 样式通常存储在样式表中，外部样式表通常存储在 CSS 文件中，可以极大提高工作效率

2. CSS语法：  
由两个主要的部分构成：选择器、一条或多条声明(样式)

![80c8a4f7efc332ccffc90dd4d801ec4](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/80c8a4f7efc332ccffc90dd4d801ec4.2gib7q601mjo.webp)

- 选择器通常是您需要改变样式的HTML元素 
- 声明总以大括号 {} 括起来。每条声明由一个属性和一个值组成。
- 每个属性有一个值。属性和值被冒号`:`分开。属性与属性之间用`;`分号隔开。 

## css创建样式表
### 外部样式表
应用于多个页面文档时，外部样式表将是理想的选择。通过改变一个文件来改变整个站点的外观。  
在html文档中用 `<link>` 标签链接到css文档样式表。 

```html
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```
```css
/*文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。*/
/*下面是一个样式表文件的例子:*/

hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
```

### 内部样式表
当单个文档需要特殊的样式时，就应该使用内部样式表。  
html文档中用 `<style>` 标签在文档头部定义内部样式表。
```html
<head>
    <style>
        hr {color:sienna;}
        p {margin-left:20px;}
        body {background-image:url("images/back40.gif");}
    </style>
</head>
```

### 行内样式(内联样式)
将标签和属性混杂在一起，这样会损失样式表的许多优势。当属性仅需在一个元素上应用1次时使用。  
在标签内使用`<style>`属性。style 属性可以包含任何 CSS 属性。
```html
<!--本例展示如何改变段落的颜色和左外边距-->
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
```

### 多重样式
如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 
```css
h3{              /*外部样式表拥有针对 h3 选择器的三个属性*/
    color:red;
    text-align:left;
    font-size:8pt;
}
```
```html
<style>   
    h3{             <!--内部样式表拥有针对 h3 选择器的两个属性-->
    text-align:right;
    font-size:20pt;
    }
</style>
```
拥有内部样式表的这个页面同时与外部样式表链接，那么 h3 得到的样式是:  
    `color:red;  text-align:right;  font-size:20pt;`  
即颜色属性将被继承于外部样式表，而文字排列和字体尺寸会被内部样式表中的规则取代。

### 多重样式优先级
CSS 优先规则：  
- 内联样式>ID选择器>类选择器>标签选择器  
- 类选择器 = 伪类选择器 = 属性选择器  
- 标签选择器 = 伪元素选择器

> 选择器都有一个权值，权值越大越优先；      
 当权值相等时，后出现的样式表设置要优于先出现的样式表设置；    
 继承的CSS 样式不如后来指定的CSS 样式；   

## css属性

### 背景
### 文本
### 字体
### 表格

### 尺寸 
### 边框
### 内边距、外边距
### 对齐
### 文档流
### 浮动和清除浮动                            
### 定位
### 显示和隐藏




## 选择器（符）
### 通配符
以`*`来定义  
可以与任何元素匹配，但优先级最低，一般做样式初始化
```html
<head>
    <style>
        *{
            color: orange;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <p>你好</p>
    <h5>我很好</h5>
</body>
```

### 标签选择器
HTML文档中的标签定义，`p、b、div、a、img、body`等。  
标签选择器，经常描述“共性”，无法描述某一个元素的“个性”
```html
<head>
    <style>
        p{
            color: red;
        }
    </style>
</head>
<body>
    <p>衣服</p>
    <p>鞋子</p>
</body>
```

```html
<head>            <!--让“苹果”变为红色字体-->
    <style>
        span{
            color: red;
            }
    </style>
</head>
<body>
    <p>先吃西瓜<span>苹果</span>，再吃米饭</p>
</body>
```
 > 提示：  
 ① 所有的标签，都可以是选择器。比如ul、li、lable、dt、input等  
②无论这个标签藏的多深，一定能够被选择上  
③选择的所有，而不是一个

### 类选择器（class选择器）
用圆点`.`来定义。优点：灵活
```html
<head>
    <style>
        .content{
            color: red;
        }

        .size{
            font-size:30px;
        }
    </style>
</head>
<body>
    <p>加油</p>
    <h1 class="content">我哭了</h1>
    <p class="content size">我又哭了</p>
</body>
```
```html
正确编写
 <p class="content size">我又哭了</p>

错误编写
<p class="content" class="size">我又哭了</p>
```
> class属性的特点  
①  类选择器可以被多种标签使用  
②  类名**不能以数字开头**  
③同一个标签可以使用多个类选择器。**用空格隔开**

### id选择器
以`#`来定义  
针对某一个特定的标签来使用，只能使用一次。
```html
<head>
    <style>
        #mytitle{
            color: blue;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <p id="mytitle">向往的生活</p>
</body>
```
> 特别强调  
① ID是唯一的，id的名称不能重复  
② ID不能以数字开头

### 分组选择器
`选择器1,选择器2…{}` 每个选择器用逗号分隔   
提取共同的样式，减少重复代码的编写
```html
<head>
    <style>
        p,h3{
            color: blue;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <p>向往的生活</p>
    <h3>你好世界</h3>
</body>
```
```html
<head>
    <style>
        .text,.title{
            color: red;
            font-size: 50px;
        }
    </style>
</head>
<body>
    <p class="text">李雷</p>
    <h3 class="title">韩梅梅</h3>
</body>
```

### 嵌套选择器  
|选择符|描述|
|:--|:--|  
|p{ }|为所有 p 元素指定一个样式。  |
|.marked{ } |为所有 class="marked" 的元素指定一个样式。|  
|.marked p{ } |为所有 class="marked" 元素内的 p 元素指定一个样式。| 
|p.marked{ } |为所有 class="marked" 的 p 元素指定一个样式。|

```html
<head>
	<style>
		p{color:blue;
		text-align:center;
		}
	
		.marked{background-color:red;
		}
	
		.marked p{color:white;
		}
	
		p.marked{text-decoration:underline;
		}
	</style>
</head>

<body>
	<p>这个段落是蓝色文本，居中对齐。</p>
	
	<div class="marked">
		<p>这个段落不是蓝色文本。</p>
	</div>
	
	<p>所有 class="marked"元素内的 p 元素指定一个样式，但有不同的文本颜色。</p>
	
	<p class="marked">带下划线的 p 段落。</p>
</body>
```

### 关系选择器
#### 后代选择器
选择所有被E元素包含的F元素，中间用`空格`隔开  
`E F{}`
`E F G…{}`
```html
<head>                <!--段落1、2为黄色-->
    <style>
        div p{background-color:yellow;
        }
    </style>
</head>
<body>
    <div>
        <p>段落 1。 在 div 中。</p>
        <p>段落 2。 在 div 中。</p>
    </div>

    <p>段落 3。不在 div 中。</p>
    <p>段落 4。不在 div 中。</p>
</body>
```

#### 子代选择器
选择所有作为E元素的直接子元素F，对更深一层元素不起作用，用`>`表示  
`E>F{}`
`E>F>G…{}`
```html
<head>               <!--只有“I live in Duckburg.”有颜色-->
    <style>
        div>p{background-color:yellow;
        }
    </style>
</head>
<body>
    <h1>Welcome to My Homepage</h1>
    <div>
        <h2>My name is Donald</h2>
        <p>I live in Duckburg.</p>
    </div>

    <div>
    <span><p>I will not be styled.</p></span>
    </div>

    <p>My best friend is Mickey.</p>
</body>
```

#### 相邻兄弟选择器
选择紧跟E元素**后面的第一个兄弟元素**F，用`+`表示  
`E+F{}`
`E+F+G…{}`
```html
<head>
    <style>
        div+p{background-color:yellow;
        }
    </style>
</head>
<body>
    <h1>文章标题</h1>

    <div>
        <h2>DIV 内部标题</h2>
        <p>DIV 内部段落。</p>
    </div>

    <p>DIV 之后的第一个 P 元素。</p>

    <p>DIV 之后的第二个 P 元素。</p>
</body>
```

#### 普通兄弟选择器
E元素**后面的所有兄弟元素**F，用`~`表示   
`E~F{}`
`E~F~G…{}`
```html
<head>               <!--段落3、4为黄色-->
    <style>
        div~p{background-color:yellow;
        }
    </style>
</head>
<body>
    <p>之前段落，不会添加背景颜色。</p>
    <div>
        <p>段落 1。 在 div 中。</p>
        <p>段落 2。 在 div 中。</p>
    </div>

    <p>段落 3。不在 div 中。</p>
    <p>段落 4。不在 div 中。</p>

</body>
```

### 属性选择器
|选择符|	描述|
|:-|:-|
|[att]|	选择具有 att 属性的元素。|  
|[att = val]	|选择具有 att 属性且属性值等于 val 的元素。|  
|[att ~= val]	|选择具有 att 属性且属性值为用空格分隔的字词列表，其中一个等于 val 的元素。|
|[att ^= val]|	选择具有 att 属性且属性值为以 val 开头的字符串的元素。|
|[att $= val]	|选择具有 att 属性且属性值为以 val 结尾的字符串的元素。|
|[att *= val]	|选择具有 att 属性且属性值为包含 val 的字符串的元素。|
|[att &#124;=val]|选择具有 att 属性且属性值为以 val 开头并用连接符"-“分隔的字符串的元素，如果属性值仅为 val，也将被选择。|

```html
<head>          <!--把包含标题（title）的所有元素变为蓝色-->
    <style>
        [title]{color:blue;
        }
    </style>
</head>
<body>
    <h2>Will apply to:</h2>
    <h1 title="Hello world">Hello world</h1>
    <a title="runoob.com" href="http://www.runoob.com/">runoob.com</a>
    <hr>
    <h2>Will not apply to:</h2>
    <p>Hello!</p>
</body>
```

### 伪类选择器
|选择符|	版本|	描述|
|:-|:-|:--|
|E:link	|CSS1|	设置超链接a在未被访问前的样式。|
|E:visited|	CSS1	|设置超链接a在其链接地址已被访问过时的样式。|
|E:hover	|CSS1/2	|设置元素在其鼠标悬停时的样式。|
|E:active|	CSS1/2	|设置元素在被用户激活（在鼠标点击与释放之间发生的事件）时的样式。|
|E:focus	|CSS1/2	|设置元素在成为输入焦点（该元素的onfocus事件发生）时的样式。|
|E:first-child	|CSS2|	匹配父元素的第一个子元素E。|
|E:last-child	|CSS3|	匹配父元素的最后一个子元素E。|
|E:only-child	|CSS3|	匹配父元素仅有的一个子元素E。|
|E:nth-child(n)|	CSS3|	匹配父元素的第n个子元素E。|
|E:empty	|CSS3	|匹配没有任何子元素（包括text节点）的元素E。|
|E:checked	|CSS3	|匹配用户界面上处于选中状态的元素E。(用于input type为radio与checkbox时)|
|E:disabled|	CSS3	|匹配用户界面上处于禁用状态的元素E。|

```css
/* 链接的不同状态都可以以不同的方式显示 */
a:link {color:#FF0000;}       /* 未访问的链接 */
a:visited {color:#00FF00;}    /* 已访问的链接 */
a:hover {color:#FF00FF;}     /* 鼠标划过链接 */
a:active {color:#0000FF;}    /* 已选中的链接 */

/* 选择器匹配作为任何元素的第一个子元素的 <p> 元素*/
p:first-child{color:blue;}   

 /*选择相匹配的所有<p>元素的第一个 <i> 元素 */
p > i:first-child{color:blue;}

 /*选择器匹配所有作为元素的第一个子元素的 <p> 元素中的所有 <i> 元素 */
p:first-child i{color:blue;}
```
> 在CSS定义中：  
a:hover 必须被置于 a:link 和 a:visited 之后，才是有效的。    
a:active 必须被置于 a:hover 之后，才是有效的。

### 伪对象选择器

|选择符|	描述|
|:-|:-|
|E::first-letter|	设置对象内的第一个字符的样式。|
|E::first-line	|设置对象内的第一行的样式。|
|E::before	|设置在对象前（依据对象树的逻辑结构）发生的内容。用来和 content 属性一起使用|
|E::after	|设置在对象后（依据对象树的逻辑结构）发生的内容。用来和 content 属性一起使用|
|E::placeholder	|设置对象文字占位符的样式。|
|E::selection	|设置对象被选择时的颜色。|


## 布局
### 网页布局
### 盒子模型
### 弹性盒子模型
### 网格布局
### 圣杯布局
### 输入框的布局
### 悬挂式布局
### 固定的底栏
### 流式布局





## 扩展
### css响应式设计
#### 媒体查询
#### 视频
#### 框架
### css3新特性
#### 圆角
#### 阴影
#### 动画
### 滚动条
### 鼠标
### 颜色



## 参考
{{< card "http://css.doyoe.com/" >}}        
{{< card "https://developer.mozilla.org/en-US/" >}}      
{{< card "https://www.runoob.com/css/css-tutorial.html" >}}     
{{< card "https://www.w3school.com.cn/index.html" >}}
