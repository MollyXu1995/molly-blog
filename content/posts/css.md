---
title: "草稿css"
date: 2022-08-04T16:20:44+08:00
tags: ['Essay']
---
## CSS简介、语法
使用CSS的唯一目的就是**让网页具有美观**一致的页面
### CSS概念
CSS（Cascading Style Sheets）**层叠样式表**，又叫级联样式表，简称样式表。  
CSS文件后缀名为`.css`  
***CSS用于HTML文档中元素样式的定义***
### 语法
CSS规则由两个主要的部分构成：选择器、一条或多条声明(样式)

![80c8a4f7efc332ccffc90dd4d801ec4](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/80c8a4f7efc332ccffc90dd4d801ec4.2gib7q601mjo.webp)

- 选择器通常是您需要改变样式的HTML元素 
- 每条声明由一个属性和一个值组成
- 属性（property）是您希望设置的样式属性(style attribute)。每个属性有一个值。属性和值被冒号`:`分开。属性与属性之间用`;`分号隔开。 
```html
<head>
    <style>
        h1{
            color: blue;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <h1>标题内容</h1>
</body>
```

---
## CSS的样式
把CSS和HTML合起来（关联上）
### 内联样式（行内样式）
要使用内联样式，你需要在相关的标签内使用样式（Style）属性，Style属性可以包含任何CSS属性
> 提示：  
缺乏整体性和规划性，不利于维护，维护成本高
```html
<body>
    <p style="color: red;font-size: 40px;">内联样式的方案</p>
</body>
```
### 内部样式
当单个文档需要特殊的样式时，就应该使用内部样式表，你可以使用`<style>`标签在文档头部定义内部样式表
> 提示：  
单个页面内的CSS代码具有统一性和规划性，便于维护，但是多个页面之间容易混乱
```html
<head>
    <style>
        h3{
            color: blue;
            font-size: 30px;
        }
    </style>
</head>
<body>
    <h3>标题内容</h3>
    <h3>你是我的小苹果</h3>
</body>
```
### 外部样式（推荐）
**当样式需要应用于很多页面时**，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。 

每个页面使用`<link>`标签链接到样式表。`<link>`标签在（文档的）头部

创建`.css`文件，注意只能写css语言，不能写html语言  

public.css文件里编写：
```css
p{
    color: green;
    font-size: 30px;
}
h4{
    color: pink;
    font-size: 50px;
}
```

public.html文件里编写：
```html
<head>
    <link rel="stylesheet" href="./public.css">
</head>
<body>
    <p>导航</p>
    <a href="./index.html">产品</a>
    <h4>手机</h4>
</body>
```

index.html文件里编写：
```html
<head>
    <link rel="stylesheet" href="./public.css">
</head>
<body>
     <p>我是产品</p>
     <h4>电脑</h4>
</body>
```

---
## 选择器一
CSS规则由两个主要的部分构成：**选择器**、一条或多条声明(样式)  
![图例](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220804/80c8a4f7efc332ccffc90dd4d801ec4.2gib7q601mjo.webp)
### 全局选择器
**可以与任何元素匹配，但优先级最低**，一般做样式初始化
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
### 元素选择器
HTML文档中的元素，`p、b、div、a、img、body`等。
标签选择器，选择的是页面上所有这种类型标签，所以经常描述“共性”，无法描述某一个元素的“个性”
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

再比如说，我想让“先吃西瓜苹果，再吃米饭”这句话，“苹果”变为红色字体，那么可以用`<span>`标签把“苹果”两个字围起来，然后给`<span>`标签加一个标签选择器
```html
<head>
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
规定用圆点`.`来定义，针对你想要的所有标签使用
> 优点：灵活
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
> class属性的特点  
①  类选择器可以被多种标签使用  
②  类名不能以数字开头  
③同一个标签可以使用多个类选择器。**用空格隔开**
```html
正确编写
 <p class="content size">我又哭了</p>

错误编写
<p class="content" class="size">我又哭了</p>
```

### ID选择器
针对某一个特定的标签来使用，只能使用一次。
`css`中的`ID选择器`以`#`来定义
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

### 合并选择器
语法：`选择器1,选择器2…{}`  
作用：提取共同的样式，减少重复代码的编写
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

