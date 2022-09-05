---
title: "CSS3知识总结"
date: 2022-08-10T12:11:27+08:00
tags: ['Language']
series: ['前端学习之旅']
---
## 简介
1. CSS 是**层叠样式表** (Cascading Style Sheets)
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
### 外部样式表(外联式)
应用于多个页面文档时，外部样式表将是理想的选择。通过改变一个 .css 文件来改变整个站点的外观。  
在html文档中用 `<link>` 标签链接到css文档样式表。 

```html
<head>
    <link rel="stylesheet" type="text/css" href="./mystyle.css">
</head>
```
```css
/*文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。*/
/*下面是一个样式表文件的例子:*/

hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
```

### 内部样式表(内嵌式)
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
之后会配合js使用
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
- 行内样式>id选择器>类选择器>标签选择器>通配符>继承>!important(继承的)
- 类选择器 = 伪类选择器 = 属性选择器  
- 标签选择器 = 伪元素选择器

> 选择器都有一个权值，权值越大越优先；      
 当权值相等时，后出现的样式表设置要优于先出现的样式表设置；    
 继承的CSS 样式不如后来指定的CSS 样式；   

## css属性
### 元素显示模式
- 块级元素
    - 独占一行，可设置宽高，宽度为父元素的宽度，高度为内容高度
    - div、p、h、ul、li、dl、form、header、nav、footer…

- 行内元素
    - 不换行，设置宽高不生效，尺寸和内容大小相同
    - a、span、strong、del、em、i…

- 行内块元素
    - 不换行，可设置宽高
    - img、input、textarea、button、select…

- 显示模式转换
    - 改变元素默认的显示特点，让元素符合布局要求
    - 转换成块级元素 display:block
    - 转换成行内块元素 display:inline-block
    - 转换成行内元素 display:inline

- 元素嵌套规范注意点
    - 块级元素一般作为大容器，嵌套：文本、块级元素、行内元素、行内块元素…
    - p标签不要嵌套div、p、h等块级元素
    - p、h不能相互嵌套
    - a标签内部可以嵌套任意元素，但不能嵌套a标签

### 特性
1、继承性  
子元素默认继承父元素的样式特点，常见可继承的属性： 
- 控制文字的属性都可以继承，color、font-size、text-align line-height…
- 不是控制文字的属性都不可以继承，height、weight…
- a标签的color会继承失效；h系列的font-size会继承失效

2、层叠性  
选择器优先级相同时，同一标签设置相同的样式时，写在最后的样式会生效

3、优先级（见上）

4、复合选择器的优先级，通过权重叠加计算，个数高的优先级高
- （第一级行内样式个数，第二级id选择器个数，第三级类选择器个数，第四级标签选择器个数）
- 比较规则，先比较第一级数字，比较出来了，之后的统统不看；第一级相同，比较第二级，比较出来了，后面都不看了，以此类推；若每级数字都相同，表示优先级相同，则比较层叠（谁写在下面，谁说了算）
- 若都是继承，则看其父级的权重，哪个高哪个选择器生效
- 注意：!important如果不是继承，则权重最大，优先级最高，天下第一！

### 背景
- background-color : 背景颜色

- background-image : 背景图片
    -  background-image:url(图片路径);
    - 仅给盒子起到装饰效果，类似背景色，是不能撑开盒子的
    - 默认是会根据盒子宽高，在水平垂直方向平铺

- background-repeat : 背景图是否重复
    - 不平铺no-repeat；沿x轴平铺repeat-x；沿y轴平铺repeat-y；

- background-attachment : 背景图片是否固定

- background-position : 背景图片定位(可以使用%和 px 值和英语单词)
    - background-position:水平方向位置 垂直方向位置
    - background-position:left|center|right  top|center|bottom
    - background-position:50px 20px
    - 正数：向右向下移动； 负数：向左向上移动

- background: #ccc url(‘xxx.png’) no-repeat fixed 50% 50%
    - 复合属性：取值之间用空格隔开，无顺序，可按需求省略 
    - 背景图位置取值是数值时，水平垂直取值顺序不要颠倒

- background-size : 设置背景图片的尺寸

- background-origin : 设置背景图的位置
(padding-box\border-box\content-box)

背景图：起修饰美化作用的图，用 background-image    
img图：重要的图，如产品图等，用 img


### 文本
- color: 颜色  
- text-align: 水平对齐方式（默认left  center  right）
    - 给以下元素的父元素设置`text-align:center`，可实现水平居中对齐：  
    - 文本、span标签、a标签、input标签、img标签
- text-indent: 段落首行缩进（单位em，1em = 一个字的大小）
- line-height: 行高
    - 控制一行的上下行间距
    - 网页精准布局时，会设置`line-height：1 `可以取消上下间距
    - 让单行文本垂直居中，可以设置`line-height：父级元素高度`
- text-decoration: 文本修饰
    - 无装饰线none；下划线underline； 删除线line-through； 上划线overline 
- text-shadow: 设置文字阴影    
- text-transform: 文本转换大小写字母

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
- font-size：字体大小（浏览器默认文字大小是16px）
- font-weight：字体粗细（正常400；加粗700）
- font-family： 字体类型（Windows默认用：微软雅黑 ；Macos默认用：平方）
- font-style：字体样式（正常normal  斜体italic）

