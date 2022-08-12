---
title: "CSS知识总结"
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
- background-color : 背景颜色
- background-image : 背景图片
- background-repeat : 背景图是否重复
- background-attachment : 背景图片是否固定
- background-position : 背景图片定位(可以使用%和 px 值和英语单词)
- background(缩写形式) : #ccc url(‘xxx.png’) no-repeat fixed 50% 50%
- background-size : 设置背景图片的尺寸
- background-origin : 设置背景图的位置(padding-box\border-box\content-box)

### 文本
- color: 颜色  
- text-align: 对齐 
- text-decoration: 文本修饰  
- text-transform: 文本转换大小写字母
- text-indent: 文本第一行缩进
- line-height: 行高   
- text-shadow: 设置文字阴影  

```css
/*颜色*/                        
body {color:red;}
h1 {color:#00ff00;}
p.ex {color:rgb(0,0,255);}

/*对齐*/
h1 {text-align:center;}
p.date {text-align:right;}
p.main {text-align:justify;}   /*每一行被展开为宽度相等，左，右外边距是对齐*/

/*文本修饰*/
a {text-decoration:none;}             /*删除链接的下划线*/
h1 {text-decoration:overline;}       /*文本上方添加横线*/
h2 {text-decoration:line-through;}     /*文本中间添加横线*/  
h3 {text-decoration:underline;}         /*文本下方添加横线*/

/*文本转换大小写字母*/
p.uppercase {text-transform:uppercase;}   /*全部大写*/
p.lowercase {text-transform:lowercase;}   /*全部小写*/
p.capitalize {text-transform:capitalize;}   /*首字母大写*/

/*文本第一行缩进*/
p {text-indent:50px;}

/*设置行高*/
p.small {line-height:norma}    /*默认为浏览器的值*/
p.small {line-height:90%}   
p.big {line-height:200%}

/*设置文字阴影*/
h1{text-shadow: 2px 2px #ff0000;}  
```
### 字体
- font-family : 字体类型
- font-size : 字体大小
- font-style: 字体样式

### 表格(table)
使 HTML 表格更美观
- border-collapse:collapse    表格折叠成单一的边框
- border-spacing:    表格边框之间的距离

```css
table{ border-collapse:collapse;}
table,th, td{border: 1px solid black;}
```

### 尺寸 
- width : 设置宽度(屏幕自适应宽度 100%)
- height : 设置高度
- max-width:
- min-width:
- max-height:
- min-height:
- line-height:  设置行高

### 边框
- border-width : 边框粗细
- border-style : 边框样式
- border-color : 边框颜色
- border(缩写形式) : 1px solid #ccc
- border-left : 左侧边框
- border-top : 顶部边框
- border-right : 右侧边框
- border-bottom : 底部边框
- border-radius : 设置圆角
- box-shadow : 设置阴影

### 内边距、外边距
- margin-top : 上部外边距
- margin-right : 右侧外边距
- margin-bottom : 底部外边距
- margin-left : 左侧外边距
- margin(缩写) : 全部、上下/左右、上/左右/下、上/右/下/左
- padding-top : 上部内边距
- padding-right : 右侧内边距
- padding-bottom : 底部内边距
- padding-left : 左侧内边距
- padding(缩写) : 全部、上下/左右、上/左右/下、上/右/下/左
- margin: auto;  水平居中对齐一个元素

### 文档流
- 文档流产生的部分现象：
    - 块元素自上而下摆放，内联元素从左到右摆放
    -  高矮不齐，底边对齐
    -  空格折叠现象：不管你加多少空格，页面就只显示一个空格
    -  元素无间隙：放两张图片，这两张图之间会有一点点空隙

- 使一个元素脱离标准文档流有三种方式  
    - 浮动
    -  绝对定位
    -  固定定位

### 浮动和清除浮动  
浮动：增加一个浮层来放置内容，从而使元素脱离文档流
- `float`属性定义元素在哪个方向浮动，任何元素都可以浮动
- `float: left|right;`  浮动只有左右浮动，没有上下浮动

清除浮动: 浮动元素会造成父元素高度塌陷、后续元素会受到影响，对布局不利。  
解决方案：  
- 父元素设置高度，撑开元素本身大小
- 为受影响的元素增加clear属性` clear:both;`
- 父元素塌陷且同级元素也受到了影响（父布局不能设置高度）
    - overflow清除浮动：在父级标签的样式里加 `overflow:hidden;` `clear: both;`
    - 伪对象方式：为父标签添加伪类`after`，设置空的内容` content: "";`，并且使用`display: block;` `clear:both;` 

### 定位
- position:
    - absolute  绝对定位(脱离文档流，释放文档流中的位置，第一个定位的父标签左上角是原点)
    - relative  相对定位(遵循文档流，自己是原点)
    - fixed  固定定位(脱离文档流，相对于浏览器窗口是固定位置,不随窗口滚动)
    - static  静态定位(遵循正常的文档流对象)