### 选择器的优先级
CSS中，权重用数字来衡量，权重数字越大，优先级越高。  
- 元素选择器的权重为：1  
- class选择器的权重为：10   （类选择器）
- ID选择器的权重为：100  
- 内联样式的权重为：1000    （行内样式）

优先级从高到低：内联样式>ID选择器>类选择器>元素选择器

同级覆盖，绿会把红覆盖，只显示绿色
```html
<head>
    <style>
        .t1{
            color: red;
        }
        .t2{
            color: green;
        }
    </style>
</head>
<body>
    <p class="t1 t2">降龙十八掌</p>
</body>
```

---
## 关系选择器
1. 后代选择器
2. 子代选择器
3. 相邻兄弟选择器
4. 通用兄弟选择器
### 后代选择器
选择所有被E元素包含的F元素，中间用**空格**隔开
```CSS
E F{}
```
```html
<head>
    <style>
        ul li{
            color: green;
        }
    </style>
</head>
<body>
    <ul>
        <li>列表1</li>
        <li>列表2</li>
        <li>列表3</li>
        <div>
            <ol>
                <li>列表4</li>
                <li>列表5</li>
            </ol>
        </div>
    </ul>
</body>
```
### 子代选择器
选择所有作为E元素的直接子元素F，对更深一层元素不起作用，用>表示
```CSS
E>F{}
```
只有“大家好”有颜色
```html
<head>
    <style>
         div>p{
            color: red;
        }
    </style>
</head>
<body>
     <div>
        <p>大家好</p>
        <ul>
            <li>
                <p>你好</p>
            </li>
        </ul>
    </div>
</body>
```
### 相邻兄弟选择器
选择紧跟E元素后的F元素，用加号表示，选择相邻的第一个兄弟元素，只能是后面的第一个
```CSS
E+F{}
```
只有“小红”有颜色
```html
<head>
    <style>
         h3+p{
            color: blue;
        }
    </style>
</head>
<body>
        <p>张三</p>
        <h3>小明</h3>
        <p>小红</p>
        <p>小亮</p>
</body>
```
### 通用兄弟选择器
选择E元素**之后**的所有兄弟元素F，作用于多个元素，用~隔开，只能向下选择
```CSS
E~F{}
```
“小红、小亮”有颜色
```html
<head>
    <style>
         h3~p{
            color: red;
        }
    </style>
</head>
<body>
        <p>张三</p>
        <h3>小明</h3>
        <p>小红</p>
        <div>李四</div>
        <p>小亮</p>
</body>
```

---
## 字体属性
CSS字体属性定义字体的，颜色、大小、加粗、文字样式
### color
***规定文本的颜色***
```css
div{color:red;}
div{color:#ff0000;}        十六进制（推荐）
div{color:rgb(255,0,0);}    三原色
div{color:rgba(255,0,0,1);}    1为完全不透明
```
### font-size
***设置字体大小***  
能否管理文字大小，在网页中是非常重要的。但你不能通过调整字体大小使段落看上去像标题，或使标题看上去像段落。
```css
p{font-size:30px;}
h1{font-size:40px;}
h3{font-size:20px;}
```
> 提示：chrome浏览器接受最小字体是12px

### font-weight
***设置文本的粗细***  
| 值 | 描述 |
| :--: | :--|
|  bold  | 定义粗体字符 |
| bolder | 定义更粗的字符 |
| lighter | 定义更细的字符 |
| 100-900 | 定义由细到粗 400等同默认 700等同于bold(700常用) |
```css
p{font-weight:bold;}
h1{font-weight:700;}
h3{font-weight:lighter;}
```

### font-style
***指定文本的字体样式***
| 值 | 描述 |
| :--: | :--|
|  normal  | 默认值 |
| italic | 定义斜体字 |
```css
p{font-style:italic;}
```
### font-family
***指定元素的字体***
> 提示：  
每个值用逗号隔开  
如果字体名称包含空格，它必须加上引号
```css
p{font-family:"Microsoft YaHei";}
```

---
## 背景属性
背景设置可以更好的衬托内容
### CSS背景属性
| 属性 | 描述 |
| :--: | :--:|
| background-color | 设置背景颜色 |
| background-image | 设置背景图片 |
| background-position | 设置背景图片显示位置 |
| background-repeat | 设置背景图片如何填充 |
| background-size | 设置背景图片大小属性 |
###  background-color属性
设置背景颜色
```html 
<head>
    <style>
        .box1{
            width:400px;
            height:400px;
            background-color:red;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
</body>
```
> 设置的是容器大小：
 width:400px;