复合属性：一个属性冒号后面 书写多个值的写法   
`font:style weight size/line-height family  `    
有顺序，只能省略前两个style weight，省略相当于设置默认值

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
- line-height:  设置行高;单行文本垂直居中

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

### 文档流(标准流)
浏览器渲染网页内容时默认采用的一套排版规则
- 文档流产生的部分现象：
    -  块元素自上而下摆放，内联元素从左到右摆放
    -  高矮不齐，底边对齐
    -  空格折叠现象：不管你加多少空格，页面就只显示一个空格
    -  元素无间隙：放两张图片，这两张图之间会有一点点空隙

- 使一个元素脱离标准文档流有三种方式  
    - 浮动
    -  绝对定位
    -  固定定位

### 浮动和清除浮动影响  
浮动：增加一个浮层来放置内容，从而使元素脱离文档流
- `float`属性定义元素在哪个方向浮动，任何元素都可以浮动
- `float: left|right;`  浮动只有左右浮动，没有上下浮动
- 浮动后的标签具备行内块特点：在一行排列，宽高生效
- 浮动的元素不能通过text-align、margin:0 auto;无效

清除浮动带来的影响: 浮动元素会造成父元素高度塌陷、后续标准流元素会受到影响，对布局不利。  
解决方案：  
- 父元素设置高度，撑开元素本身大小
- 为受影响的元素增加clear属性` clear:both;`
- 父元素塌陷且同级元素也受到了影响（父布局不能设置高度）
    - overflow清除浮动：在父级标签的样式里加 `overflow:hidden;` `clear: both;`
    - 伪对象方式：为父标签添加伪类`::after`或`::before`，设置空的内容` content: "";`，并且使用`display: block;` `clear:both;` 

外边距塌陷：父子标签，都是块级，子级添加margin会影响父级的位置

```css
单伪元素清除法
.clearfix::after{
    content: "";
    display: block;
    clear:both;
    /* 也可不加下面两行代码，为了兼容低版本浏览器*/
    height:0;
    visibility:hidden;
}


双伪元素清除法
.clearfix::before,      /* 解决外边距塌陷问题 */
.clearfix::after {
  content: "";
  display: table;
}
.clearfix::after {     /* 清除浮动带来的影响 */
  clear: both;
}
```

### 定位
让元素自由的摆放在网页的任意位置，一般用于盒子之间的层叠情况
- 定位之后的元素层级最高，可以层叠在其他盒子上面
 - 可以让盒子固定在屏幕中的某个位置  

设置定位方式
- position:
    - `absolute`  绝对定位(脱离文档流，释放文档流中的位置)，不占有原来位置，改变标签的显示模式特点，具备行内块特点，相对于已定位的父级进行移动，若没有这样的父级，就以浏览器窗口为参照移动。（加宽高生效，若没有宽度也没有内容，盒子的宽度尺寸就是0）
    - `relative`  相对定位(遵循文档流，自己是原点)，占有原来的位置，仍具备标签原有的显示模式特点，相对于自己原来位置移动，配合方位属性实现移动。

    - `fixed`  固定定位(脱离文档流，相对于浏览器窗口是固定位置,不随窗口滚动)，不占位置，具备行内块特点。
    - static  静态定位(遵循正常的文档流对象)，即不定位

方位属性设置偏移值，水平给一个垂直给一个就可以，离哪个近给哪个
- left : 水平，设置左侧距原点的长度
- top : 水平，设置上方的距原点的长度
- right : 垂直，设置右侧距原点的长度
- bottom : 垂直，设置底部距原点的距离

元素层级问题
- 定位>浮动>标准流
- 相对、绝对、固定默认是层级相同
- 定位的盒子，后来者居上

Z-index:整数；  
- 设置元素的堆叠顺序（谁的Z-index值大，就能压盖Z-index值小的，可为负值）
- Z-index值默认是0
- 必须配合定位才生效

vertical-align  
- 设置元素的垂直对齐方式
- 浏览器解析行内、行内块，都当作文字来处理
- 针对行内块和文字、行内块和行内块的对齐问题

|属性值|效果|
|:--|:--|
|baseline|默认，基线对齐|
|top|顶部对齐|
|middle|中部对齐|
|bottom|底部对齐|

子绝父相  
- 子级用绝对定位，父级用相对定位，让子级相对于父级位置进行移动（这里父级含义包括爷爷、太爷爷……）
- 使用margin：0 auto；进行居中，不生效了
- 子盒子在父盒子中水平、垂直居中：
```css
.box{
    position:absolute;
/* 整个盒子移动到浏览器中间偏右的位置 */
    left:50%;
/* 把盒子向左侧移动：自己宽度的一半 */
    margin-left:-150px;

/* 整个盒子移动到浏览器中间偏下的位置 */
    top:50%;
/* 把盒子向上移动：自己高度的一半 */
    margin-top:-150px;
}

/* 移动先使用 margin，因为transform有时候会有层叠问题 */

或者
.box{
    position:absolute;
/* 整个盒子移动到浏览器中间偏右的位置 */
    left:50%;

/* 整个盒子移动到浏览器中间偏下的位置 */
    top:50%;

/* 位移：自己宽度高度的一半 */
    transform:translate(-50%,-50%);
}
```