- left : 设置左侧距原点的长度
- top : 设置上方的距原点的长度
- right : 设置右侧距原点的长度
- bottom : 设置底部距原点的距离
- Z-index : 设置元素的堆叠顺序（谁的Z-index值大，就能压盖Z-index值小的，可为负值）
- vertical-align : 设置元素的垂直对齐方式。

### 显示和隐藏
- display
    - none : 隐藏不占位
    - block : 块显示
    - inline : 行内显示
- visibility
    - hidden : 隐藏占位
    - visible : 显示
- opactity : 设置透明度


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
### 盒子模型
所有HTML元素可以看作盒子；  
CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：  
外边距（margin），边框(border)，内边距(padding)，和实际内容(content)
![1de8a1d57796e5f98d7768fd89d9186](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220807/1de8a1d57796e5f98d7768fd89d9186.5ezwq52ipbs0.webp)

1. Margin（外边距):清除边框外的区域，外边距是透明的(两个值的话：第一个值上下，第二个值左右)
2. Border(边框):围绕在内边距和内容外的边框（三个值的话：第一个值边框粗细，第二个值实线，第三个值颜色）
3. Padding(内边距)：清除内容周围的区域(两个值的话：第一个值上下，第二个值左右)
4. Content(实际内容):盒子的内容，显示文本和图像

如果把盒子模型看作是一个生活中的快递，那么内容部分等同于你买的实物，内边距等同于快递盒子中的泡沫，边框等同于快递盒子，外边距等同于两个快递盒子之间的距离
```html
<head>
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: green;
            padding: 20px 20px;
            border: 5px solid blue;
            margin: 30px 30px;
        }
    </style>
</head>
<body>
    <div>我是内容</div>
</body>
```
可以这样设置：
```html
<head>
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: red;
            padding-top: 20px;
            padding-bottom: 20px;
            padding-left: 20px;
            padding-right: 20px;

            border: 5px solid blue;
            margin-top: 30px;
            margin-bottom: 30px;
            margin-left: 30px;
            margin-bottom: 30px;
        }
    </style>
</head>
<body>
    <div>你好</div>
</body>
```
### 弹性盒子模型（flex box）
- 弹性盒子是CSS3的一种新的布局模式；   
- CSS3弹性盒是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式；  
- 引入弹性盒子布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间；

CSS3弹性盒内容  
1.弹性盒子由弹性容器（Flex container）和弹性子元素(Flex item)组成   
2. 通过设置`display`属性的值为`flex`将其定义为弹性容器  
3. 弹性容器内包含了一个或多个弹性子元素
> 提示  
弹性容器外、弹性子元素内是正常渲染的。弹性盒子只定义了弹性子元素如何在弹性容器内布局


比如：给外层容器`container`增加弹性容器的设置，就可以刚好的管理里面的这三个盒子`box1、box2、box3`，纵向摆放变成了横向摆放。
```html
<head>
    <style>
        .container{
             width: 500px;
             height: 500px;
            background-color: grey;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        .box1{
            width: 100px;
            height: 100px;
            background-color: red;
            flex: 2;
        }
        .box2{
            width: 100px;
            height: 100px;
            background-color: green;
            flex: 2;
        }
        .box3{
            width: 100px;
            height: 100px;
            background-color:blue;
            flex: 1;
        }
    </style>
</head>
<body>
    <div>
        <div class="container">
            <div class="box1"></div>
            <div class="box2"></div>
            <div class="box3"></div>
        </div>
    </div>
</body>
```
> 提示：默认弹性盒里内容横向摆放

父元素上的属性
1. display属性：  
`display:flex;`开启弹性盒，子元素默认水平横向排列

2. `flex-direction`属性：  
指定了弹性子元素在父容器中的位置，水平还是竖直
```css
flex-direction: row |row-reverse |column |column-reverse
```
- row：横向从左到右排列（左对齐），默认的排列方式
- row-reverse：反转横向排列（右对齐，从后往前排，最后一项排在最前面）不常用
- column：纵向排列（与顶部对齐）
- column-reverse：反转纵向排列（与底部对齐，从后往前排，最后一项排在最上面）不常用

3. `justify-content`属性:  （上下位置）  
内容对齐，应用在弹性容器上，把弹性项沿着弹性容器的主轴线（main axis）对齐
```css
justify-content: flex-start |flex-end |center
```
- flex-start：（居上摆放）弹性项目向行头紧挨着填充。这个是默认值。第一个弹性项main-start的外边距边线被放置在该行的main-start边线，而后续弹性项依次平齐摆放
- flex-end：（居下摆放）弹性项目向行尾紧挨着填充。第一个弹性项的main-end外边距边线被放置在该行的main-end边线，而后续弹性项依次平齐摆放
- center：（居中摆放）弹性项目居中紧挨着填充。（如果剩余的自由空间是负的，则弹性项目将在这两个方向上同时溢出）

4. `align-items`属性：（左右位置）  
设置或检索弹性盒子元素在侧轴（纵轴）方向上的对齐方式
```css
align-items: flex-start |flex-end |center
```
- flex-start：（居左）弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界
- flex-end：（居右）弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界
- center：（居中）弹性盒子元素在该行的侧轴（纵轴）上居中位置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）