height:400px;

### background-image属性 
设置元素的背景图像  
元素的背景是元素的总大小，包括填充和边界（不包括外边距）。默认情况下background-image属性放置在元素的左上角，如果图像不够大的话会在垂直和水平方向平铺图像，如果图像大小超过元素大小从图像的左上角显示元素大小的那部分
```html
<head>
    <style>
        .box2{
            width:300px;
            height:300px;
            background-image:url("小丸子.webp");
        }
    </style>
</head>
<body>
    <div class="box2"></div>
</body>
```
### background-repeat属性
如何平铺背景图像,即水平或垂直方向是否重复
| 值 | 说明 |
| :--: | :--: |
| repeat | 默认值（水平垂直方向都平铺） |
| repeat-x | 只向水平方向平铺 |
| repeat-y | 只向垂直方向平铺 |
| no-repeat | 不平铺 |
```html
<head>
    <style>
        .box{
            width:1300px;
            height:1300px;
            background-image:url("小姐姐图.webp");
            background-repeat:repeat-x;
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
```
### background-size属性
该属性设置背景图像的大小
| 值 | 说明 |
| :--: | :--: |
| length | 设置背景图片的宽度和高度，第一个值宽度，第二个值高度，如果只是设置一个，第二个值auto |
| percentage | 计算相对位置区域的百分比，第一个值宽度，第二个值高度，如果只是设置一个，第二个值auto |
| cover | 保持图片纵横比并将图片缩放成完全覆盖背景区域的最小大小（**常用**） |
| contain | 保持图片纵横比并将图像缩放成适合背景定位区域的最大大小 |
```html
<head>
    <style>
        .box3{
            width:500px;
            height:500px;
            background-image:url("../海绵宝宝.webp");
            background-repeat:no-repeat;
            background-size:300px 400px;
        }
    </style>
</head>
<body>
    <div class="box3"></div>
</body>
```
### background-position属性
该属性设置背景图像的起始位置，其默认值是：0% 0%
| 值 | 说明 |
| :--: | :--: |
| left top | 左上角 |
| left center | 左中 |
| left bottom | 左下 |
| right top | 右上角 |
| right center | 右中 |
| right bottom | 右下 |
| center top | 中上 |
| center center | 中中 |
| center bottom | 中下 |
| x% y% | 第一个值是水平位置，第二个值是垂直位置，左上角是0% 0%，右下角是100% 100%。如果只指定了一个值，其他值默认是50%，默认是0% 0% |
| xpos ypos | 单位是像素 |
```html
<head>
    <style>
        .box4{
            width:300px;
            height:300px;
            background-image:url("小哥哥.jpeg");
            background-repeat:no-repeat;
            background-position:center center;
        }
    </style>
</head>
<body>
    <div class="box4"></div>
</body>
```

---
## 文本属性
控制文本显示效果
### text-align
指定元素文本的水平对齐方式
| 值 | 描述 |
| :--| :--|
| left | 文本居左排列，默认值 |
| right | 把文本排列到右边 |
| center | 把文本排列到中间 |
```html
<head>
    <style>
        h3{
            text-align: right;
        }
    </style>
</head>
<body>
    <h3>我是标题</h3>
</body>
```
### text-decoration
text-decoration 属性规定添加到文本的修饰，下划线、上划线、删除线等
| 值 | 描述 |
| :--| :--|
| underline | 定义下划线 |
| overline | 定义上划线 |
| line-through | 定义删除线 |
```html
<head>
    <style>
        h1{
            text-decoration:underline;
        }
    </style>
</head>
<body>
    <h1>明天会更好</h1>
</body>
```
### text-transform
text-transform 属性控制文本的大小写
| 值 | 描述 |
| :--| :--|
| capitalize | 定义每个单词开头大写 |
| uppercase | 定义全部大写字母 |
| lowercase | 定义全部小写字母 |
```html
<head>
    <style>
        p{
            font-size:50px;
            text-align:center;
            text-transform:capitalize;
        }
    </style>
</head>
<body>
    <p>helloword</p>
</body>
```
### text-indent
text-indent 属性规定文本块中首行文本的缩进
```html
<head>
    <style>
        p{
            text-indent:30px;
        }
    </style>
</head>
<body>
    <p>轻轻的我走了，正如我轻轻的来；我轻轻的招手，作别西天的云彩。那河畔的金柳，是夕阳中的新娘；波光里的艳影，在我的心头荡漾。</p>
</body>
```
> 提示  
负值是允许的，如果值是负数，将第一行左缩进