### 显示和隐藏
- display:
    - none 隐藏不占位
    - block 块显示
    - inline 行内显示
```css
.nav li a:hover img{
    display:block;
}
```
- visibility:
    - hidden 隐藏占位
    - visible 显示

- opacity 设置透明度，让元素整体（包括内容）一起变透明，取值0-1之间的数字
    - 1：表示完全不透明
    - 0：表示完全透明

## 选择器（符）
### 通配符
以`*`来定义   
结构：`*{css属性名：属性值;} `   
为页面上所有的标签，设置样式     
可以与任何元素匹配，但优先级最低，`一般做样式初始化`
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
结构：`标签名{css属性名：属性值;}`    
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
结构：`.类名{css属性名：属性值;}`    
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
②  类名**不能以数字、中划线开头**  
③ 同一个标签可以使用多个类选择器。**用空格隔开**  
④ 类名可以重复，一个类选择器可以同时选中多个标签

### id选择器
以`#`来定义  
结构：`#id属性值{css属性名：属性值;}`  
针对某一个特定的标签来使用，只能使用一次。  
基本配合 js 来使用
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
① ID是唯一的，id的名称不能重复。类似于身份证号码  
② ID不能以数字开头  
③ 一个标签上只能有一个id属性值  
④ 一个id选择器只能选中一个标签

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
|`E:hover`	|CSS1/2	|设置元素在其鼠标悬停时的样式。|
|E:active|	CSS1/2	|设置元素在被用户激活（在鼠标点击与释放之间发生的事件）时的样式。|
|E:focus	|CSS1/2	|设置元素在成为输入焦点（该元素的onfocus事件发生）时的样式。|
|`E:first-child`	|CSS2|	匹配父元素的第一个子元素E。|
|`E:last-child`	|CSS3|	匹配父元素的最后一个子元素E。|
|E:only-child	|CSS3|	匹配父元素仅有的一个子元素E。|
|`E:nth-child(n)`|	CSS3|	匹配父元素的第n个子元素E。|
|`E:nth-child(公式)`|	CSS3|	匹配父元素的第公式个子元素E。公式如下|
|E:nth-last-child(n)|	CSS3|	匹配父元素中倒数第n个子元素E。|
|E:empty	|CSS3	|匹配没有任何子元素（包括text节点）的元素E。|
|E:checked	|CSS3	|匹配用户界面上处于选中状态的元素E。(用于input type为radio与checkbox时)|
|E:disabled|	CSS3	|匹配用户界面上处于禁用状态的元素E。|

注意：n为0、1、2、3、4、5、6……
|功能|	公式||
|:-|:-|:--|
|偶数|2n|2的倍数|
|奇数|2n+1|
|找到前5个|-n+5|
|找到从第5个往后|n+5|



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

### 伪元素选择器
伪元素：由css模拟出的标签效果  
- 网页中的一些装饰的不重要的小图就可以用伪元素选择器编写  
- 伪元素默认是行内元素

|选择符|	描述|
|:-|:-|
|E::first-letter|	设置对象内的第一个字符的样式。|
|E::first-line	|设置对象内的第一行的样式。|
|`E::before`	|设置在对象前（依据对象树的逻辑结构）发生的内容。必须和 content 属性一起使用|
|`E::after`	|设置在对象后（依据对象树的逻辑结构）发生的内容。必须和 content 属性一起使用|
|`E::placeholder`|设置对象文字占位符的样式。可用于表单输入框的信息提示文本|
|E::selection	|设置对象被选择时的颜色。|

```css
E::before{           /* 大米E */
    content:"大米";
}

E::after{           /* E大米 */
    content:"大米";
}
```

## 布局
### 盒子模型
每一个标签都可以看作一个“盒子”；css规定每个盒子分别由：        
内容区域(content)，内边距区域(padding)，边框区域(border)，外边距区域（margin）

![1de8a1d57796e5f98d7768fd89d9186](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220807/1de8a1d57796e5f98d7768fd89d9186.5ezwq52ipbs0.webp)

1. content(实际内容):盒子的内容，显示文本和图像
2. padding(内边距)：清除内容周围的区域(两个值的话：第一个值上下，第二个值左右)；出现在内容和纸箱子边框之间。
3. border(边框):围绕在内边距和内容外的边框（三个值的话：第一个值边框粗细，第二个值实线，第三个值颜色）；纸箱子（内容宽高区域加个边框）。
4. margin（外边距):清除边框外的区域，外边距是透明的(两个值的话：第一个值上下，第二个值左右)；出现在盒子外面，两个纸箱子之间的距离。

5. 自动内减：给盒子添加属性`box-sizing:border-box;`  
即可解决border、padding会撑大盒子的问题，浏览器自己计算多余大小自动在内容中减去

6. 清除默认内外边距：
有些标签有默认自带的内外边距，比如body、p、ul等
```css
*{              
    margin:0;         /* 清除默认内外边距 */
    padding:0;
}
```
7. 外边距塌陷问题：给父级添加 `overflow:hidden;`  
互相嵌套的块级元素，子元素的margin-top会作用在父元素上，导致父元素一起往下移动。 

8. 行内标签的垂直居中，添加：`line-height`  
设置上下内边距padding-top|bottom、上下外边距 margin-top|bottom，是不生效的。
    