子元素上的属性  
`flex`属性:  （平均分配）
- 根据弹性盒子元素所设置的扩展因子作为比率来分配剩余空间  
- 默认为0，即如果存在剩余空间，也不放大

如果只有一个子元素设置，那么按扩展因子转化的百分比对其分配剩余空间。0.1即10%，1即100%
> 举例   
容器大盒子总份数权重是500。第一个子元素盒子占200，第二个占200，第三个占100。也就是分别占了2，2，1

### 网格布局
#### 概念
- 网格是一组相交的水平线和垂直线，它定义了网格的列和行。
- CSS 提供了一个基于网格的布局系统，带有行和列，可以让我们更轻松地设计网页，而无需使用浮动和定位。
#### 网格元素
- 网格布局由一个父元素及一个或多个子元素组成。 
- display 属性设置为 grid 或 inline-grid 后，它就变成了一个网格容器，这个元素的所有直系子元素将成为网格元素。
- 通过 grid-template-columns 和 grid-template-rows 属性来定义网格中的行和列。一个网格轨道就是网格中任意两条线之间的空间
- 引入了 fr 单位帮助我们创建灵活的网格轨道。一个 fr 单位代表网格容器中可用空间的一等份。这些轨道会随着可用空间增长和收缩。
- 网格间距指的是两个网格单元之间的网格横向间距或网格纵向间距。
    - grid-column-gap 属性来设置列之间的网格间距：
    - grid-row-gap 属性来设置行之间的网格间距：
    - grid-gap

```html                      
<head>
<style>                                
.grid-container{          
  display: inline-grid;
  grid-template-columns: auto auto auto;      <!--3列-->
  grid-template-rows: 100px 300px;      <!--第一行高度为 100px，第二行高度为 300px-->
  background-color: #2196F3;
  padding: 10px;
}

.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  padding: 20px;
  font-size: 30px;
  text-align: center;
}
</style>
</head>
<body>

<div class="grid-container">           
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>    
  <div class="grid-item">3</div>  
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>  
  <div class="grid-item">7</div>
  <div class="grid-item">8</div>
  <div class="grid-item">9</div>  
</div>
</body>
```

## 扩展
### 媒体查询
- 媒体查询能使页面在不同的终端设备下达到不同的效果，根据设备的大小自动识别加载不同的样式  
- 设置meta标签：使用设备的宽度作为视图宽度并禁止初始的缩放。在`<head>`标签里加入这个`meta`标签

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!--参数解释
1. `width=device-width`宽度等于当前设备的宽度
2. `initial-scale`初始的缩放比例（默认设置为1.0）
3. `maximum-scale`允许用户缩放到的最大比例（默认设置为1.0）
4. `user-scalable`用户是否可以动手缩放（默认设置为no）-->
```

媒体查询语法
```html
<head>
    <style>
        .box{
            width: 300px;
            height: 300px;
        }  

                         /*设备小于768px加载样式，手机*/
        @media screen and (max-width:768px) {    
            .box{
                background-color: aqua;
            }

            .p1{
            display: none;   /*隐藏 不显示*/
            }

            .p2{
            display: none;  
            }
        }

                         /*设备大于768px但小于992px加载样式，平板*/
        @media screen and (min-width:768px) and (max-width:992px) {
            .box{
                background-color: green;
            }

            .p1{
            display: none;  
            }

            .p2{
            display: block;  /*显示*/
            }
        }


                         /*设备大于768px但小于992px加载样式，电脑*/
        @media screen and (min-width:992px) {
            .box{
                background-color: red;
            }

            .p1{
            display: block; 
            }

            .p2{
            display: block;  
            }
        }

    </style>
</head>
<body>

    <div class="box"></div>
    <p class="p1">哈哈哈哈</p>
    <p class="p2">呵呵呵呵</p>
    
</body>
```



### 动画
使用`@keyframes`规则创建动画  
使用`animation`执行动画
```css
@keyframes name{
            0%{background-color: red;}
            50%{background-color: green;}
            100%{background-color: red;}

div{animation: name 3s linear 0s infinite}
```

### 滚动条
overflow : 设置滚动条状态(hidden、auto、scroll)

### 鼠标
cursor : 改变鼠标样式(text\pointer\default\wait\help\crosshair)

### 颜色
- 英语表示：red
- 十进制表示 : rgb();
- 十六进制表示 : #000000;
- 带透明度十进制 : rgba();  

可参见：[CSS颜色](https://www.runoob.com/cssref/css-colors.html)

## 参考
{{< card "http://css.doyoe.com/" >}}        
{{< card "https://developer.mozilla.org/en-US/" >}}      
{{< card "https://www.runoob.com/css/css-tutorial.html" >}}     
{{< card "https://www.w3school.com.cn/index.html" >}}  
{{< card "https://humble-blog.vercel.app/html" >}}  