---
## 表格属性
HTML表格标签的表格不太好看，所以使用CSS的表格属性，可以使HTML表格更美观
### 表格边框
指定CSS表格边框，使用border属性
```html
<head>
    <style>
        table,td{
            border: 1px solid red;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
    </table>
</body>
```
> solid表示实线
### 折叠边框
border-collapse属性，双边框折叠成单边框
### 表格宽度和高度
width和height属性定义表格的宽度和高度
```html
<head>
    <style>
        table,td{
            border: 1px solid red;
        }
        table{
            border-collapse:collapse;
            width: 500px;
            height: 300px;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
    </table>
</body>
```
### 表格文字对齐
表格中的文本对齐和垂直对齐属性  
text-align属性设置水平对齐方式，向左，右，或中心
```css
td{ text-align: right; }
```
垂直对齐属性
```css
 td{vertical-align: top;}
```
```html
<head>
    <style>
        table,td{
            border: 1px solid red;
        }
        table{
            border-collapse:collapse;
            width: 500px;
            height: 300px;
        }
         td{
            text-align: center;
            vertical-align: bottom;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
    </table>
</body>
```
### 表格填充
字与四周边框的距离
```css        
td{ padding: 20px; }
```
```html
<head>
    <style>
        table,td{
            border: 1px solid red;
        }
        table{
            border-collapse:collapse;
        }
         td{
            padding: 20px;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
        <tr>
            <td>单元格</td>
            <td>单元格</td>
            <td>单元格</td>
        </tr>
    </table>
</body>
```
### 表格颜色
指定边框的颜色、背景、文本颜色
```css
table,td,th{ border: 1px solid red;}
```
```css
td{ background-color: grey;
    color: blue;
}
```
```html
<head>
    <style>
        table,td{
            border: 1px solid red;
        }
        table{
            border-collapse:collapse;
        }
        td{
            background-color: grey;
            color: blue;
        }
    </style>
</head>
```

---
## CSS布局 盒子模型（Box Model）
在设计和布局时使用
### 概念
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

---
## CSS布局 弹性盒子模型（flex box）
- 弹性盒子是CSS3的一种新的布局模式；   
- CSS3弹性盒是一种当页面需要适应不同的屏幕大小以及设备类型时确保元素拥有恰当的行为的布局方式；  
- 引入弹性盒子布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间；
### CSS3弹性盒内容
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

### 父元素上的属性
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

### 子元素上的属性
`flex`属性:  （平均分配）
- 根据弹性盒子元素所设置的扩展因子作为比率来分配剩余空间  
- 默认为0，即如果存在剩余空间，也不放大

如果只有一个子元素设置，那么按扩展因子转化的百分比对其分配剩余空间。0.1即10%，1即100%
> 举例   
容器大盒子总份数权重是500。第一个子元素盒子占200，第二个占200，第三个占100。也就是分别占了2，2，1

---
## 文档流
页面元素在摆放时所占用的位置/空间
### 概念 
文档流是文档中可显示对象在排列时所占用的位置/空间   
例如:块元素自上而下摆放，内联元素从左到右摆放  
标准流里面的限制非常多，导致很多页面效果无法实现

导致出的问题：  
- 高矮不齐，底边对齐   
- 空白折叠现象
    - 无论多少个空格、换行、tab，都会折叠为一个空格
    - 如果我们想让img标签之间没有间隙，必须紧密连接
### 文档流产生的以下问题
1. 高矮不齐，底边对齐
2. 空格折叠现象：不管你加多少空格，页面就只显示一个空格
3. 元素无间隙：放两张图片，这两张图之间会有一点点空隙