- 如果把盒子模型看作是一个生活中的快递，那么内容部分等同于你买的实物，内边距等同于快递盒子中的泡沫，边框等同于快递盒子，外边距等同于两个快递盒子之间的距离

- chrome调试工具中：蓝色是内容宽高；绿色是内边距padding；橙色黄色是外边距margin。

-  border会撑大盒子，宽400px高400px，边框10，结果盒子就会变成宽420px高420px，要想盒子为宽400px高400px，则尺寸就得设置成宽380px高380px。

- padding也会撑大盒子，也是同 border一样减掉。取值顺时针转一圈，上下左右；上 右 下 左；上 左右 下；上下 左右；


```html
<head>
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: green;
            padding: 20px 20px;
            border: 5px solid blue;    /* 虚线dashed，点线dotted*/
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

                    /*border-left、border-right、border-top*/
            border-bottom: 5px solid blue;   
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
### Flex布局/弹性布局
- 是CSS3的一种新的浏览器提倡的布局模式；灵活控制块级项目的布局方式，避免浮动布局脱标的问题   
- CSS3弹性盒是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式；  
- 引入弹性布局模型的目的是提供一种更加有效的方式来`对一个容器中的子元素进行排列、对齐和分配空白空间`
- IE6-9版本不支持Flex布局，关于浏览器是否兼容可查询：[caniuse](https://caniuse.com/)


#### 基本概念
- 由弹性容器（Flex container）、弹性子元素/项目(Flex item)、主轴、侧轴（交叉轴）组成  （方向可改变） 
- 通过设置`display:flex`将其定义为弹性容器，容器内包含了一个或多个项目（弹性子元素  ）

`主轴默认是水平方向`，侧轴默认是垂直方向：
![c609167878e2e2d5fe55e5785c9aea6](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220825/c609167878e2e2d5fe55e5785c9aea6.6dk02ago08g0.webp)

- 任何一个容器都可以指定为 Flex 布局

```css
.box{
  display: flex;
}

