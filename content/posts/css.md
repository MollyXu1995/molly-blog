---
title: "CSS的使用"
date: 2022-08-04T16:20:44+08:00
tags: ['Language']
series: ['前端学习之旅']
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
## CSS的引入方式
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
```

```
### background-image属性 
设置元素的背景图像  
元素的背景是元素的总大小，包括填充和边界（不包括外边距）。默认情况下background-image属性放置在元素的左上角，如果图像不够大的话会在垂直和水平方向平铺图像，如果图像大小超过元素大小从图像的左上角显示元素大小的那部分
```

```
### background-repeat属性
如何平铺背景图像
| 值 | 说明 |
| :--: | :--: |
| repeat | 默认值 |
| repeat-x | 只向水平方向平铺 |
| repeat-y | 只向垂直方向平铺 |
| no-repeat | 不平铺 |
```

```
### background-size属性
该属性设置背景图像的大小
| 值 | 说明 |
| :--: | :--: |
| length | 设置背景图片的宽度和高度，第一个值宽度，第二个值高度，如果只是设置一个，第二个值auto |
| percentage | 计算相对位置区域的百分比，第一个值宽度，第二个值高度，如果只是设置一个，第二个值auto |
| cover | 保持图片纵横比并将图片缩放成完全覆盖背景区域的最小大小 |
| contain | 保持图片纵横比并将图像缩放成适合背景定位区域的最大大小 |
```

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
```

```