```html
<head>
    <style>
        img{
            width: 500px;
            height: 300px;
        }
    </style>
</head>
<body>
    <span>我们一起看美女</span>
    <img src="美女.webp" alt="">
    <p>这是一名    网红</p>
    <img src="小丸子.webp" alt="">
    <img src="小丸子.webp" alt="">
</body>
```
如果不想出现默认的以上现象，该怎么办呢？办法：移民，脱离标准文档流

### 脱离文档流
使一个元素脱离标准文档流有三种方式  
1. 浮动
2. 绝对定位
3. 固定定位
> 后面学习，脱离文档流

---
## 浮动
增加一个浮层来放置内容，从而脱离文档流
### 定义
`float`属性定义元素在哪个方向浮动，任何元素都可以浮动
| 值 | 描述 |
| :- |:- |
| left |元素向左浮动 |
| right | 元素向右浮动 |
- 浮动以后使元素脱离文档流
- 浮动只有左右浮动，没有上下浮动
### 元素向左/向右浮动
脱离文档流之后，元素相当于在页面上增加一个浮层来放置内容。可以理解为有两层页面，一层是底层的原页面，一层是脱离文档流的上层页面，所以会出现折叠现象
![41b529ac679efbf347682ea63f22391](https://cdn.staticaly.com/gh/MollyXu1995/molly-picx@master/20220807/41b529ac679efbf347682ea63f22391.bq16uqq4fq8.webp)

```html
<head>
    <style>
        .box{
            width: 200px;
            height: 200px;
            background-color: aqua;
            float: left;
        }
        .container{
            width: 400px;
            height: 400px;
            background-color: blueviolet;
        }
        img{
            width: 300px;
            float: left;
        }
    </style>
</head>
<body>
    <div class="box"></div>
    <div class="container"></div>
    <div>
        <img src="../路飞.webp" alt="">
        <img src="../路飞.webp" alt="">
    </div>
</body>
```
### 所有元素向左/向右浮动
当所有元素同时浮动的时候，会变成水平摆放，向左或者向右
```html
<head>
    <style>
        div{
            width: 200px;
            height: 200px;
            float: left;
        }
        .box1{
            background-color: red;
        }
        .box2{
            background-color: blue;
        }
        .box3{
            background-color: green;
        }
        ul li{
            float: left;
            margin: 0 30px;
        }

    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
    <ul>
        <li>导航1</li>
        <li>导航2</li>
        <li>导航3</li>
        <li>导航4</li>
        <li><a href="#">导航5</a></li>
    </ul>
</body>
```
### 当容器不足时
当容器不足以横向摆放内容时候，会在下一行摆放
```html
<head>
    <style>
        .container{
            width: 500px;
            height: 500px;
            background-color: gray;
        }
        div{
            width: 200px;
            height: 200px;
            float: left;
        }
        .box1{
            background-color: red;
        }
        .box2{
            background-color: blue;
        }
        .box3{
            background-color: green;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box1"></div>
        <div class="box2"></div>
        <div class="box3"></div>
    </div>
</body>
```

---
## 清除浮动
### 浮动副作用:
当元素设置float浮动后，该元素就会脱离文档流并向左/向右浮动
- 浮动元素会造成父元素高度塌陷
- 后续元素会受到影响

所以浮动不要轻易设，不然还要清除浮动，比较麻烦

### 清除浮动
当父元素出现塌陷的时候，对布局是不利的，所以我们必须清除副作用。  
解决方案有很多种：  
- 父元素设置高度
- 受影响的元素增加`clear`属性
- overflow清除浮动
- 伪对象方式

1. **父元素设置高度**  
如果父元素高度塌陷，可以给父元素设置高度，撑开元素本身大小


2. 增加`clear`属性  
给受影响的元素增加：`clear:both;`

>子元素在里面受影响：增加`clear`属性   
子元素在外面受影响：其他方式都可以消除浮动 

```html
<head>
    <style>
        .container{
            width: 500px;
            height: 500px;
            background-color: #888;
        }
        .box{
            width: 100px;
            height: 100px;
            background-color:aqua;
            margin: 5px;
            float: left;
        }
        .text{
            width: 100px;
            height: 100px;
            background-color:purple;
            clear: both;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box"></div>
        <div class="box"></div>
        <div class="box"></div>
        <div class="text"></div>
    </div>
</body>
```
3. overflow清除浮动 （较常用）
如果父元素塌陷，并且同级元素也受到了影响，可以使用`overflow`清除浮动，这种情况下，**父布局不能设置高度**  
父级标签的样式里面加：`overflow:hidden;` `clear: both;`
```html
<head>
    <style>
        .container{
            width: 500px;
            background-color: #888;
            overflow: hidden;
            clear: both;
        }
        .box{
            width: 100px;
            height: 100px;
            background-color:aqua;
            margin: 5px;
            float: left;
        }
        .text{
            width: 100px;
            height: 100px;
            background-color:purple;
            clear: both;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box"></div>
        <div class="box"></div>
        <div class="box"></div>
        <div class="text"></div>
    </div>
</body>
```

4. 伪对象方式  
如果有父级塌陷，并且同级元素也受到了影响，还可以使用伪对象方式处理  
为父标签添加伪类`after`，设置空的内容` content: "";`，并且使用`display: block;` `clear:both;`  
这种情况下，**父布局不能设置高度**  
```css
.container::after{
            content: "";
            display: block;
            clear: both;
}
```

```html
<head>
    <style>
        .container{
            width: 500px;
            background-color: #888;
        }
        .container::after{
            content: "";
            display: block;
            clear: both;
        }
        .box{
            width: 100px;
            height: 100px;
            background-color:aqua;
            margin: 5px;
            float: left;
        }
        .text{
            width: 100px;
            height: 100px;
            background-color:purple;
            clear: both;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box"></div>
        <div class="box"></div>
        <div class="box"></div>
        <div class="text"></div>
    </div>
</body>
```

---
## 定位
### 概念
`position`属性指定了元素的定位类型
| 值 | 描述 |
|:- | :- |
| relative | 相对定位 |
| absolute | 绝对定位 |
| fixed | 固定定位 |

其中，绝对定位、固定定位会脱离文档流  
设置定位之后，可以使用四个方向值进行调整位置：`left、top、right、bottom`  

### 相对定位
```html
<head>
    <style>
        div{
            width: 200px;
            height: 200px;
            background-color: red;
            position: relative;
            left: 200px;
            top: 100px;
        }
    </style>
</head>
<body>
    <div></div>
</body>
```

### 绝对定位
每一个绝对定位就是一层，元素之间相互压盖  
会随着页面滚动
```html
<head>   
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: red;
            position: absolute;
            left:100px;
            top: 200px;
        }
        .box2{
            width: 300px;
            height: 300px;
            background-color:blue;  
        }
        .box3{
            width: 200px;
            height: 200px;
            background-color:purple;  
            position: absolute;
            left:50px;
            top: 100px;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
</body>
```

### 固定定位
固定在页面上，不随页面滚动
```html
<head>
    <style>
        .box1{
            width: 100px;
            height: 100px;
            background-color: green;
            position: fixed;
            right: 100px;
            bottom: 100px;
        }
        .box2{
            width: 400px;
            height: 400px;
            background-color: red;
        }
        .box3{
            width: 200px;
            height: 200px;
            background-color: blue;
            position: absolute;
            left: 0px;
            top: 0px;
        }
        h3{
            height: 500px;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
    
    <h3>哈哈哈</h3>
    <h3>哈哈哈</h3>
    <h3>哈哈哈</h3>
    <h3>哈哈哈</h3>
</body>
```

> 提示：   
设置定位之后，相对定位和绝对定位他是相对于具有定位的父级元素进行位置调整，如果父级元素不存在定位，则继续向上逐级寻找，直到顶层文档  

以父级元素的位置进行调整，则该元素添加绝对定位，父级添加相对定位；      
不以父级元素的位置进行调整，则该元素添加绝对定位，父级不添加相对定位；  

```html
<head>
    <style>
        .container{
            width: 200px;
            height: 200px;
            background-color: gray;
            position: relative;
            margin-left: 100px;
        }
        .box{
            width: 100px;
            height: 100px;
            background-color: blueviolet;
            position: absolute;
            left: 50px;
            top: 50px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box"></div>
    </div>
</body>
```

### Z-index属性
`z-index`设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面  
谁覆盖谁，谁的Z-index值大，就能覆盖Z-index值小的

```html
<head>
    <style>
        .box1{
            width: 200px;
            height: 200px;
            background-color: red;
            position: absolute;
            left:100px;
            top: 200px;
            z-index: 100;
        }
        .box3{
            width: 200px;
            height: 200px;
            background-color:purple;  
            position: absolute;
            left:50px;
            top: 100px;
            z-index: 50;
        }
    </style>
</head>
<body>
    <div class="box1"></div>
    <div class="box3"></div>
</body>
```

---
## CSS3新特性
### 圆角
使用CSS3`border-radius`属性，你可以给任何元素制作“圆角”  
`border-radius`属性，可以使用以下规则：
1. 四个值：第一个值为左上角，第二个值为右上角，第三个值为右下角，第四个值为左下角 
2. 三个值：第一个值为左上角，第二个值为右上角和左下角，第三个值为右下角
3. 两个值：第一个值为左上角与右下角，第二个值为右上角与左下角
4. 一个值：四个圆角值相同

```html
<head>
    <style>
        div{
            width: 56px;
            height: 56px;
            background-color: blueviolet;
            border-radius: 20px;
        }
    </style>
</head>
<body>
    <div></div>
</body>
```
>`border-radius:20px;`圆角  
`border-radius:100%;`圆 (50%也是圆，与100%效果一样) 


### 阴影
`box-shadow`向框添加一个或多个阴影

> 四个方向的数值：水平阴影、垂直阴影、模糊距离、阴影颜色   
`box-shadow: h-shadow v-shadow blur color; `  
box-shadow: 10px 10px 20px red;     下、右加阴影   
box-shadow: -10px -10px 20px red;   上、左加阴影


| 值 | 描述 |
|:- | :- |
| h-shadow | 必选，水平阴影的位置 |
| v-shadow | 必选垂直阴影的位置 |
| blur | 可选，模糊距离 |
| color | 可选，阴影的颜色 |


```html
<head>
    <style>
        .box{
            width: 400px;
            height: 400px;
            background-color: blueviolet;
            margin: 0 auto;    /*上下为0  左右边距平均分配*/
            box-shadow: 10px 10px 20px rgba(0, 0, 0, 0.5);
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
```

三个方向的阴影效果
```html
<head>
    <style>
        .box{
            width: 400px;
            height: 400px;
            background-color: blueviolet;
            margin: 0 auto;    /*上下为0  左右边距平均分配*/
            box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.5);
        }
    </style>
</head>
<body>
    <div class="box"></div>
</body>
```

---
## 动画
- 动画是使元素从一种样式逐渐变化为另一种样式的效果  
- 您可以改变任意多的样式任意多的次数  
- 请用百分比来规定变化发生的时间，或用关键词"from"和"to"，等同于0%和100%    
- 0%是动画的开始，100%是动画的完成

### @keyframes创建动画
使用`@keyframes`规则，你可以创建动画

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>

        @keyframes myAnim{
            0%{
                background-color: red;
            }
            50%{
                background-color: green;
            }
            100%{
                background-color: red;
            }

        }

    </style>
</head>
<body>
    
</body>
```

name:动画名称，开发人员自己命名；  
percent:为百分比值，可以添加多个百分比值；


### animation执行动画

切换背景颜色
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div{
            width: 200px;
            height: 200px;
            background-color: red;
            animation: myAnim 3s linear 0s infinite ;
        }

        /*鼠标放上面，就暂停动画*/
        div:hover{
            animation-play-state: paused;
        }     

        @keyframes myAnim{
            0%{
                background-color: red;
            }
            50%{
                background-color: green;
            }
            100%{
                background-color: red;
            }

        }

    </style>
</head>
<body>

    <div></div>

</body>
```

| 值 | 描述 |
|:- | :- |
| name | 设置动画的名称 |
| duration | 设置动画的持续时间，单位s |
| timing-function | 设置动画效果的速率（如下） |
| delay | 设置动画的开始时间（延时执行），单位s |
| iteration-count | 设置动画循环的次数，infinite为无限次数的循环，不写就默认循环1次 |
| direction | 设置动画播放的方向（如下） |
| animation-play-state | 控制动画的播放状态：running代表播放，而paused代表停止播放 |



| timing-function | 描述 |
| :- | :- |
| ease | 逐渐变慢（默认） |
| linear | 匀速 |
| ease-in | 加速 |
| ease-out | 减速 |
| ease-in-out | 先加速后减速 |



| direction值 | 描述 |
| :- | :- |
| normal | 默认值为normal表示向前播放 |
| alternate | 动画播放在第偶数次向前播放，第奇数次向反方向播放 |


呼吸效果
```html
<head>

    <style>
        .box{
            width: 500px;
            height: 500px;
            margin: 40px auto;
            background-color: #2b92d4;
            border-radius: 50%;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
            animation: breathe 1s ease-in-out infinite alternate;
        }

        @keyframes breathe{
            0%{
                opacity: .2;  /*透明度为0.2*/
                box-shadow:0 1px 2px rgba(255, 255, 255, 0.1);
            }

            50%{
                opacity: .5;
                box-shadow:0 1px 2px rgba(18, 190, 84, 0.76);
            }
            100%{
                opacity: 1;
                box-shadow:0 1px 30px rgba(59, 255, 255, 1);
            }

        }

    </style>

</head>
<body>
    <div class="box"></div>
</body>
```

---
## 媒体查询
媒体查询能使页面在不同的终端设备下达到不同的效果  
媒体查询**会根据设备的大小自动识别加载不同的样式**
### 设置meta标签
使用设备的宽度作为视图宽度并禁止初始的缩放。在`<head>`标签里加入这个`meta`标签

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
> `！`基础框架里就有这条语句

参数解释
1. `width=device-width`宽度等于当前设备的宽度
2. `initial-scale`初始的缩放比例（默认设置为1.0）
3. `maximum-scale`允许用户缩放到的最大比例（默认设置为1.0）
4. `user-scalable`用户是否可以动手缩放（默认设置为no）

### 媒体查询语法

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
        }
                         /*设备大于768px但小于992px加载样式，平板*/
        @media screen and (min-width:768px) and (max-width:992px) {
            .box{
                background-color: green;
            }
        }

                         /*设备大于768px但小于992px加载样式，电脑*/
        @media screen and (min-width:992px) {
            .box{
                background-color: red;
            }
        }

    </style>