/* 行内元素也可以使用 Flex 布局 */
.box{
  display: inline-flex;
}
```

#### 容器的属性（亲父元素）
- 给亲父元素先必须添加`display:flex;`开启弹性布局。容器里子项目会横向摆放（块级变成行内 ）
- 项目是沿着主轴进行排列的。   

- 以下6个属性设置在容器上
    |属性|  说明|
    |:--|:--|
    |display:flex|开启弹性布局|
    |justify-content|项目在主轴上的排列对齐方式|
    |align-items|项目在交叉轴上的排列对齐方式|
    |flex-direction|修改主轴方向|
    |flex-wrap|项目换行|
    |flex-flow|flex-direction和flex-wrap属性的简写形式。默认值为row nowrap|
    |align-content|

1、`justify-content`  
- 定义了项目在主轴上的排列对齐方式。

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列（左对齐）|
    |flex-end|终点开始依次排列（右对齐）|
    |`center`|居中|
    |space-between|两端对齐，项目之间的间隔都相等|
    |space-around|每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。|
    |space-evenly|项目与容器、容器与容器，间距都相等|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.st1evmf8dzk.webp)

2、`align-items`
- 定义项目在交叉轴上的排列对齐方式 

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列|
    |flex-end|终点开始依次排列|
    |`center`|沿侧轴居中排列|
    |baseline|项目的第一行文字的基线对齐|
    |stretch|默认值，如果项目未设置高度或设为auto，将占满整个容器的高度|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.2fh6v177807w.webp)

3、`flex-direction`
- 决定主轴的方向（即项目的排列方向）。
- 修改主轴方向，主轴若竖着，侧轴就自动默认横着。

    |属性值|作用|
    |:--|:--|
    |row|水平（默认值）从左到右|
    |`column`|垂直，从上到下|
    |row-reverse|水平，从右向左|
    |column-reverse|垂直，从下向上|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.rc5wnog5l6o.webp)

4、`flex-wrap`
- Flex布局，默认沿着主轴排不换行，父级宽度不够，子级就自动挤压来适应父级宽度
- 实现一条轴线排不下，项目进行换行，多行排列效果

    |属性值|作用|
    |:--|:--|
    |nowrap|默认值，不换行|
    |`wrap`|换行，第一行在上方|
    |wrap-reverse|换行，第一行在下方|

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.1rno17iwa0hs.webp)

![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.3t5e8ffg2k40.webp)

5、`flex-flow`
- flex-flow属性是flex-direction属性和flex-wrap属性的简写形式
- 默认值为row nowrap。

6、`align-content`
- 定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

    |属性值|作用|
    |:--|:--|
    |flex-start|默认值，起点开始依次排列|
    |flex-end|终点开始依次排列|
    |`center`|居中排列|
    |space-between|与交叉轴两端对齐，轴线之间的间隔平均分布|
    |space-around|每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍|
    |stretch|（默认值）轴线占满整个交叉轴|

    ![image](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220902/image.5mhekyijw000.webp)


#### 项目的属性（亲儿子元素）

- 以下6个属性设置在项目上
    |属性|  说明|
    |:--|:--|
    |align-self|控制某个子级项目在侧轴的对齐方式|
    |flex|复合属性。`flex:取值整数`，占用父级剩余尺寸的份数|
    |order|定义项目的排列顺序。数值越小，排列越靠前，默认为0。一般设置负数，使其靠前|
    |flex-grow|定义项目的放大比例。默认为0不放大|
    |flex-shrink|定义了项目的缩小比例。默认为1，即空间不足，都将等比例缩小|
    |flex-basis|定义了在分配多余空间之前，项目占据的主轴空间。默认值为auto，即项目的本来大小|

1、`align-self`  
- 控制某一个子级项目在侧轴的对齐方式（给子元素添加） 
- 可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
- 可能取6个值，除了auto，其他都与align-items属性完全一致

|属性值|作用|
|:--|:--|
|flex-start|默认值，起点开始依次排列|
|flex-end|终点开始依次排列|
|`center`|沿侧轴居中排列|
|stretch|默认值，项目沿着主轴线被拉伸至铺满容器|
|baseline|项目的第一行文字的基线对齐|


2、`flex`  
- flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
- 弹性伸缩比，使用flex属性修改项目子元素的宽度尺寸。`flex:取值整数`，占用父级剩余尺寸的份数。

比如：给外层容器`container`增加弹性容器的设置，就可以刚好的管理里面的这三个子项目`box1、box2、box3`，纵向摆放变成了横向摆放。
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

3、`order`  
- 定义项目的排列顺序。数值越小，排列越靠前，默认为0。一般设置负数，使其靠前。

4、`flex-grow`   
- 定义项目的放大比例。默认为0，即如果存在剩余空间，也不放大。  
- 如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

5、`flex-shrink`  
- 定义了项目的缩小比例。默认为1，即如果空间不足，各项目都将等比例缩小。
- 如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
- 负值对该属性无效。

6、`flex-basis`  
- 定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
- 它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。
    
> 提示：  
>①默认弹性容器里内容横向摆放  
>②弹性容器外、弹性子元素内是正常渲染的。只定义了弹性子元素如何在弹性容器内布局


### 百分比布局
- 即宽度`%`数的写法，百分比布局也叫流式布局
- 效果：宽度自适应百分比%，高度固定px  

百分比布局是早期的布局方法，现在不仅追求宽度自适应，高度也要自适应了。所以此种布局不太适应当今追求。


### 网格布局
一、概念
- 网格是一组相交的水平线和垂直线，它定义了网格的列和行。
- CSS 提供了一个基于网格的布局系统，带有行和列，可以让我们更轻松地设计网页，而无需使用浮动和定位。

二、网格元素
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
### css书写顺序
这样写，浏览器执行效率会更高些  
1、浮动、display
2、盒子模型：margin、border、padding、宽度高度、背景色
3、文字样式

### 媒体查询
- 响应式网页：同一代码，适配不同屏幕宽度
- 媒体查询能使页面在不同的终端设备下达到不同的效果，根据设备的大小自动识别加载不同的样式  

1、设置meta标签：使用设备的宽度作为视图宽度并禁止初始的缩放。在`<head>`标签里加入这个`meta`标签

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


                         /*设备大于992px加载样式，电脑*/
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

2、css属性都有层叠性，所以要按书写顺序来写
- min-width （从小到大）
- max-width （从大到小）

```css
/* 工作中简化写法 */
@media (min-width:768px) {      /* 视口宽度大于等于768px */
    .box{
        background-color: blue;
    }
}
@media (min-width:992px) {    
    .box{
        background-color: red;
    }
}
@media (min-width:1200px) {    
    .box{
        background-color: green;
    }
}
```

3、外链式css引入
```html
<head>
    <link rel="stylesheet" href="./one.css" media="(min-width:992px)">
</head>
```
4、隐藏  
一般电商站的响应式网页会涉及隐藏
```css
/* 如果检测到视口宽度小于768px，认为是手机端，将left隐藏 */
@media (max-width:768px){
    .left{
        display:none;
    }
}
```
> 后续对于设计响应式网页，可以使用 BootStrap 框架


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
### 版心
```css
margin:0 auto;      /* 版心居中 */
```

### 精灵图（雪碧图）
1. 项目中将多张小图片，合并成一张大图片，这张大图片称之为精灵图。
    - 合成一张精灵图发送，仅发送1次
    - 优点：减少服务器发送次数，减轻服务器压力，提高页面加载速度

2. 使用步骤
    - 创建一个盒子，设置盒子尺寸和小图尺寸相同
    - 将精灵图设置为盒子的背景图片background-image:url();
    - 修改背景图位置，通过PxCook测量出小图片以大图左上角为原点的坐标值，分别取负值给盒子的background-position:x y; 再结合chrome调式工具微调修改坐标值

3. 背景图大小  
background-size:宽度 高度；

|取值|场景|
|:--|:--|
|数字+px|简单方便，常用|
|百分比|相当于当前盒子自身的宽高百分比|
|contain|包含，将背景图等比例缩放，直到不会超出盒子的最大|
|cover|覆盖，将背景图等比例缩放，直到刚好填满整个盒子没有空白|

缩写 background：color image repeat position/size;

### 网页标题图标
.ico格式的图标

```html
<head>

 <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">

</head>
```

### 字体图标
可实现网页中简洁的图标效果
- 简单的、颜色单一的图片使用字体图标（复杂图用css精灵图）
- 展示的是图标，本质上是字体
- 优点：可灵活地修改尺寸、颜色；体积小渲染快；兼容性大，使用方便。

使用：
1. 下载字体包，常用字体图标库：[阿里字体图标库](https://www.iconfont.cn/)
2. 登录账号，素材库官方图标库，添加购物车，加入项目，新建项目，下载至本地
3. 解压，将文件复制到自己项目文件夹目录下，打开demo_index.html选择font-class引用
4. 根据步骤编写代码
5. 注意调用图标的类名，必须调用2个类名
    - iconfont 固定类名，基本样式包含字体的使用等
    - icon-xxxx 图标对应的类名（点后面的，不带点）

```html
<head>
           <!-- 引入字体图标样式表 -->
    <link rel="stylesheet" href="./font/iconfont.css">

           <!-- 调用字体图标的类名 注意不带点 -->
    <style>
        .install{
            font-size: 100px;     <!-- 设置字体图标的样式-->
            color: #e1251b;
        }

    </style>

</head>
<body>
              <!-- 调用字体图标的类名 注意不带点 -->
    <span class="iconfont icon-shezhi"></span>

</body>
```
6. 若图标库没有所需图标，怎么办？
那就在iconfont网站上传矢量图，生成字体图标
- 与设计师沟通，得到SVG矢量图
- iconfont网站上传图标（去除颜色提交），下载使用

### 圆角边框
border-radius:一个值|两个值|三个值|四个值
- 数字+px、百分比
- 从左上角开始赋值，然后顺时针赋值，没有赋值的看对角与对角一样
- 正圆：盒子得是正方形，设置边框圆角为盒子宽高的一般 border-radius:50%；
- 胶囊按钮：盒子是长方形，设置border-radius:盒子高度的一半

### 盒子阴影
box-shadow: 给盒子添加阴影效果 6个值

|参数|作用|
|:--|:--|
|h-shadow|必须，水平偏移量，允许负值|
|v-shadow|必须，垂直偏移量，允许负值|
|blur|可选，模糊度|
|spread|可选，阴影扩大|
|color|可选，阴影颜色|
|inset|可选，将阴影改为内部阴影|

### 过渡
作用：让元素的样式慢慢的变化，常配合hover使用  
transition:
|参数|取值|
|:--|:--|
|过渡的属性|全部变化all，或者单独设置height、 width……|
|过渡的时长|数字+s(秒)|

```css
.box{
    width:200px;
    height:200px;
    background-color:red;

    transition:width 1s, background-color 2s;
    /* transition:all 3s */
}
.box:hover{
    width:600px;
    background-color:blue;
}
```
### 平面转换
使用transform属性实现平面内元素的位移、旋转、缩放等效果
- 改变盒子在平面内的形态（位移、旋转、缩放）
- 2D转换  

位移  
1. `transform:translate(水平移动距离，垂直移动距离)；`
    - 取值正负均可，x轴正向为右，y轴正向为下，单位px
    - 单位% （参照物为盒子自身尺寸）
    - transform：translate(一个值)；表示x轴方向移动距离
    - 单独设置某个方向的移动距离：
        - transform：translateX（20px）; x轴方向移动距离
        - transform：translateY（30px）; y轴方向移动距离
```css
/* 鼠标移动到父盒子，son改变位置 */
.father:hover .son{
    transform:translate(50px 100px)；
}
```
2. 绝对定位居中
```css
.box{
    position:absolute;
/* 整个盒子移动到浏览器中间偏右的位置 */
    left:50%;

/* 整个盒子移动到浏览器中间偏下的位置 */
    top:50%;

/* 平面位移：自己宽度高度的一半 */
/* 单位% 参考盒子自身尺寸计算结果 */
    transform:translate(-50%,-50%);
}
```
3. 双开门布局
```css
.box::before,
.box::after{
    float:left;
    content:"";
    width:50%;
    height:600px;
    background-image:url(./images/fm.jpg)

     /* 全部过渡，时间0.5s */
    transition:all .5s;

    /* 产出父级范围的隐藏 */
    overflow:hidden;

}

/* 单独控制 after的背景图位置 */
.box::after{
    background-position:right 0;
}

/* 鼠标移入box, before向左移动100%*/
.box:hover::before{
    transform:translate(-100%);
}

/* 鼠标移入box,after向右移动100%*/
.box:hover::after{
    transform:translate(100%);
}
```

旋转  
transform：rotate(角度);  
- 注意：角度单位deg  
- 取值正负均可：正顺时针旋转，负逆时针旋转

转换原点  
使用transform-origin属性改变转换原点  
- transform-origin：原点水平位置  原点垂直位置；
- 默认原点是盒子中心
- 取值
    - 方位名词（left、top、right、bottom、center）
    - 像素单位数值
    - 百分比（参照盒子自身尺寸计算）
- 注意添加给标签本身，不要给hover 

多重转换：边走边转 
```css 
/* 不能颠倒顺序，先旋转会改变坐标轴向，位移方向受到影响 */
/* 多重转换如果涉及旋转，就往后书写 */
transform:translate() rotate();
```
缩放  
使用scale改变元素的尺寸   
- transform:scale(x轴缩放倍数，y轴缩放倍数);
- transform:scale(缩放倍数);
    - 一般情况下，只为scale位置一个值，表示x轴y轴等比例缩放
    - scale值大于1表示放大，小于1表示缩小
- 伪元素、hover的transform会有层叠问题，要写成复合属性，不要分开

渐变  
多个颜色逐渐变化的视觉效果，一般用于设置盒子的背景  
```css
background-image:linear-gradient(颜色1，颜色2，颜色3);