</head>
<body>
    <div class="box"></div>
</body>
```


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

---
## 雪碧图
CSS Sprite也叫CSS精灵图、CSS雪碧图，是一种网页图片应用处理方式。它允许你将一个页面涉及到的所有零星图片都包含到一张大图中去

### 优点
- 减少图片的字节
- 减少网页的http请求，从而大大的提高页面的性能

### 原理
1. 通过`background-image`引入背景图片 
2. 通过`background-position`把背景图片移动到自己需要的位置

在网页检查中调整位置，再将位置复制到代码文档中
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .icon1{
            display: block;    /*把行内元素span变成块级元素,才可设置大小*/
            width: 700px;
            height: 700px;
            background-image: url(表情.png);
            border: 1px solid red;
            background-position: -170px 0px ;
        }
        .icon2{
            display: block;    
            width: 700px;
            height: 700px;
            background-image: url(表情.png);
            border: 1px solid red;
            background-position: -1133px -661px;
        }

    </style>
</head>
<body>

    <span class="icon1"></span>
    <span class="icon2"></span>

</body>
```

---
## 字体图标
我们会经常用到一些图标。但是我们在使用这些图标时，往往会遇到失真的情况，而且图片数量很多的话，页面加载就越慢。所以，我们可以使用字体图标的方式来显示图标，即解决了是真的问题，也解决了图片占用资源的问题  

常用字体图标库：[阿里字体图标库](https://www.iconfont.cn/)

### 优点
- 轻量性：加载速度快，减少http请求
- 灵活性：可以利用CSS设置大小颜色等
- 兼容性：网页字体支持所有现代浏览器，包括IE低版本

### 使用字体图标
1. 注册账号并登录
2. 选取图标或搜索图标
3. 添加购物车
4. 下载代码
5. 解压，将文件复制到自己文档的文件夹目录下，打开demo_index.html
6. 选择`font-class`引用
7. 根据步骤编写

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <link rel="stylesheet" href="./font/iconfont.css">

    <style>
        .install{
            font-size: 100px;
            color: #e1251b;
        }

    </style>

</head>
<body>

    <span class="iconfont icon-shezhi install"></span>

</body>
```

---
## 参考资料

{{< card "https://developer.mozilla.org/en-US/" >}}

{{< card "https://www.w3school.com.cn/index.html" >}}

{{< card "https://humble-blog.vercel.app/css" >}}

