/* 半透明渐变     transparent:透明*/
background-image:linear-gradient(
    transparent，
    rgba(0,0,0,0.5)
);
```
空间转换（先略）


### 滚动条
盒子内容部分超出盒子范围的区域，溢出部分显示效果  
overflow:
|属性值|效果|
|:--|:--|
|visible|默认值，溢出部分可见|
|hidden|溢出部分隐藏|
|scroll|无论是否溢出，都显示滚动条|
|auto|根据是否溢出，自动显示或隐藏滚动条|

### 鼠标
cursor :设置鼠标光标在元素上时显示的样式
|属性值|效果|
|:--|:--|
|default|默认值，箭头|
|pointer|小手效果，提示用户可以点击|
|text|工字形，提示用户可以选择复制文字|
|move|十字光标，提示用户可以移动|
|wait||
|help||
|crosshair||


### 标签（大盒子）水平居中
- 让div、p、h（大盒子）水平居中，直接给`当前元素本身设置`
- 可以通过添加 `margin:0 auto;`来实现
- margin:0 auto一般针对于固定宽度的盒子，如果大盒子没有设置宽度，此时会默认占满父元素的宽度

### emmet语法
通过简写语法，快速生成代码  
html文档：
|记忆|示例|效果|
|:--|:--|:--|
|标签名|div|`<div></div>`|
|类选择器|.red|`<div class="red"></div>`|
|id选择器|#one|`<div id="one"></div>`|
|交集选择器|p.red#one|`<div class="red" id="one"></div>`|
|子代选择器|ul>li |`<ul><li></li></ul>`|
|内部文本|ul>li{我是li的内容}|`<ul><li>我是li的内容</li></ul>`|
|创建多个|ul>li*3|`<ul><li></li><li></li><li></li></ul>`|

css文档：首字母
|示例|效果|
|:--|:--|
|bgc|background-color|
|bgi|background-imge|
|lh|line-height|
|fs|font-size|
|w| width|
|h|height|
|w300+h200+bgc| width:300; height:200; background-color:#fff;|


### 颜色
文字颜色：color  
背景颜色：background-color
- 英语表示：red
- 十进制表示 : rgb(255,255,255);
- 十六进制表示 : #000000;
- 带透明度十进制 : rgba(188,10,18,0.3);  a是透明度 取值为0-1

可参见：[CSS颜色](https://www.runoob.com/cssref/css-colors.html)


## 进阶
### 移动端认知
1、PC端和移动端的网页区别：
- PC屏幕大，网页宽度有固定版心
- 手机屏幕小，网页宽度多数100%  

2、如何在电脑里边写代码边调试移动端网页效果：
- 谷歌模拟器（调整到移动端，刷新下网页）

3、移动端主流设备分辨率
- 屏幕尺寸：指屏幕对角线的长度，一般用英寸来度量
- pc分辨率
    - 1920x1080、1366x768……
    - 缩放150%，即（1920/150%）x（1080/150%）
    - 硬件分辨率（出厂设置）；缩放调节的分辨率（软件设置）
- 分辨率分类
    - 物理分辨率：生产屏幕时固定的，不可被改变
    - 逻辑分辨率：软件（驱动）决定的
    - 制作网页是参考逻辑分辨率。
- 设计师一般以iPhone6/7/8出设计稿，iPhone6/7/8手机分辨率：
    - 物理分辨率 750x1334 
    - 逻辑分辨率375x667

4、视口
- pc端，html标签尺寸默认就是电脑分辨率，屏幕充满100%
-手机端，html标签尺寸默认是980px,所以要加视口代码
```html
 <!--宽度等于设备宽度：移动端网页开发的时候用到-->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

5、二倍图  
为了高分辨率下图片不会模糊失真
- 设计师一般以iPhone6/7/8，物理分辨率 750x1334 出设计稿，宽750px分辨率的图就叫做二倍图
- 但我们要根据，逻辑分辨率375px来编写代码，`即PxCook测量元素尺寸时，将开发模式的设计图选2x`。

### 移动适配（rem、vw/vh）
移动适配：网页所有元素的宽高，都要随着不同设备的宽度自适应变化  

#### rem    
1、rem是目前多数企业在用的解决方案。
- 用`rem单位`设置网页元素的尺寸
    - 相对单位，相对于HTML根标签的字号计算结果
    - 1rem=1HTML字号大小
```css
html{
    font-size:20px;
}

/* 即 box的尺寸是：宽100px,高60px */
.box{
    width:5rem;
    height:3rem;
    background-color:pink;
}
```
2、媒体查询    
- 通过不同移动设备，设置不同的HTML字号大小，则使用rem就完成了适配
- 媒体查询能够检测视口的宽度，然后编写差异化的css样式
- HTML标签字号为视口宽度的1/10
- 写法举例：

```css
/* HTML标签字号为视口宽度的1/10 */

@media(width:414px){
    html{
        font-size:41.4px;
    }
}

@media(width:375px){
    html{
        font-size:37.5px;
    }
}

/* box尺寸是68*29 */
/* 设计稿375，HTML37.5， 68/37.5  29/37.5   */
.box{
    width:1.813rem;
    height:0.773rem;
    background-color:pink;
}

```

3、移动适配
使用`flexible.js配合rem`实现在不同宽度的设备中，网页元素尺寸等比缩放效果
- flexible.js是手陶开发出的一个用来适配移动端的js框架
- 原理：根据不同的视口宽度，给网页中html根节点设置不同的font-size。
```html
         <!-- 在html文档中，引入js文件 -->
<body>

    <script src="../js/flexible.js"></script>
</body>
```

#### vw/vh  
未来会流行的解决方案，目前个别大厂已经转型在用，比如B站、天猫。
1、相对单位，相对`视口的尺寸`计算结果 
- vw：viewport width
    - 1vw=1/100视口宽度

- vh：viewport height
    - 1vh=1/100视口高度

```css
.box{
    width:50vw;      /* 3.75x50=187.5px */
    height:30vw;    /* 3.75x30=112.5px */
    background-color:pink;
}
```

2、移动适配
不同宽度的设备，网页元素尺寸等比缩放

```less
/* box尺寸是68*29 */
/* 设计稿375，1vw=3.75， 68/3.75  29/3.75   */
.box{
    width:(68 / 3.75vw);
    height:(29 / 3.75vw);    /* 不允许vw、vh混用，因为全面屏会受到影响 */
    background-color:pink;
}
```

### Less
1、简介
- less就是快速编译生成css代码的一个工具，less文件后缀是`.less`  
- 扩充css语言，使css具备一定的逻辑性、计算能力。如，完成px单位到rem单位的转换（ 如68/37.5=1.813rem）  
- 安装vscode插件：EasyLess。`.less`文件保存后，会在同级目录下自动生成一个`.css`文件

```less
.father{
    width:(68 / 37.5rem);

    .son{
        background-color:pink;
    }
}
```
会自动生成下面的css代码
```css
.father{
    width:(68 / 37.5rem);
}

.father .son{
        background-color:pink;
    }
```

2、注释
- 单行注释
    - 语法：//注释内容
    - 快捷键：ctrl+/
- 块注释
    - `/*注释内容*/`
    - 快捷键：ctrl+shift+/ 

单行注释在css里是不显示的，但也没关系，因为css是给浏览器看的，开发人员看的是less

3、计算
- 加、减、乘，直接书写计算表达式
- 除法需要添加`小括号`或`.`

```less
.box{
    width:100 + 50px;
    height:5 * 32px;

    width:(100 / 5rem);  (推荐)
    height:500./10rem;
}
```
4、快速生成后代选择器  
注意：`&`不生成后代选择器，表示当前选择器，通常配合伪类或伪元素使用
```less
.father{
    color:red;
    .son{
        background-color:pink;
        &:hover{
            background-color:green;
        }
    }
}
```

会自动生成下面的css文件代码
```css
.father{
    color:red;
}

.father .son{
        background-color:pink;
}

.father .son:hover{
        background-color:green;
}
```

5、变量
存储数据，方便使用和修改
- 比如把颜色提前存储到一个容器，设置属性值为这个容器名
- 语法：
    - 定义变量：`@变量名:值;`
    - 使用变量：`css属性:@变量名;`

```less
@colora:red;
                // 凡是红色，都可以调用 @colora
.box{
    color:@colora;
}

.father:{
    color:@colora;
}
```

6、导入  
- 开发网站时，less文件中，可以使用`less导入`写法引用其他less文件代码
- 此导入是把引用的文件里的所有代码导入对应的css文件里
- 导入：`@import "文件路径";` （注意加空格）

```less
@import "./base.less";   // 导入代码写在less文件开头
@import "./common.less";  // 如果是less文件，可以省略后缀.less
```

7、导出  
`.less`文件保存后，会在同级目录下自动生成一个`.css`文件。但，我们希望css文件就在css文件夹，less文件就在less文件夹   

导出css文件的方法：  
1、配置EasyLess插件，实现所有less有相同的导出路径
- 设置——搜索EasyLess——在setting.json中编辑——添加代码（注意，必须是双引号）

```
"less.compile": {
        "out": "../css/"
    }
```
2、单独导出路径
- 必须在less文件第一行，写入代码。
- 如，将css文件保存到abc文件夹
```
// out: ./abc/
```
- 如，将css文件保存到qqq文件夹，文件命名为lisa
```
// out: ./qqq/lisa.css
```
- 如，将css文件保存到与less文件同级目录下
```
// out: ./
```

3、禁止导出  
- 并不是所有的less文件都需要导出css文件，比如base.css、common.css 是被引入的文件  
- 禁止导出css文件，必须在less文件第一行添加：`// out: false`


## 参考
{{< card "http://css.doyoe.com/" >}}        
{{< card "https://developer.mozilla.org/en-US/" >}}      
{{< card "https://www.runoob.com/css/css-tutorial.html" >}}     
{{< card "https://www.w3school.com.cn/index.html" >}}  
{{< card "https://humble-blog.vercel.app/html" >}}  

